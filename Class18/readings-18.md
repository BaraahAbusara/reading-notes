# Class-18 : 
***

In this file I will be summarizing what I have learnt in class-18 reading notes which included the following resources : 
- [Many to many relationships](https://www.baeldung.com/hibernate-many-to-many).
- [Security: a humorous overview](https://scholar.harvard.edu/files/mickens/files/thisworldofours.pdf).

## Many to many relationships
***
To make a many to many relationship we use **@ManyToMany** annotation. 
As an example , in studying the relationship between project and employee entities a project may have many employees working on it and an employee may be working on many projects.  

Same in online courses websites, a course may have many students studying it and a student may be studying many courses.  
That is in simple words the many to many relationship , and to do so in coding each entinty should have its table with an Id number as a primary key and we will have a third table as a connection between the two tables including both Ids . 
![many to many relationship](https://img2020.cnblogs.com/blog/1059130/202005/1059130-20200527125145796-1670191302.png)

### Database Setup :
For the employee-project relationship , to set up our database we have to :
1. create our database.
2. create a table for each entity with an Id as a primary key.
3. Create employee_project join table with employee_id and project_id as foreign keys.
4. don't forget to add the proper dependencies, this guid should help you , [Guide to Hibernate4 with Spring](https://www.baeldung.com/hibernate-5-spring).

### Create Models :
We have to create model classes with JPA annotations , such the @ManyToMany, @JoinTable and @JoinColumn annotations. 
We have to make entities refere to eachothers :
```
@Entity
@Table(name = "Project")
public class Project {    
    // ...  
 
    @ManyToMany(mappedBy = "projects")
    private Set<Employee> employees = new HashSet<>();
    
    // standard constructors/getters/setters   
}
```
```
@Entity
@Table(name = "Employee")
public class Employee { 
    // ...
 
    @ManyToMany(cascade = { CascadeType.ALL })
    @JoinTable(
        name = "Employee_Project", 
        joinColumns = { @JoinColumn(name = "employee_id") }, 
        inverseJoinColumns = { @JoinColumn(name = "project_id") }
    )
    Set<Project> projects = new HashSet<>();
   
    // standard constructor/getters/setters
}
```

This association has two sides i.e. the owning side and the inverse side. In our example, the owning side is Employee so the join table is specified on the owning side by using the @JoinTable annotation in Employee class. The @JoinTable is used to define the join/link table.    
**@JoinColumn** annotation is used to specify the join/linking column with the main table   
In the Project class, the mappedBy attribute is used in the **@ManyToMany** annotation to indicate that the employees collection is mapped by the projects collection of the owner side.

