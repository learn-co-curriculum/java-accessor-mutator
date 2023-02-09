# Accessor and Mutator Methods

## Learning Goals

- Introduce Accessor (Getter) and Mutator (Setter) Methods
- Use IntelliJ to Generate Getter and Setter Methods

## Introduction

Encapsulation is a programming technique for keeping implementation
details hidden from other classes.  This makes it easier to adapt
and evolve code by isolating other classes from the internal state of a given class.

We use the `private` keyword to encapsulate instance variables.
A private variable is only visible within the class it is declared, so other classes can't see it.
In Java, we define public methods to access or modify the value of a private instance variable.
We can evolve the implementation of a public method if the class design changes, while keeping
the method signature used by other classes the same.

## Accessor and Mutator Methods


The example programs we've worked with so far have involved
as single class, where the `main` method is within the same class as the objects it creates
and methods it calls.   But soon we will start to write programs that consist of several
classes. So how can we access or modify object state if instance variables are private
and only visible in a single class?

In Java, we define public **accessor** and **mutator** methods to get and set private instance variables.

- An accessor method takes no parameters and returns the value of a private instance variable.
  The method return type matches the instance variable's declared type.
  Accessor methods are also called **getter** methods.
    - An accessor method for a non-boolean instance variable `abc` would be named `getAbc`.
    - An accessor method for a boolean instance variable `abc` would be named `isAbc`.
- A mutator method takes one parameter whose type and name match the instance variable's declared type
  and name. Mutator methods don't return a value and are also called **setter** methods.
    - A mutator method for an instance variable `abc` would be named `setAbc` and would take a parameter named `abc`.

Let's see how this works with the `Dog` class, which has instance variables `name` and `waggingTail`.

```java
public class Dog {
  private String name;
  private boolean waggingTail;
}
```

The accessor methods to get each instance variable are `getName` and `isWaggingTail`:

```java
public String getName() {
    return name;
}

public boolean isWaggingTail() {
    return waggingTail;
}
```

The mutator methods to set each instance variable are `setName` and `setWaggingTail`.

```java
public void setName(String name) {
    this.name = name;
}

public void setWaggingTail(boolean waggingTail) {
    this.waggingTail = waggingTail;
}
```

Notice each setter method takes a parameter having the same name as the instance variable.
The parameter `name` shadows the instance variable `name`.  Similarly, the parameter `waggingTail`
shadows the instance variable `waggingTail`.

We must use a qualified name such as `this.name` on the left-hand side of the assignment
state to set the instance variable to the parameter value.

![setter method](https://curriculum-content.s3.amazonaws.com/6676/java-methods/setter.png)

The `Dog` class is thus:

```java
public class Dog {
    private String name;
    private boolean waggingTail;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public boolean isWaggingTail() {
        return waggingTail;
    }

    public void setWaggingTail(boolean waggingTail) {
        this.waggingTail = waggingTail;
    }

}
```

We can then put the `main` method in a separate class `Main` and
call the accessor and mutator methods as shown below.
The `Main` class is referred to as a *driver* class, since it contains the `main`
method that defines the program logic.

```java
public class Main {

    public static void main(String[] args) {
        Dog dog1 = new Dog();
        dog1.setName("fido");
        dog1.setWaggingTail(true);

        System.out.println(dog1.getName());
        System.out.println(dog1.isWaggingTail());
    }

}
```

The code prints:

```text
fido
true
```

## Auto-generation of accessor and mutator methods

IntelliJ can generate accessor and mutator methods for the class fields.

Assume we have the following `Cat` class:

```java
public class Cat {
  private String name;
  private boolean purring;
  private String favoriteToy;
  
}
```

1. Right-click after the fields and select "Generate".     
   ![right click, pick generate](https://curriculum-content.s3.amazonaws.com/6676/java-methods/pick_generate.png)
2. Select "Getter and Setter".    
   ![get set](https://curriculum-content.s3.amazonaws.com/6676/java-methods/get_set.png)
3. Select all of the fields and press "OK".     
   ![select all fields](https://curriculum-content.s3.amazonaws.com/6676/java-methods/select_all_fields.png)

IntelliJ generates a getter and setter method for each field.  Notice the boolean getter is named `isPurring`,
while the string getters are `getName` and `getFavoriteToy`.

```java
public class Cat {
private String name;
private boolean purring;
private String favoriteToy;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public boolean isPurring() {
        return purring;
    }

    public void setPurring(boolean purring) {
        this.purring = purring;
    }

    public String getFavoriteToy() {
        return favoriteToy;
    }

    public void setFavoriteToy(String favoriteToy) {
        this.favoriteToy = favoriteToy;
    }
}
```




## Conclusion

In Java, we define public methods to get and set the value of a private field
such as an instance variable. IntelliJ can generate getters and setters based
on the fields defined in the class. 



