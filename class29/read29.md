# Save data in a local database using Room

*Room provides Compile-time verification of SQL queries,Convenience annotations that minimize repetitive and error-prone boilerplate code,Streamlined database migration paths 

to use Room
1. add the dependencies 
2.  The `database class` that holds the database and serves as the main access which The class must be annotated with a `@Database`,and  must be an abstract class that extends `RoomDatabase.`
3. Data entities that represent tables in your app's database.
4. Data access objects (DAOs) that provide methods that your app can use to query, update, insert, and delete data in the database
5.  create an instance of the database
```
AppDatabase db = Room.databaseBuilder(getApplicationContext(),
        AppDatabase.class, "database-name").build();

        UserDao userDao = db.userDao();
List<User> users = userDao.getAll();

```




# Defining data using Room entities

use Room entities to define the database schema without writing any SQL code
1. define each Room entity as a class that is annotated with `@Entity`
2. If you want the table to have a different name, set the tableName property of the `@Entity` annotation,add the `@ColumnInfo` annotation to the field and set the name property
3.  annotate a single column with` @PrimaryKey` or define a composite primary key by listing those columns in the `primaryKeys` property of @Entity

4. If an entity has fields that you don't want to persist, you can annotate them using `@Ignore`

* for search for details in your database's tables. Use full-text search 
* add the `@Fts3` or `@Fts4` annotation to a given entity for very quick access to database information through full-text search (FTS)
* In cases where a table supports content in multiple languages, use the `languageId`


# Define relationships between objects

* we can use the` @Embedded` annotation to represent an object that you'd like to decompose into its subfields within a table. You can then query the embedded fields just as you would for other individual columns

* If an entity has multiple embedded fields of the same type, you can keep each column unique by setting the `prefix` property

### *relationships*

 *one-to-one and one-to-many and many--to-many*

1. create a class for each of your two entities. One of the entities must include a variable that is a reference to the primary key of the other entity.
2. model the one-to-one relationship between the two entities by create a new data class where each instance holds an instance of the parent entity and the corresponding instance of the child entity
3.  Add the `@Relation` annotation to the instance of the child entity, with `parentColumn` set to the name of the primary key column of the parent entity and `entityColumn `set to the name of the column of the child entity that references the parent entity's primary key

4.  add a method to the DAO class that returns all instances of the data class by add the `@Transaction` annotation to this method to ensure that the whole operation is performed atomically
5. in many-to-many  model the relationship between the entities by using the associateBy property in the @Relation annotation in each of these classes to identify the cross-reference entity providing the relationship between classes
6.  add a method to the DAO class to expose the query functionality your app needs.


* nested relationships between the tables to query a set of three or more tables that are all related to each other

# Accessing data using Room DAOs

* always annotate your DAOs with `@Dao.` DAOs don't have properties, but they do define one or more methods for interacting with the data in your app's database

### two types of DAO methods

1. Convenience methods:that let you insert, update, and delete rows in your database without writing any SQL code which annotate with ` @Insert` ,`@Delete`,`@Update`

2. Query methods : that let you write your own SQL query to interact with the database

*Simple queries*
```
@Query("SELECT * FROM user")
public User[] loadAllUsers();

```

*Return a subset of a table's columns*

```
public class NameTuple {
    @ColumnInfo(name = "first_name")
    public String firstName;

    @ColumnInfo(name = "last_name")
    @NonNull
    public String lastName;
}
```
*Pass simple parameters to a query*
```
@Query("SELECT * FROM user WHERE age > :minAge")
public User[] loadAllUsersOlderThan(int minAge);
```

*Pass a collection of parameters to a query*

```
@Query("SELECT * FROM user WHERE region IN (:regions)")
public List<User> loadUsersFromRegions(List<String> regions);
```

*Query multiple tables*

```
@Query("SELECT * FROM book " +
       "INNER JOIN loan ON loan.book_id = book.id " +
       "INNER JOIN user ON user.id = loan.user_id " +
       "WHERE user.name LIKE :userName")
public List<Book> findBooksBorrowedByNameSync(String userName);
```

*Direct cursor access*

```
@Dao
public interface UserDao {
    @Query("SELECT * FROM user WHERE age > :minAge LIMIT 5")
    public Cursor loadRawUsersOlderThan(int minAge);
}
```



resources

[1](https://developer.android.com/training/data-storage/room)
[2](https://developer.android.com/training/data-storage/room/defining-data)
[3](https://developer.android.com/training/data-storage/room/relationships)
[4](https://developer.android.com/training/data-storage/room/accessing-data#java)
