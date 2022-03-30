# Spring Boot and OAuth2


we will learn how to build a sample app doing various things with "social login" using OAuth 2.0 and Spring Boot.
## Single Sign On With GitHub
1. create a Spring Boot application by `https://start.spring.io` and add the dependencies
2.  create index.html and add JavaScript links
3. adding jQuery,webjars "locator" and Twitter Bootstrap  dependency
`webjars "locator" which is provided as a library by the webjars site. Spring can use the locator to locate static assets in webjars without needing to know the exact versions `

4. add  Spring Security OAuth 2.0 Client starter
```
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
```

5. configure your app to use GitHub 
6. Add a New GitHub App
7. indicate the Authorization callback URL as `http://localhost:8080/login/oauth2/code/github`
8. Configure application.yml
```
spring:
  security:
    oauth2:
      client:
        registration:
          github:
            clientId: github-client-id
            clientSecret: github-client-secret
```

## Add a Welcome Page
1. change the client side with JQuery, 

```
<div class="container unauthenticated">
    With GitHub: <a href="/oauth2/authorization/github">click here</a>
</div>
<div class="container authenticated" style="display:none">
    Logged in as: <span id="user"></span>
</div>
<script type="text/javascript">
    $.get("/user", function(data) {
        $("#user").html(data.name);
        $(".unauthenticated").hide()
        $(".authenticated").show()
    });
</script>
```

2. Making the Home Page Public
  * switch off the security on the home page by extending WebSecurityConfigurerAdapter


## Add a Logout Button
1. provide a logout button and some JavaScript to call back to the server to ask for the authentication to be cancelled
2. `/logout` endpoint which will do the right thing for us (clear the session and invalidate the cookie). To configure the endpoint we simply extend the existing `configure() `method in our` WebSecurityConfigurerAdapter`
3. add the CSRF token, which you just made available as a cookie from the backend
4. reference it in your HTML
`<script type="text/javascript" src="/webjars/js-cookie/js.cookie.js"></script>`

## login with GitHub
*  add Google as a second option for the end user
1. set up a project in the Google API Console to obtain OAuth 2.0 credentials
2. ensure that the Authorized redirect URIs field is set to `http://localhost:8080/login/oauth2/code/google`
3. configure the client to point Google
```
spring:
  security:
    oauth2:
      client:
        registration:
          github:
            clientId: github-client-id
            clientSecret: github-client-secret
          google:
            client-id: google-client-id
            client-secret: google-client-secret
        
```
4. add login link in home bage 
```
 <div>
    With Google: <a href="/oauth2/authorization/google">click here</a>
  </div>
  ```

  ## Adding an Error Page for Unauthenticated Users

  ```
  spring:
  security:
    oauth2:
      client:
        registration:
          github:
            client-id: bd1c0a783ccdd1c9b9e4
            client-secret: 1a9030fbca47a5b2c28e92f19050bb77824b5ad1
 ```
 index.html
`<div class="container text-danger error"></div>`
Then, add a call to the /error endpoint, populating the `<div>` with the result then Adding an Error Message

```
index.html
$.get("/error", function(data) {
    if (data) {
        $(".error").html(data);
    } else {
        $(".error").html('');
    }
});
```
* Spring Boot has provided an easy extension point: If you declare a @Bean of type OAuth2UserService, it will be used to identify the user principal. You can use that hook to assert the the user is in the correct organization, and throw an exception if not to Generate a 401 in the Server