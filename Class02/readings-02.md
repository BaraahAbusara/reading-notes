# Class-02 Arrays, Loops, Imports

In this file I will be summarizing what I have learnt in class-02 reading notes which included the following resources : 
- [Java Imports.](https://perso.ensta-paris.fr/~diam/java/online/notes-java/language/10basics/import.html)
- [Different types of loops in Java.](https://www.baeldung.com/java-loops)


## Loops 
***
> looping is a feature which facilitates the execution of a set of instructions until the controlling Boolean-expression evaluates to false.

Java has different types of loops :
### For loop 
```
for (int counter =0 ;counter<=10;counter++)
{
    System.out.print(counter+" ");
}
//output : 0 1 2 3 4 5 6 7 8 9 10 
```

### While loop 
```
int counter=0;
while (counter<=10)
{
    System.out.print(counter+" ");
}
//output : 0 1 2 3 4 5 6 7 8 9 10 
```

### Do while loop 
```
int counter=0;
do
{
    System.out.print(counter+" ");
} while (counter<=10);
//output : 0 1 2 3 4 5 6 7 8 9 10 
```
## Java imports
***
### Packages:
#### What?
packages are like making certain java classes inside one container/directory/file .

#### Why?
because they have certain relationship between them , like all are related to finance methodologies so we put them all in one package and import them all together in one import line. 

#### How?
you creat it when you define your java program and give it a name same as the directory which includes all .java files (classes) name. 

#### Syntax of declaration:

```
package pakageName;
```
we add it to the very beggining of the file and after it we start our imports , following most common imports in java files :

>import java.awt.*;	Common GUI elements.  
import java.awt.event.*;	The most common GUI event listeners.  
import javax.swing.*;	More common GUI elements. Note "javax".  
import java.util.*;	Data structures (Collections), time, Scanner, etc classes.  
import java.io.*;	Input-output classes.  
import java.text.*;	Some formatting classes.  
import java.util.regex.*;	Regular expression classes.  

<!-- taken from Java Notes Packages and Import -->
