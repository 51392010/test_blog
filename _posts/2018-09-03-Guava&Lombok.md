---
layout: post
title: Guava & Lombok使用手册
date: 2018-09-03
tag: JAVA
---

### Guava是什么?
Guava是一种基于开源的Java库，其中包含谷歌正在由他们很多项目使用的很多核心库。这个库是为了方便编码，并减少编码错误。这个库提供用于集合，缓存，支持原语，并发性，常见注解，字符串处理，I/O和验证的实用方法。

### Guava的好处
- 标准化 - Guava库是由谷歌托管。
- 高效 - 可靠，快速和有效的扩展JAVA标准库
- 优化 -Guava库经过高度的优化。
- 函数式编程 -增加JAVA功能和处理能力。
- 实用程序 - 提供了经常需要在应用程序开发的许多实用程序类。
- 验证 -提供标准的故障安全验证机制。
- 最佳实践 - 强调最佳的做法。

### Guava环境配置
Guava需要有JAVA的支持，才可操作。

在Maven pom.xml文件中添加对应的Guava jar包即可
```
<dependency>
	<groupId>com.google.guava</groupId>
	<artifactId>guava</artifactId>
	<version>21.0</version>
</dependency>
```
感兴趣的朋友可参考[参考资源]或访问[官网文档]细看！

---

### Lombok介绍
Lombok主要为开发人员提供快捷的方式来简洁代码，减少很多重复代码的书写，比如说我们写的比较繁琐的Setter/Getter/toString等方法。

Lombok需要安装一个插件，安装完之后即可查看效果。

### IDEA中的安装
打开IDEA的Setting –> 选择Plugins选项 –> 选择Browse repositories –> 搜索lombok –> 点击安装 –> 安装完成重启IDEA

### 引入依赖
在项目中添加Lombok依赖jar，在pom文件中添加如下部分。
```
<!-- https://mvnrepository.com/artifact/org.projectlombok/lombok -->
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.16.18</version>
    <scope>provided</scope>
</dependency>
```

### Lombok使用
如下表示设置这几个变量的Setter/Getter方法
```
import lombok.Getter;
import lombok.Setter;

@Setter
@Getter
public class Student {
    
    private String id;
    
    private String name;
    
    private String age;
    
    private String sex;
}
```

### Lombok有哪些注解
- @Setter
- @Getter
- @Data
- @Log(这是一个泛型注解，具体有很多种形式)
- @AllArgsConstructor
- @NoArgsConstructor
- @EqualsAndHashCode
- @NonNull
- @Cleanup
- @ToString
- @RequiredArgsConstructor
- @Value
- @SneakyThrows
- @Synchronized

### 介绍几个常用的Lombok注解

@Getter和@Setter

该注解使用在类或者属性上，该注解可以使用在类上也可以使用在属性上。生成的getter遵循布尔属性的约定。例如：boolean类型的sex,getter方法为isSex而不是getSex

在使用该注解时，会默认生成一个无参构造。和对应的getterhe setter方法 

当然也可以使用在单个属性变量上：如下所示
```
import lombok.Getter;
import lombok.Setter;

public class Student {
    
    private String id;

    @Setter
    @Getter
    private String name;
    
    private String age;
    
    private String sex;
}

```

@Data 一般使用最多

该注解只能使用在类上，该注解会提供getter、setter、equals、canEqual、hashCode、toString方法。
```
import lombok.Data;

@Data
public class Student {

    private String id;

    private String name;

    private String age;

    private String sex;
}

```

@NonNull

该注解使用在属性上，该注解用于属的非空检查，当放在setter方法的字段上，将生成一个空检查，如果为空，则抛出<font color='red'>NullPointerException</font>。 

该注解会默认是生成一个无参构造。
```
import lombok.NonNull;

public class Student {

    @NonNull
    private String id;

    private String name;

    private String age;

    private String sex;
}

```

*至此Guava&Lombok讲解就到此为止了，感谢参考。我也捕捉到了一只小跳跳！*

*参考资源：*[Guava教程™](https://www.yiibai.com/guava)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Project Lombok](https://www.projectlombok.org/)