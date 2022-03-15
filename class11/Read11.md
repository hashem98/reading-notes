# Spring 

Spring is a Java-based open-source application framework. Spring Framework comes with various modules like Spring MVC, Spring Boot, Spring Security which provides various ready to use features for web application development.

### starting with spring 

Download and unzip the source repository for this guide, or clone it using Git: `git clone https://github.com/spring-guides/gs-serving-web-content.git`

cd into `gs-serving-web-content/initial`

Jump ahead to Create a Web Controller.

When you finish, you can check your results against the code in `gs-serving-web-content/complete`

### Create a Web Controller 
* `@Controller`  classes are responsible for preparing a model map with data and selecting a view to be rendered
   and HTTP requests are handled by a controller .

* `@GetMapping` annotation ensures that HTTP GET requests to /greeting are mapped to the greeting() method.
* `@RequestParam` binds the value of the query string parameter `name` into the `name` parameter of the greeting() method.
* The value of the name parameter is added to a `Model` object, ultimately making it accessible to the view template.
* Thymeleaf parses the `greeting.html` template and evaluates the `th:text `expression to render the value of the `${name}` parameter that was set in the controlle
### Run the Application

by `SpringBootApplication` which is a convenience annotation that adds all features you need.

### Build an executable JAR
executable JAR file that contains all the necessary dependencies, classes, and resources and run that. Building an executable jar makes it easy to ship, version, and deploy the service as an application throughout the development lifecycle, you can build it using `./gradlew build`,run it by`java -jar build/libs/gs-serving-web-content-0.1.0.jar`

### Test the Application
`http://localhost:8080/greeting` here the website runing 
to test it Provide a name query string parameter by visiting `http://localhost:8080/greeting?name=User`. Notice how the message changes from “Hello, World!” to “Hello, User!”:

# Spring MVC and Thymeleaf

 MVC stands for Model View Controller, a long standing design pattern that layers an application separating presentation concerns from business logic.

1. Spring model attributes 

model attributes : is pieces of data that can be accessed during the execution of views and it's context variables in Thymeleaf language
Spring Expression Language : is a language that supports querying and manipulating an object graph at runtime.

2. Request parameters

 Request parameters are passed from the client to server like.
 ` https://example.com/query?q=Thymeleaf+Is+Great!`

 3. Session attributes
 Similarly to the request parameters, session attributes can be accessed by using the session. prefix:

 ``` <p th:text="${session.mySessionAttribute}" th:unless="${session == null}">[...]</p>```

 4. ServletContext attributes

 The ServletContext attributes are shared between requests and sessions. In order to access ServletContext attributes in Thymeleaf you can use the #servletContext. prefix
 5. Spring beans
    Thymeleaf allows accessing beans registered at the Spring Application Context with the @beanName syntax


### three main things that spring framework brings to your applications 
1. managing your services and object instancesusing an application context managing dependencies using dependency injection
2. providing data access to simplify connecting to and working with databases
3. the ability to easily build web application using spring Mvc
