# Class-13 : Related Resources and Integration Testing
***

In this file I will be summarizing what I have learnt in class-13 reading notes which included the following resources : 
- [Related data in Spring : 3. One-to-Many Relationship](https://www.baeldung.com/spring-data-rest-relationships).
- [Baeldung: Spring Integration Testing](https://www.baeldung.com/integration-testing-in-spring).

## Related data in Spring : 3. One-to-Many Relationship 
***
for this relationship we have some annotations to use :
- @OneToMany
- @ManyToOne
- @RestResource (optional).

As an example , is we want to model a library we have to do the following: 
Book entity represents the many end to the library. 
so we first give this relationship to the library as following :  
```
 @ManyToOne
    @JoinColumn(name="library_id")
    private Library library;
```
then add the relationship to the Library class as well:
```
 @OneToMany(mappedBy = "library")
    private List<Book> books;
```
after that create a BookRepository:
```
public interface BookRepository extends CrudRepository<Book, Long> { }
```
then create a Book instance and add this book to the library :
```
curl -i -X POST -d "{\"title\":\"Book1\"}" 
  -H "Content-Type:application/json" http://localhost:8080/books
```
from here we can CRUD our books inside the library. 

## Baeldung: Spring Integration Testing
***
In this article, you will find how to implement Spring-enabled integration tests.  
Starting from dependencies you need to how to deal with CRUD requests and HTTP response status header and content inside it.  
you will also learn about how to call endpoints using WebApplicationContext and MockMvc.  
