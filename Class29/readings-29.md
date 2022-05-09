# Class-29 : Room
***

In this file I will be summarizing what I have learnt in class-29 reading notes which included the following resources :
- [Overview: Saving data with Room](https://developer.android.com/training/data-storage/room).
- [Defining entities in Room](https://developer.android.com/training/data-storage/room/defining-data)
- [Related entities in Room](https://developer.android.com/training/data-storage/room/relationships)
- [Accessing data with Room](https://developer.android.com/training/data-storage/room/accessing-data#java)


** Room dependencies**
````
dependencies {
    def room_version = "2.4.2"

    implementation "androidx.room:room-runtime:$room_version"
    annotationProcessor "androidx.room:room-compiler:$room_version"

    // optional - RxJava2 support for Room
    implementation "androidx.room:room-rxjava2:$room_version"

    // optional - RxJava3 support for Room
    implementation "androidx.room:room-rxjava3:$room_version"

    // optional - Guava support for Room, including Optional and ListenableFuture
    implementation "androidx.room:room-guava:$room_version"

    // optional - Test helpers
    testImplementation "androidx.room:room-testing:$room_version"

    // optional - Paging 3 Integration
    implementation "androidx.room:room-paging:2.5.0-alpha01"
}
````
There are three major components in Room:
1. The database class for the database and holding data.
2. Data entities for representing tables in the application.
3. Data access objects (DAOs) that provides methods the application needs to work and use the database.

![Relationship between room components ](https://developer.android.com/images/training/data-storage/room_architecture.png)

### Sample implementation :
#### Data entity with @Entity and @PrimaryKey
````
@Entity
public class User {
    @PrimaryKey
    public int uid;

    @ColumnInfo(name = "first_name")
    public String firstName;

    @ColumnInfo(name = "last_name")
    public String lastName;
}
````
you can set an individual primary key like an Id or a composite one using @Entity(primaryKeys = {"firstName", "lastName"})
````
@Entity(primaryKeys = {"firstName", "lastName"})
public class User {
    public String firstName;
    public String lastName;
}
````
And you can set your field unique in the database using 
````
@Entity(indices = {@Index(value = {"first_name", "last_name"},
        unique = true)})
````
or even ignore a field using 
````
   @Ignore
    Bitmap picture;
````
#### Data access object using @Dao
````
@Dao
public interface UserDao {
    @Query("SELECT * FROM user")
    List<User> getAll();

    @Query("SELECT * FROM user WHERE uid IN (:userIds)")
    List<User> loadAllByIds(int[] userIds);

    @Query("SELECT * FROM user WHERE first_name LIKE :first AND " +
           "last_name LIKE :last LIMIT 1")
    User findByName(String first, String last);

    @Insert
    void insertAll(User... users);

    @Delete
    void delete(User user);
}
````

#### Database
First to make a database the database class must satisfy the couple conditions:
1. The class must include @Database that has entities array which includes all of the data entities related to the database.
2. The class must be an abstract class that extends RoomDatabase.
3. For each DAO class that is related to the database, the database class must define an abstract method that has zero arguments and returns an instance of the DAO class.

then we can define our database :
````
@Database(entities = {User.class}, version = 1)
public abstract class AppDatabase extends RoomDatabase {
    public abstract UserDao userDao();
}
````
then we can create an instance of our database :
````
AppDatabase db = Room.databaseBuilder(getApplicationContext(),
        AppDatabase.class, "database-name").build();
````
and interact with it using methods by creating an instance of the DAO:
````
UserDao userDao = db.userDao();
List<User> users = userDao.getAll();
````

## Related entities in Room
In Room, we can create a relationship in two ways :
1. Using intermediate data class.
2. Using a relational query method with a multimap return type.
What is the difference between them ?
In the intermediate data class approach you will be writing more simple code but with higher complexity, and the multimap return type approach you will write a complex code that makes the SQL quiries do more work that your code was supposed to do in the other approach . 

### Relationships :
In room we can create following relationships:
1. one-to-one
2. one-to-many
3. many-to-many
4. nested relationships

## Accessing data with Room
Data access Object (DAO) is a class annotated with @DAO that includes methods that enable you to deal with your database like getting, adding editing or deleting data from your database . 
DAO's have two types of methods: 
1. Convenience methods  : methods with no SQL code. 
2. Query methods : uses SQL code to interact with the database. 

following an example of a simple DAO that defines methods for inserting, deleting, and selecting `User` objects in a Room database:
```
@Dao
public interface UserDao {
    @Insert
    void insertAll(User... users);

    @Delete
    void delete(User user);

    @Query("SELECT * FROM user")
    List<User> getAll();
}
```

## Things I want to know more about
- `@AutoValue` , I didn't understand its benifits .
- I need to learn more and practice creating relationships.
- I need to practice dealing with my database using different DAO methods. 