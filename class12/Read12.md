# Spring RequestMapping

* REST Api  is an application programming interface (API or web API) that conforms to the constraints of REST 
* the annotation is used to map web requests to Spring Controller methods.
## RequestMapping 
1. @RequestMapping — by Path
> @RequestMapping(value = "/ex/foos", method = RequestMethod.GET)
2. @RequestMapping — the HTTP Method
> @RequestMapping(value = "/ex/foos", method = POST)
3. @RequestMapping With the headers Attribute
>@RequestMapping(value = "/ex/foos", headers = "key=val", method = GET)
4. @RequestMapping Consumes and Produces
```
@RequestMapping(
  value = "/ex/foos", 
  method = GET, 
  headers = "Accept=application/json")
@ResponseBody
```
5.  RequestMapping With Path Variables
  * Single @PathVariable
  * Multiple @PathVariable
  * PathVariable With Regex
6. RequestMapping With Request Parameters
>http://localhost:8080/spring-rest/ex/bars?id=100
7. New Request Mapping Shortcuts
```
@GetMapping
@PostMapping
@PutMapping
@DeleteMapping
@PatchMapping
```

# Accessing Data with JPA

Spring Data JPA focuses on using JPA to store data in a relational database. Its most compelling feature is the ability to create repository implementations automatically, at runtime, from a repository interface. CustomerRepository extends the CrudRepository interface

* we will build an application that stores Customer POJOs (Plain Old Java Objects) in a memory-based database

# Spring Data Repositories
 some brief but important differences and features of Spring Data JPA repository interfaces

 * CrudRepository provides CRUD functions
  ```
  save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch
  findOne(…) – get a single entity based on passed primary key value
  findAll() – get an Iterable of all available entities in database
  count() – return the count of total entities in a table
  delete(…) – delete an entity based on the passed object
  exists(…) – verify if an entity exists based on the passed primary key value
  ```

* PagingAndSortingRepository provides methods to do pagination and sort records

* JpaRepository provides JPA related methods such as flushing the persistence context and delete records in a batch

 ```
  save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch
  findOne(…) – get a single entity based on passed primary key value
  findAll() – get an Iterable of all available entities in database
  count() – return the count of total entities in a table
  delete(…) – delete an entity based on the passed object
  exists(…) – verify if an entity exists based on the passed primary key value
 ```
