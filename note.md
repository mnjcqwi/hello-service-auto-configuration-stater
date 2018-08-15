###### Customized Springboot Starter Demo

Commit 1:

通过springboot 来build起来项目，我们的目的是写一个hello-starter。
首先看下我们的pom.xml
并没有我们常见的starter
```XML
	<dependencyManagement>
		<dependencies>
			<dependency>
				<groupId>com.example</groupId>
				<artifactId>hello-service</artifactId>
				<version>0.0.1-SNAPSHOT</version>
			</dependency>

			<dependency>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-dependencies</artifactId>
				<version>${spring-boot.version}</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
		</dependencies>
	</dependencyManagement>
```
我们这里没有用到任关于starter的东西，标准的spring配置除了一个annotation 
@SpringBootApplication

这个是3个annotation组成的
```java
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan
```
这里其实只有EnableAutoConfiguration这个是新的，这个也是SpringBoot实现了自动配置的关键
SpringBootConfiguartion其实是 @Configuration的一个很小的变种，不是很重要

那为什么还需要ComponentScan哪？

其实是因为SpringBoot把初始化分为了两个阶段，一个是userconfiguration，比如你知道你要用什么datasource，你知道你想要
什么样的tomcat port，这些spring不能给你覆盖掉，在后面我们会讲解这个

>另外一个不太重要的，CommandLineRunner是一个在springboot启动之前就跑的程序，
所以打印hello在spring启动之前


