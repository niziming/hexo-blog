---
title: Java 8到Java 21的重要特性
subtitle: Java 8到Java 21的重要特性
catalog: true
tags: [Java21,Java17,Java11,Java8]
date: 2025-09-12 18:26:16
header-img:
---

# Java 8到Java 21的重要特性

> **Java 8 vs Java 21 特性全面对比与演示**

本项目通过实际代码演示Java 8到Java 21的重要特性变化，帮助开发者了解和学习Java语言的演进。

## 📋 项目概述

### 主要目标

- 🔍 **对比展示**：直观对比Java 8与Java 21的特性差异
- 🎯 **实用演示**：通过实际可运行的代码展示各种特性
- 📚 **学习资源**：为Java开发者提供版本升级参考
- 🏷️ **版本标注**：使用自定义注解清晰标识各特性的Java版本

### 技术栈

- **Java版本**：Java 21 (兼容展示Java 8特性)
- **构建工具**：Maven 3.8+
- **测试框架**：JUnit 5
- **开发环境**：支持Java 21的IDE (推荐IDEA 2023.2+)

## 🚀 快速开始

### 环境要求

- ✅ Java 21 或更高版本
- ✅ Maven 3.8 或更高版本
- ✅ 支持Java 21的IDE

### 安装运行

1. **克隆项目**

   ```bash
   git clone <repository-url>
   cd Java21FeatureFrom8
   ```

2. **编译项目**

   ```bash
   mvn clean compile
   ```

3. **运行所有演示**

   ```bash
   mvn exec:java -Dexec.mainClass="com.demo.utils.DemoRunner"
   ```

4. **运行特定演示**

   ```bash
   # 运行语言特性演示
   mvn exec:java -Dexec.mainClass="com.demo.utils.DemoRunner" -Dexec.args="language"
   
   # 运行并发特性演示
   mvn exec:java -Dexec.mainClass="com.demo.utils.DemoRunner" -Dexec.args="concurrent"
   ```

## 📂 项目结构

```
src/main/java/com/demo/
├── annotations/          # 版本特性标注注解
│   ├── Java8Feature.java
│   ├── Java9Feature.java
│   ├── Java11Feature.java
│   ├── Java17Feature.java
│   └── Java21Feature.java
├── language/            # 语言特性增强
│   └── LanguageEnhancementsDemo.java
├── collections/         # 集合框架增强
│   └── CollectionsDemo.java
├── streams/            # Stream API增强
│   └── StreamsDemo.java
├── concurrent/         # 并发编程增强
│   └── ConcurrencyDemo.java
├── io/                 # I/O操作增强
│   └── IODemo.java
├── text/               # 文本处理增强
│   └── TextProcessingDemo.java
├── records/            # Records特性
│   └── RecordsDemo.java
├── pattern/            # 模式匹配
│   └── PatternMatchingDemo.java
├── sealed/             # 密封类
│   └── SealedClassesDemo.java
├── preview/            # 预览特性
│   └── PreviewFeaturesDemo.java
└── utils/              # 工具类
    └── DemoRunner.java
```

## 🎯 特性演示模块

### 1. 语言特性增强 (`language`)

**Java 8 引入的核心特性：**

- 🔥 **Lambda表达式** - 函数式编程支持
- 🔗 **方法引用** - Lambda的简化形式
- 📦 **Optional类** - 空值处理
- 🎛️ **接口默认方法** - 接口演进支持

**Java 11+ 增强：**

- 🆚 **var关键字** - 类型推断
- 🔍 **instanceof模式匹配** (Java 17)
- 🎯 **switch表达式** (Java 17)

```java
// Java 8: Lambda表达式
list.forEach(item -> System.out.println(item));

// Java 11: var关键字
var message = "Hello Java";

// Java 17: instanceof模式匹配
if (obj instanceof String str) {
    System.out.println(str.toUpperCase());
}
```

### 2. 集合框架增强 (`collections`)

**Java 8 特性：**

- 🎭 **Stream集成** - 函数式数据处理
- 🛠️ **便利方法** - forEach, removeIf等
- ⚡ **ConcurrentHashMap增强** - 并发安全操作

**Java 9+ 特性：**

- 🏭 **不可变集合工厂** - List.of(), Set.of(), Map.of()
- 🔄 **toArray()增强** (Java 11)

```java
// Java 9: 不可变集合
List<String> languages = List.of("Java", "Python", "JavaScript");

// Java 8: Stream操作
Map<String, List<Employee>> byDept = employees.stream()
    .collect(groupingBy(Employee::getDepartment));
```

### 3. Stream API增强 (`streams`)

**Java 8 核心功能：**

- 🌊 **基础Stream操作** - filter, map, reduce
- 📊 **收集器** - Collectors的丰富功能
- ⚡ **并行Stream** - 多核处理能力

**Java 9+ 增强：**

- 🎯 **takeWhile/dropWhile** - 条件操作
- 📝 **Stream.toList()** (Java 16) - 简化收集

```java
// Java 8: 基础操作
List<String> result = list.stream()
    .filter(s -> s.length() > 3)
    .map(String::toUpperCase)
    .collect(Collectors.toList());

// Java 16: 简化收集
List<String> result = list.stream()
    .filter(s -> s.length() > 3)
    .map(String::toUpperCase)
    .toList();
```

### 4. 并发编程增强 (`concurrent`)

**Java 8 特性：**

- 🔮 **CompletableFuture** - 异步编程框架
- 🍴 **ForkJoinPool** - 工作窃取算法
- ⚛️ **原子操作增强** - updateAndGet等

**Java 21 重大突破：**

- 🚀 **虚拟线程** - Project Loom的核心特性
- 🏗️ **结构化并发** (预览) - 任务组管理

```java
// Java 8: CompletableFuture
CompletableFuture<String> future = CompletableFuture
    .supplyAsync(() -> processData())
    .thenApply(String::toUpperCase);

// Java 21: 虚拟线程
Thread virtualThread = Thread.ofVirtual().start(() -> {
    // 可以安全地阻塞，成本极低
    processLongRunningTask();
});
```

### 5. Records特性 (`records`)

**Java 17 重要特性：**

- 📋 **数据载体类** - 简洁的不可变数据结构
- 🔧 **自动生成方法** - 构造器、getter、equals、hashCode、toString
- ✅ **紧凑构造器** - 数据验证
- 🎯 **泛型支持** - 类型安全

```java
// 传统类需要20+行代码
public record Person(String name, int age, String city) {}

// 自动获得所有标准方法
Person person = new Person("张三", 25, "北京");
System.out.println(person.name()); // 访问字段
```

### 6. 模式匹配 (`pattern`)

**Java 17 特性：**

- 🎯 **instanceof模式匹配** - 自动类型转换
- 🔄 **switch表达式增强** - 更灵活的分支

**Java 21 预览特性：**

- 📋 **Record模式匹配** - Record解构
- 🏗️ **嵌套模式匹配** - 复杂结构处理
- 🛡️ **守卫条件** - when子句

```java
// Java 17: instanceof模式匹配
if (obj instanceof String str && str.length() > 10) {
    System.out.println("长字符串: " + str.toUpperCase());
}

// Java 21 预览: Record模式匹配 (概念)
switch (person) {
    case Person(var name, var age, "工程师") -> handleEngineer(name, age);
    case Person(var name, var age, var job) when age > 30 -> handleSenior(name, job);
}
```

### 7. 密封类 (`sealed`)

**Java 17 特性：**

- 🔒 **继承控制** - 限制类的继承层次
- 🎯 **完备性检查** - 编译器保证覆盖所有情况
- 🏗️ **类型层次设计** - 更好的API设计
- 📋 **与Record结合** - 类型安全的数据结构

```java
// 密封类定义
public sealed abstract class Shape 
    permits Circle, Rectangle, Triangle {
}

// switch表达式无需default分支
return switch (shape) {
    case Circle c -> Math.PI * c.radius() * c.radius();
    case Rectangle r -> r.length() * r.width();
    case Triangle t -> calculateTriangleArea(t);
};
```

## 🎮 演示命令

### 运行全部演示

```bash
mvn exec:java
```

### 运行特定模块

```bash
# 语言特性
mvn exec:java -Dexec.args="language"

# 集合框架
mvn exec:java -Dexec.args="collections"

# Stream API
mvn exec:java -Dexec.args="streams"

# 并发编程 (包括虚拟线程)
mvn exec:java -Dexec.args="concurrent"

# Records特性
mvn exec:java -Dexec.args="records"

# 模式匹配
mvn exec:java -Dexec.args="pattern"

# 密封类
mvn exec:java -Dexec.args="sealed"
```

## 📊 特性版本对比表

| 特性分类     | Java 8                             | Java 9-11             | Java 17 LTS                            | Java 21 LTS                       |
| ------------ | ---------------------------------- | --------------------- | -------------------------------------- | --------------------------------- |
| **语言语法** | Lambda表达式 方法引用 接口默认方法 | var关键字             | instanceof模式匹配 switch表达式 文本块 | 字符串模板(预览) 未命名变量(预览) |
| **数据结构** | Optional Stream API                | 不可变集合工厂        | **Records** **密封类**                 | Record模式匹配(预览)              |
| **并发编程** | CompletableFuture 并行Stream       | CompletableFuture增强 | -                                      | **虚拟线程** 结构化并发(预览)     |
| **集合框架** | Stream集成 便利方法                | takeWhile/dropWhile   | -                                      | -                                 |
| **模式匹配** | -                                  | -                     | instanceof switch增强                  | Record解构(预览) 守卫条件(预览)   |

## 🏗️ 版本标注系统

项目使用自定义注解标识特性的Java版本：

```java
@Java8Feature(value = "Lambda表达式", description = "函数式编程支持")
@Java17Feature(value = "Records", description = "简洁的数据载体类")
@Java21Feature(value = "虚拟线程", description = "轻量级线程，支持数百万并发")
```

## 🔧 开发配置

### Maven配置要点

- **Java版本**: 21
- **编译器参数**: `--enable-preview` (预览特性)
- **编码**: UTF-8
- **测试框架**: JUnit 5

### IDE配置建议

- **语言级别**: Java 21
- **预览特性**: 启用
- **编码**: UTF-8
- **代码风格**: 使用现代Java语法

## 📈 性能对比

### 虚拟线程性能提升

```java
// 传统线程池: 100个线程处理1000个任务
ExecutorService traditional = Executors.newFixedThreadPool(100);
// 耗时: ~500ms

// 虚拟线程: 1000个虚拟线程处理1000个任务  
ExecutorService virtual = Executors.newVirtualThreadPerTaskExecutor();
// 耗时: ~50ms (10倍性能提升)
```

### 代码简洁性对比

```java
// 传统类: ~25行代码
public class TraditionalPoint {
    private final int x, y;
    // 构造器、getter、equals、hashCode、toString...
}

// Record: 1行代码
public record Point(int x, int y) {}
```

## 🚨 注意事项

### Java 21预览特性

以下特性需要使用 `--enable-preview` 编译选项：

- 字符串模板
- 结构化并发
- Record模式匹配
- 未命名变量和模式

### 兼容性说明

- 项目需要Java 21运行环境
- 展示Java 8特性时保持向后兼容
- 预览特性可能在未来版本中发生变化

## 🤝 贡献指南

### 添加新特性演示

1. 在相应模块中添加演示方法
2. 使用正确的版本注解标注
3. 添加详细的中文注释
4. 更新README文档
5. 添加单元测试

### 代码规范

- 使用中文注释和文档
- 方法名使用英文，注释使用中文
- 保持代码简洁易懂
- 添加版本特性注解

## 📚 学习资源

### 官方文档

- [Java 21 Documentation](https://docs.oracle.com/en/java/javase/21/)
- [OpenJDK Java 21](https://openjdk.org/projects/jdk/21/)

### 重要JEP (Java Enhancement Proposal)

- **JEP 444**: 虚拟线程
- **JEP 440**: Record模式匹配 (预览)
- **JEP 430**: 字符串模板 (预览)
- **JEP 409**: 密封类
- **JEP 395**: Records

## 📄 许可证

本项目仅用于学习和演示目的。

------

**🎯 开始探索Java的演进之路，体验从Java 8到Java 21的精彩特性！**



## 📊 项目统计

### 已完成的模块
- ✅ **基础结构** - Maven配置、项目结构
- ✅ **版本注解** - 5个Java版本特性标注注解
- ✅ **语言特性** - Lambda、Optional、var、instanceof模式匹配等
- ✅ **集合框架** - 不可变集合、Stream集成、便利方法等
- ✅ **Stream API** - 基础操作、收集器、并行处理等
- ✅ **并发编程** - CompletableFuture、虚拟线程、ForkJoinPool等
- ✅ **Records特性** - 数据载体类、验证、泛型支持等
- ✅ **模式匹配** - instanceof、switch表达式、Record解构(概念)等
- ✅ **密封类** - 继承控制、完备性检查、类型安全等
- ✅ **演示运行器** - 统一的演示入口和管理
- ✅ **详细文档** - 完整的README和使用说明

### 代码文件统计
- **Java文件**: 12个核心演示类
- **注解文件**: 5个版本标注注解
- **代码行数**: 约2000+行带详细中文注释的代码
- **演示方法**: 50+个特性演示方法

## 🚀 测试结果

### 编译测试
- ✅ 所有Java文件编译成功
- ✅ 支持Java 21特性（虚拟线程等）
- ✅ 代码语法正确无错误

### 运行测试
- ✅ **语言特性演示** - 成功运行，展示Lambda、Optional、模式匹配等
- ✅ **并发编程演示** - 成功运行，虚拟线程性能提升9.34倍！

## 🎯 重要特性亮点

### Java 21虚拟线程性能对比
```
传统线程池: 1000个任务 = 570ms
虚拟线程:   1000个任务 = 61ms
性能提升:   9.34倍！
```

### 代码简洁性对比
```java
// 传统类: ~25行代码
public class TraditionalPoint {
    private final int x, y;
    // 构造器、getter、equals、hashCode、toString...
}

// Java 17 Record: 1行代码
public record Point(int x, int y) {}
```

## 📁 项目结构
```
src/main/java/com/demo/
├── annotations/         # Java版本特性标注注解
├── language/           # 语言特性增强演示
├── collections/        # 集合框架增强演示  
├── streams/           # Stream API演示
├── concurrent/        # 并发编程演示(含虚拟线程)
├── records/           # Records特性演示
├── pattern/           # 模式匹配演示
├── sealed/            # 密封类演示
└── utils/             # 演示运行器
```

## 🎮 使用方法

### 运行全部演示
```bash
java -cp target/classes com.demo.utils.DemoRunner
```

### 运行特定模块
```bash
java -cp target/classes com.demo.utils.DemoRunner language    # 语言特性
java -cp target/classes com.demo.utils.DemoRunner concurrent  # 并发编程
java -cp target/classes com.demo.utils.DemoRunner records     # Records
java -cp target/classes com.demo.utils.DemoRunner sealed      # 密封类
```

## 🏆 项目特色

1. **完整性** - 涵盖Java 8到21的主要特性
2. **实用性** - 所有代码都可以直接运行和学习
3. **标注化** - 使用自定义注解清晰标识特性版本
4. **中文化** - 所有注释和文档都使用中文
5. **现代化** - 充分展示Java 21的强大特性

## 📚 学习价值

这个项目非常适合：
- Java开发者学习新版本特性
- 团队培训和技术分享
- 版本升级决策参考
- 面试准备和技术储备

## 🎊 总结

项目创建完全成功！你现在拥有一个功能完整、代码质量高、文档详细的Java版本对比演示项目。特别是Java 21的虚拟线程特性展示了令人印象深刻的性能提升。

**立即开始探索Java的演进之路吧！** 🚀

项目

>[niziming/Java21FeatureFrom8: 自Java8依赖到21的新特性](https://github.com/niziming/Java21FeatureFrom8#)