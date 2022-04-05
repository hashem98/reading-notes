# Using WebSocket to build an interactive web application

*  WebSocket is a thin, lightweight layer above TCP. This makes it suitable for using “subprotocols” to embed messages. In this guide, we use STOMP messaging with Spring.is establish open conection but HTTP always you need to hit request to get response.is like TCP for the web 
* STOMP(simple text oriented message protocole) is a subprotocol operating on top of the lower-level WebSocket. 

to start
1. git clone https://github.com/spring-guides/gs-messaging-stomp-websocket.git then unzip it
2. cd into gs-messaging-stomp-websocket/initial

3. by spring choose these dependence 

```
dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-websocket'
	testImplementation 'org.springframework.boot:spring-boot-starter-test'
    implementation 'org.webjars:webjars-locator-core'
    implementation 'org.webjars:sockjs-client:1.0.2'
    implementation 'org.webjars:stomp-websocket:2.3.3'
    implementation 'org.webjars:bootstrap:3.3.7'
    implementation 'org.webjars:jquery:3.1.1-1'
}
```

4. Create a Resource Representation HelloMessage.java Class which have the name 
   Upon receiving the message and extracting the name, the service will process it by creating a greeting and publishing that greeting on a separate queue to which the client is subscribed. The greeting will also be a JSON object
5. To model the greeting representation, add another plain old Java object with a `content property `and a corresponding `getContent()` method
6. create a controller to receive the hello message and send a greeting message

```
@Controller
public class GreetingController {


  @MessageMapping("/hello")
  @SendTo("/topic/greetings")
  public Greeting greeting(HelloMessage message) throws Exception {
    Thread.sleep(1000); // simulated delay
    return new Greeting("Hello, " + HtmlUtils.htmlEscape(message.getName()) + "!");
  }
```

7. Configure Spring for STOMP messaging

```
@Configuration
@EnableWebSocketMessageBroker
public class WebSocketConfig implements WebSocketMessageBrokerConfigurer {

  @Override
  public void configureMessageBroker(MessageBrokerRegistry config) {
    config.enableSimpleBroker("/topic");
    config.setApplicationDestinationPrefixes("/app");
  }

  @Override
  public void registerStompEndpoints(StompEndpointRegistry registry) {
    registry.addEndpoint("/gs-guide-websocket").withSockJS();
  }

}
```
8. Create a Browser Client from JavaScript client that will send messages to and receive messages from the server side

This HTML file imports the `SockJS` and `STOMP` javascript libraries that will be used to communicate with our server through `STOMP` over websocket. We also import `app.js`, which contains the logic of our client application

9. Make the Application Executable
```
@SpringBootApplication
public class MessagingStompWebsocketApplication {

  public static void main(String[] args) {
    SpringApplication.run(MessagingStompWebsocketApplication.class, args);
  }
}
```

10. Build an executable JAR
ou can run the application from the command line with Gradle by `./gradlew bootRun` but  Building an executable jar makes it easy to ship, version, and deploy the service as an application throughout the development lifecycle, across different environments
* build the JAR file by using `./gradlew build`
* run `java -jar build/libs/gs-messaging-stomp-websocket-0.1.0.jar`


Resource

[Real time messaging with websockets](https://spring.io/guides/gs/messaging-stomp-websocket/)
