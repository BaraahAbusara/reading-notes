# Class-06 :
***

In this file I will be summarizing what I have learnt in class-06 reading notes which included the following resources : 
- [Java OO Tutorial](https://docs.oracle.com/javase/tutorial/java/concepts/)
- [Java Inheritance & Interfaces Tutorial](https://docs.oracle.com/javase/tutorial/java/IandI/index.html)


**Inheretance:**  
To imagine what is an inheretance you can imagine it as is in normal life , we are all humans have the same properities starting from a hight and width , a name and a skin color .. etc. 
But each family has its own properities and methods (activities). as an example family A started an activity of learning a new language or playing piano but not all humans do so , only members of that family are inheriting the activity of playing piano. Maybe in some late generation the family started playing football so it started inhirithing it and the playing piano and being humans to the next generations.
That is exactly what is inheritance , taking the methods and properities of the parent class and add to it my own methods and properities and being able to give them to my children. 

**Interface:** 
Interface is a class that is made to be inherted but not to be used. Like if a parent bought a new guitar but didn't use it then his children inhirited it and overwrote the method to use it. 
Defining an interface is similar to creating a new class:

```

public interface OperateCar {

   // constant declarations, if any

   // method signatures
   
   // An enum with values RIGHT, LEFT
   int turn(Direction direction,
            double radius,
            double startSpeed,
            double endSpeed);
   int changeLanes(Direction direction,
                   double startSpeed,
                   double endSpeed);
   int signalTurn(Direction direction,
                  boolean signalOn);
   int getRadarFront(double distanceToCar,
                     double speedOfCar);
   int getRadarRear(double distanceToCar,
                    double speedOfCar);
         ......
   // more method signatures
}
``` 
**Packages:**  
packages are putting certain related classes and interfaces in one place. It is like putting all people you know who can play piano in one category to be able to call them once you need any of them. 


