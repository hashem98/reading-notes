# Spring Security Architecture

## Authentication and Access Control(authorization )

* AuthenticationManager is The main strategy interface for authentication and it can do 3 things in it's method
1. Return an Authentication (normally with authenticated=true) valid principal.

2. Throw an AuthenticationException if it believes that the input represents an invalid principal.

3. Return null if it cannot decide.

* AuthenticationProvider instances. An AuthenticationProvider is a bit like an AuthenticationManager, but it has an extra method to allow the caller to query whether it supports a given Authentication type

```
public interface AuthenticationProvider {

	Authentication authenticate(Authentication authentication)
			throws AuthenticationException;

	boolean supports(Class<?> authentication);
}

```

## Customizing Authentication Managers

Spring Security provides some configuration helpers to quickly get common authentication manager features set up in your application like `AuthenticationManagerBuilder`
```
@Configuration
public class ApplicationSecurity extends WebSecurityConfigurerAdapter {

  @Autowired
  DataSource dataSource;

   ... // web stuff here

  @Override
  public void configure(AuthenticationManagerBuilder builder) {
    builder.jdbcAuthentication().dataSource(dataSource).withUser("dave")
      .password("secret").roles("USER");
  }

}
```

## Authorization or Access Control

There are three implementations provided by the framework and all three delegate to a chain of AccessDecisionVoter instances,

```
boolean supports(ConfigAttribute attribute);

boolean supports(Class<?> clazz);

int vote(Authentication authentication, S object,
        Collection<ConfigAttribute> attributes);
```


`ConfigAttribute` is an interface. It has only one method (which is quite generic and returns a String), so these strings encode in some way the intention of the owner of the resource, expressing rules about who is allowed to access it. A typical ConfigAttribute is the name of a user role , and they often have special formats or represent expressions that need to be evaluated.

## Web Security

* is based on Servlet `Filters`
Spring Boot manages it through two mechanisms: `@Beans` of type Filter can have an `@Order` or implement Ordered, and they can be part of a `FilterRegistrationBean` that itself has an order as part of its API

* `FilterRegistrationBean.REQUEST_WRAPPER_FILTER_MAX_ORDER` (the maximum order that a Spring Boot application expects filters to have if they wrap the request, modifying its behavior)

## Request Matching for Dispatch and Authorization
`WebSecurityConfigurerAdapter`  has a request matcher that is used to decide whether to apply it to an HTTP request.

within a filter chain, you can have more fine-grained control of authorization by setting additional matchers in the `HttpSecurity` configurer

## Method Security
As well as support for securing web applications, Spring Security offers support for applying access rules to Java method executions. For Spring Security, this is just a different type of “protected resource”. For users, it means the access rules are declared using the same format of `ConfigAttribute` strings but in a different place in your code


## Working with Threads

Spring Security is fundamentally thread-bound, because it needs to make the current authenticated principal available to a wide variety of downstream consumers. The basic building block is the SecurityContext, which may contain an Authentication (and when a user is logged in it is an Authentication that is explicitly authenticated). You can always access and manipulate the SecurityContext through static convenience methods in SecurityContextHolder, which, in turn, manipulate a ThreadLocal

If you need access to the currently authenticated user in a web endpoint
```
@RequestMapping("/foo")
public String foo(@AuthenticationPrincipal User user) {
  ... // do stuff with user
}
```


## Processing Secure Methods Asynchronously

 if you want to do any background processing that calls secure methods, you need to ensure that the context is propagated To propagate the `SecurityContext` to` @Async` methods, you need to supply an `AsyncConfigurer` and ensure the Executor is of the correct type

 ```
 @Configuration
public class ApplicationConfiguration extends AsyncConfigurerSupport {

  @Override
  public Executor getAsyncExecutor() {
    return new DelegatingSecurityContextExecutorService(Executors.newFixedThreadPool(5));
  }

}
```

