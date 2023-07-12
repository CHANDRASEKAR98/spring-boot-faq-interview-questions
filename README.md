# Spring Boot Interview Questions (FAQs)
This Repository contains most frequently asked Spring Boot related question on interviews. Each question contains brief explanation as answers. All the answers are very simple and it may not be considered as the exact definition.

## Questions
### Q1: What is the default server on Spring Boot ?
**Tomcat** is the default server on Spring Boot. You can also add any other server you want by excluding the default server.

### Q2: What is @Configuration annotation ?
It is a class level annotation used to register the beans in **IOC Container**. It also have @Bean annotated methods in it. It is mostly used for manually configuring the dependencies which are not auto configured.

### Q3: Is @Bean annotation used at class level ? If not, in which level it is used ?
**@Bean** annotation is not used at class level. It is actually used in method level.

### Q4: How many annotations are reuired to start a simple Spring Boot application ?
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
