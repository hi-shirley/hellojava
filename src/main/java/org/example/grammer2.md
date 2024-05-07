# ** java notes——basic knowledge 41- 81**

## 41. interface
a template that can be applied to a class. An interface can contain methods and variables, but the methods in an interface are abstract by default. The interface is used to specify what a class must do 
```java
public interface Prey {
    // abstract method,can not have a body
    void flee();
}
public interface Predator {
    void hunt();
}

public class fish implements Prey,Predator{
    @Override
    public void flee(){
        System.out.println("Fish is fleeing");
    }
    @Override
    public void hunt(){
        System.out.println("Fish is hunting");
    }
}

public class Main {
    public static void main(String[] args) {
        fish myFish = new fish();
        // call the methods of two interfaces
        myFish.flee();
        myFish.hunt();
    }
}
```

## 42.polymorphism
* an ability of an object to identify as more than one type
* for example: car is identified as a Vehicle and a Car
```java
public class Car extends Vehicle{
    @Override
    void go(){
        System.out.println("The car begins moving");
    }
}

public class Boat extends Vehicle{
    @Override
    void go(){
        System.out.println("The boat begins moving");
    }
}

public class Vehicle(){
    void go(){
        System.out.println("This vehicle begins moving");
    }
}

public class Main {
    public static void main(String[] args) {
        Car car = new Car();
        Boat boat = new Boat();
        
        // Car[] racers = {car,boat};
        // because both car and boat belong to vehicle,so it's better to contain them in a Vehicle date type
        Vehicle[] racers = {car,boat};
        
        // we can use for-each loop to call go method one by one
        for(Vehicle x : racers) {
            x.go();
        }
    }
}
```
## 43.dynamic polymorphism

```java
public class Animal {
    void speak(){
        System.out.println("Animal is *bu*");
    }
}
public class Cat extends Animal{
    @Override
    void speak(){
        System.out.println("This cat is meow");
    }
}
public class Dog extends Animal{ @Override
void speak(){
    System.out.println("This dog is bark");
}
}
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        // advantage of dynamic polymorphism
        // you can declare an object and make space for it even you don't know what kind of object it is
        Animal animal;

        System.out.println("what kind of animal do you prefer?");
        System.out.print("1 represent dog and 2 represent cat");
        int choice = scanner.nextInt();

        if(choice==1){
            animal = new Dog();
            animal.speak();
        }
        else if(choice==2){
            animal = new Cat();
            animal.speak();
        }
        else{
            animal = new Animal();
            System.out.println("your choice is invalid");
        }
    }
}
```
## 44. exception handling
* exception: an event that occurs during the execution of a program that disrupts the normal flow of instructions
* three steps:
  * try{}
  * catch(){}: there is still a priority of error,try to write the more specific error first
  * finally{}: this block will always be executed no matter what happens

```java
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        try {
            System.out.println("Enter a whole number to divide");
            int x = scanner.nextInt();
            System.out.println("Enter a whole number to divide by");
            int y  = scanner.nextInt();

            int z = x/y;
            System.out.println("result"+z);
        }
        catch(ArithmeticException a){
            System.out.println("zero division error");
        }
        catch(InputMismatchException i){
            System.out.println("please enter a number");
        }
        catch(Exception e){
            System.out.println("something goes wrong");
        }
        
        finally {
            scanner.close();
            System.out.println("this block will always be executed");
        }
    }
}
```
