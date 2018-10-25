---
layout: post
title: SpringBoot 详解
date: 2018-09-09
tag: JAVA
---

### Spring Boot 特点/优点
- 配置文件少，可以完全脱离xml配置
- 项目搭建速度快，无需整合第三方框架
- 根据pom文件依赖的jar包进行自动配置
- 内嵌Servlet容器，一键启动已不是想象
- 一个基于Spring的应用

### Spring Boot 核心
SpringBoot项目都会有一个入口类，被@SpringBootApplication标注，入口类有一个main方法，用于启动SpringBoot项目。

@SpringBootApplication是一个组合的注解类，如下：
```
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Inherited
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan(excludeFilters = {
		@Filter(type = FilterType.CUSTOM, classes = TypeExcludeFilter.class),
		@Filter(type = FilterType.CUSTOM, classes = AutoConfigurationExcludeFilter.class) })
public @interface SpringBootApplication {
```
比较重要的几个注解详解：

- @SpringBootConfiguration：它代替了Spring中的@Configuration
<br/>
作用：@Configuration等价于在xml配置中的beans，还有一个注解@Bean等价于xml中的bean配置。
<br/>
<br/>
- @ComponentScan：默认扫描标注@SpringBootApplication的当前目录和子目录，也可以设置指定扫描目录下的文件。
<br/>
<br/>
- @EnableAutoConfiguration：启用自动配置，它会根据项目中依赖的jar包进行对应的自动配置。

### 自动配置的幕后：SpringFactoriesLoader 详解
SpringFactoriesLoader属于Spring框架私有的一种扩展方案，主要功能就是从指定的配置文件META-INF/spring.factories加载配置。
![image](http://mmbiz.qpic.cn/mmbiz_jpg/pcT41pYWuUHL6ZWFVCvMDEpd6z50YV0BdBhOVrpZuOXYxgx1N9DsgeIJT0v022JyiaubzEYhuvg5tY1zqUGrtNA/0?wx_fmt=jpeg)

<font color='red'>@EnableAutoConfiguration自动配置是从classpath中搜索所有的spring.factories配置文件，并将EnableAutoConfiguration对应的配置通过反射实例化标注了@Configuration的JavaConfig配置类，然后一起加载到IoC容器中。</font>

### Spring Boot 执行流程
![image](http://mmbiz.qpic.cn/mmbiz_jpg/pcT41pYWuUHL6ZWFVCvMDEpd6z50YV0BV0WRLh7on3ibclf2rjhmOF3Pn8G8Nh66DMuqicS5O6IibPLALkCibiaxoibw/0?wx_fmt=jpeg)