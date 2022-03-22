# Working with Relationships
1. One-to-one relationships
In a one-to-one relationship, one record in a table is associated with one and only one record in another table

![one to one](https://fmhelp.filemaker.com/help/18/fmp/en/FMP_Help/images/one-to-one.png)

*  The Repositories
to expose these entities as resources, let's create two repository interfaces for each of them, by extending the CrudRepository interface
>public interface LibraryRepository extends CrudRepository<Library, Long> {}
>public interface AddressRepository extends CrudRepository<Address, Long> {}
* Creating the Associations
This is done using the HTTP method PUT, which supports a media type of text/uri-list, and a body containing the URI of the resource to bind to the association

* To remove an association
>curl -i -X DELETE http://localhost:8080/libraries/1/libraryAddress

2. One-to-Many Relationship

In a one-to-many relationship, one record in a table can be associated with one or more records in another table

![One-to-Many ](https://fmhelp.filemaker.com/help/18/fmp/en/FMP_Help/images/relational.07.04.2.png)

3.  Many-to-Many Relationship

A many-to-many relationship occurs when multiple records in a table are associated with multiple records in another table.
![Many-to-Many ](https://fmhelp.filemaker.com/help/18/fmp/en/FMP_Help/images/relational.07.06.1.png)


# Integration Testing in Spring
1. Enable Spring in Tests with JUnit 5

JUnit 5 defines an extension interface through which classes can integrate with the JUnit test.

We can enable this extension by adding the @ExtendWith annotation to our test classes and specifying the extension class to load. To run the Spring test, we use SpringExtension.class.

```
@ExtendWith(SpringExtension.class)
@ContextConfiguration(classes = { ApplicationConfig.class })
@WebAppConfiguration
public class GreetControllerIntegrationTest {
    ....
}
```
2. The WebApplicationContext Object
WebApplicationContext provides a web application configuration. It loads all the application beans and controllers into the context
>@Autowired
private WebApplicationContext webApplicationContext;

3.  Mocking Web Context Beans
MockMvc provides support for Spring MVC testing. It encapsulates all web application beans and makes them available for testing.

4. Writing Integration Tests

 What is a Java Integration Test?
Sometimes there is not a clear distinction on what is an integration test and what is a unit test. My basic rule of thumb is that if

a test uses the database
a test uses the network
a test uses an external system (e.g. a queue or a mail server)
a test reads/writes files or performs other I/O

Unit test	| Integration test
------------|-----------------
Results depends only on Java code | Results also depends on external systems
Easy to write and verify  |	Setup of integration test might be complicated
A single class/unit is tested in isolation |One or more components are tested
All dependencies are mocked if needed |No mocking is used (or only unrelated components are mocked)
Test verifies only implementation of code|Test verifies implementation of individual components and their interconnection behaviour when they are used together
A unit test uses only JUnit/TestNG and a mocking framework	|An integration test can use real containers and real DBs as well as special java integration testing frameworks (e.g. Arquillian or DbUnit)
Mostly used by developers| Integration tests are also useful to QA, DevOps, Help Desk
A failed unit test is always a regression (if the business has not changed) |	A failed integration test can also mean that the code is still correct but the environment has changed
Unit tests in an Enterprise application should last about 5 minutes	|Integration tests in an Enterprise application can last for hours
