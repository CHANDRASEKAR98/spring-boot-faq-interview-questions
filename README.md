# Spring Boot Interview Questions (FAQs)
This Repository contains most frequently asked Spring Boot related question on interviews. Each question contains brief explanation as answers. All the answers are very simple and it may not be considered as the exact definition.

## Questions
### Q1: What is the default server on Spring Boot ?
**Tomcat** is the default server on Spring Boot. You can also add any other server you want by excluding the default server.

### Q2: What is @Configuration annotation ?
It is a class level annotation used to register the beans in **IOC Container**. It also have @Bean annotated methods in it. It is mostly used for manually configuring the dependencies which are not auto configured.

### Q3: Is @Bean annotation used at class level ? If not, in which level it is used ?
**@Bean** annotation is not used at class level. It is actually used in method level.

### Q4: How many annotations are required to start a simple Spring Boot application ?
Only one annotation is needed. It is **@SpringBootApplication**. This annotation contains the features of three other annotations such as @Configuration, @EnableAutoConfiguration, @ComponentScan.

### Q5: You want to add **"Spring Security"** dependency to your application. Where do you add it ?
You can add/ modify the dependencies on **Pom.xml** file in your project. We just have to copy the dependency detail from [Maven Repository Site](https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-web/2.2.6.RELEASE), and paste the detail on Pom.xml file.

### Q6: I have an application with a Bean A which is already registered on IOC. The scope of the registered has to change for every sessions. What should I do ?
We have to specify the scope of the type **session** above the class whose bean is already registered.
If the scope of the class is said to be **session**, then new instance of bean is created on spring container on every HTTP session. It is usually used in web application.
```
@Scope(value = "session")
```

### Q7: How can I use other servers like Jetty instead of using Tomcat ?
To use other servers instead of Tomcat, follow the below steps.
1. Remove **(exclude)** tomcat starter from spring-boot-starter-web
2. Add jetty starter
3. Adjust application.properties if required (optional)
To exclude the tomcat server, modify the starter-web dependency as following:
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <exclusions>
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
        </exclusion>
    </exclusions>
</dependency>
```
Then add the dependency for Jetty.
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jetty</artifactId>
</dependency>
```

### Q8: What will be the output when two methods of same type / classes have @Primary annotation ?
**NoUniqueBeanDefinitionException** excpetion is thrown when the application is started. It says that no qualifying bean is found on the <package> and more than one `Primary` annotation is found.

### Q9: What will be the output when application is started in following scenario ?
#### I have a class `A`. I do not annotate it with @Component but I will autowire it on class `B`.
The application will not start. **UnsatisfiedDependencyException**  exception is thrown. The nested exception is **NoSuchBeanDefinitionException** which tells that there are no qualifying bean of type 'x.x.A' available and it expects at least 1 bean which qualifies as autowire candidate.

### Q10: What will be the output when application is started in following scenario ?
#### I have a class `A`. I will annotate it with @Component but I will not annotate with @Autowired on class `B` when injecting.
**NullPointerException** is thrown because we failed to annotate the bean declaration with @Autowired annotation. @Autowired annotation is used to check and fetch the already registered bean from IOC container.
Here, the class `A` is registered on IOC by @Component annotation but as we didn't autowire it, the application is not able to find the bean on IOC container. Hence the exception will be thrown on application start.

### Q11: Is it require to mention the starter dependencies version on Pom.xml file ?
No, it is not mandatory to specify the dependency version on Pom.xml file. The latest version of the starter dependencies are automatically been calculated based on starter parent dependency version.

### Q12: Which JAR dependency is mandatory for running Spring Boot application ?
`spring-boot-starter-parent` dependency is mandatory for running Spring Boot application. It provides default configurations for our application and a complete dependency tree to quickly build our Spring Boot project.

### Q13: What are the changes you do to change a simple Spring based application to a Spring Boot application ?
1. Include starter-parent dependency.
2. Annotate the main class with @SpringBootApplication.
3. Add the Configuration classes that will be annotated with @Configuration.
4. Migrate the reource files to a particlar folder.
5. Migrate property files if required.
6. If it is a web application, then include ` spring-boot-starter-web` dependency.

### Q14: How many ways are there to create a Spring Boot project ?
1. via [Spring Initializr Site](https://start.spring.io/)
2. via Spring Boot Tool Suite (STS)
3. via Spring Boot CLI

### Q15: What is an entry point of execution in Spring Boot application ?
Not only for Spring Boot application, for all Java based applications and frameworks, `Main method in Main Class` is the entry point of execution.
