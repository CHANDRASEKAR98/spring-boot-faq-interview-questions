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
