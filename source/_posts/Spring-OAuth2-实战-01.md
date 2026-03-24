---
title: Spring-OAuth2-实战-01
subtitle: OAuth2
catalog: true
tags: [OAuth2, Security, Spring]
date: 2025-09-10 14:48:12
header-img:
---

# Spring-OAuth2-实战-01



## 简介

Spring Security 提供全面的 OAuth 2.0 支持。本节讨论如何将 OAuth 2.0 集成到基于 Servlet 的应用程序中。

Spring Security 的 OAuth 2.0 支持由两个主要功能集组成：

- [OAuth2 Resource Server | OAuth2 资源服务器](https://docs.spring.io/spring-security/reference/servlet/oauth2/index.html#oauth2-resource-server)
- [OAuth2 Client | OAuth2 客户端](https://docs.spring.io/spring-security/reference/servlet/oauth2/index.html#oauth2-client)

这些功能集涵盖了 [OAuth 2.0 授权框架](https://tools.ietf.org/html/rfc6749#section-1.1)中定义的*资源服务器*和*客户端*角色，而*授权服务器*角色则由 [Spring Authorization Server 覆盖，Spring Authorization Server](https://docs.spring.io/spring-authorization-server/reference/index.html) 是一个基于 [Spring Security](https://docs.spring.io/spring-security/reference/index.html) 构建的单独项目。

## 准备工作

若要开始，请将依赖项添加到项目中。使用 Spring Boot 时，添加以下启动器： `spring-security-oauth2-resource-server`

~~~
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-oauth2-resource-server</artifactId>
</dependency>

~~~

以下示例使用 Spring Boot 配置属性配置 bean：`JwtDecoder`

```yaml
spring:
  security:
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: https://my-auth-server.com
```

使用 Spring Boot 时，只需这样做即可。Spring Boot 提供的默认排列方式相当于以下内容：

~~~java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

	@Bean
	public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
		http
			.authorizeHttpRequests((authorize) -> authorize
				.anyRequest().authenticated()
			)
			.oauth2ResourceServer((oauth2) -> oauth2
				.jwt(Customizer.withDefaults())
			);
		return http.build();
	}

	@Bean
	public JwtDecoder jwtDecoder() {
		return JwtDecoders.fromIssuerLocation("https://my-auth-server.com");
	}

}
~~~





####  Opaque Token Support 不透明令牌支持

以下示例使用 Spring Boot 配置属性配置 bean：`OpaqueTokenIntrospector`

```
spring:
  security:
    oauth2:
      resourceserver:
        opaquetoken:
          introspection-uri: https://my-auth-server.com/oauth2/introspect
          client-id: my-client-id
          client-secret: my-client-secret
```
使用 Spring Boot 时，只需这样做即可。Spring Boot 提供的默认排列方式相当于以下内容：


~~~java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

	@Bean
	public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
		http
			.authorizeHttpRequests((authorize) -> authorize
				.anyRequest().authenticated()
			)
			.oauth2ResourceServer((oauth2) -> oauth2
				.opaqueToken(Customizer.withDefaults())
			);
		return http.build();
	}

	@Bean
	public OpaqueTokenIntrospector opaqueTokenIntrospector() {
		return new SpringOpaqueTokenIntrospector(
			"https://my-auth-server.com/oauth2/introspect", "my-client-id", "my-client-secret");
	}

}
~~~

### 核心比喻：身份证 vs 酒店房卡

- **透明令牌 (Transparent Token)** 就像你的**身份证**。**自包含信息**：身份证上直接印着你的姓名、年龄、住址、身份证号等所有关键信息。**可离线验证**：任何一个懂规则的“验证方”（比如警察、银行职员）拿到你的身份证，不需要联网去公安局数据库查询，只通过查看防伪标识（比如水印、芯片），就能当场确认这张证件的真伪和你的身份。**最典型的例子**：**JWT (JSON Web Token)**。
- **不透明令牌 (Opaque Token)** 就像一张**酒店房卡**。**无意义的引用**：房卡本身就是一串加密的、无意义的磁条数据。你看着它，完全不知道它对应哪个房间、有效期到什么时候。它只是一个**引用**或**指针**。**必须在线验证**：你必须拿着这张房卡去刷门锁。门锁会通过内部网络，实时地向酒店的**中央管理系统**发起一个查询：“这张卡号为XYZ的房卡，现在有效吗？能开这间房吗？”。只有中央系统返回“确认”后，门才会打开。**最典型的例子**：一串随机生成的、长长的字符串。



| 特性            | 透明令牌 (JWT)                              | 不透明令牌                                                   |
| --------------- | ------------------------------------------- | ------------------------------------------------------------ |
| **结构**        | 自包含的数据结构 (Header.Payload.Signature) | 无意义的随机字符串 (引用/指针)                               |
| **验证方式**    | **本地验证** (离线，使用公钥验证签名)       | **远程验证** (在线，调用内省端点)                            |
| **性能/伸缩性** | **高**，无额外网络调用，易于扩展            | **低**，每次请求都有额外的网络调用                           |
| **撤销**        | **困难** (只能等待过期或使用黑名单)         | **简单** (在认证服务器删除记录即可)                          |
| **信息安全**    | 载荷可被解码读取，**不能存敏感信息**        | 令牌本身不泄露任何信息，**安全性高**                         |
| **耦合度**      | **松耦合**                                  | **紧耦合**                                                   |
| **典型场景**    | **微服务API**，高性能要求的无状态服务       | **金融级应用**，需要立即撤销权限的后台，面向第三方或公开客户端（不希望暴露任何信息） |



## 引用资料

>[OAuth2 :: Spring Security](https://docs.spring.io/spring-security/reference/servlet/oauth2/index.html)
>
>
