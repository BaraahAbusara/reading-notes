# Class-03  Maps, primitives, File I/O

In this file I will be summarizing what I have learnt in class-03 reading notes which included the following resources : 
- [Primitives vs. Objects]().
- [Exceptions in Java]().
- [Using Scanner to read in a file in Java](https://docs.oracle.com/javase/tutorial/essential/io/scanning.html)

## Primitives vs. Objects
***
In simple words, I learnt that in Java premitive variables like int and boolean are better in memory size and speed since they live in the stack than referenced types like Integer and Double since they requier more space and live in the heap.
In addition to that premitives have initial values but referenced types doesn't (nulls).


## Exceptions in Java
***

### What is an exception in Java?
it is an object that works in the code when an error happens and changes the flow of the code the exception object finds it and handel it.
### What are types of exceptions?
We have 3 main types as follows:
1. checked exception like java.io.FileNotFoundException.
2. error exception like java.io.IOError.
3. runtime exception like NullPointerException.
### How do we use these exceptions?
By throwing it as the following code taken from [The Java™ Tutorials](https://docs.oracle.com/javase/tutorial/essential/exceptions/throwing.html):
```
public Object pop() {
    Object obj;

    if (size == 0) {
        throw new EmptyStackException();
    }

    obj = objectAt(size - 1);
    setObjectAt(size - 1, null);
    size--;
    return obj;
}
```
Or using try-catch as the following code taken from  *Our instructor's code *Jason James:
```
        try (Scanner scanner = new Scanner(file)) {
            while (scanner.hasNextLine()) {
                System.out.println(scanner.nextLine());
            }
        } catch (FileNotFoundException fileNotFoundException) {
            System.err.println(fileNotFoundException.getMessage());
        }
```

## Using Scanner to read in a file in Java
*** 
To do so we use method **Scanner**.
we can use it to read values by word (it stops when it finds a space or endl)
using the following code taken from  [Using Scanner to read in a file in Java](https://docs.oracle.com/javase/tutorial/essential/io/scanning.html) :

```
 Scanner s = null;

        try {
            s = new Scanner(new BufferedReader(new FileReader("xanadu.txt")));

            while (s.hasNext()) {
                System.out.println(s.next());
            }
        } finally {
            if (s != null) {
                s.close();
            }
        }
```

Or read line by line as follows :
```
        try (Scanner scanner = new Scanner(file)) {
            while (scanner.hasNextLine()) {
                System.out.println(scanner.nextLine());
            }
        } catch (FileNotFoundException fileNotFoundException) {
            System.err.println(fileNotFoundException.getMessage());
        }
```
code taken by *Our instructor's code *Jason James.

