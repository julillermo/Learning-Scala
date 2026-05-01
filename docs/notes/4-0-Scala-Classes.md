# Scala Classes

## Basic class constructor

```scala
class Person(var firstName: String, var lastName: String)

val p = new Person("Bill", "Panner")
```

- "Definint parameters in a class constructure automatically creates fields in the class ..."
- Because they were defined using `var` (variable), they're also mutable

```scala
println(p.firstName + " " + p.lastName)
// Bill Panner

p.firstName = "William"
p.lastName = "Bernheim"
```

- The above is rougly equivalent to the following Java code

```java
// java
public class Person {
  private String firstName;
  private String lastName;

  public Person(String firstName, String lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  public String getFirstName() {
    return this.firstName;
  }

  public void setFirstName(String firstName) {
    this.firstName = firstName;
  }

  public String getLastName() {
    return this lastName;
  }

  public void setLastName(String lastName) {
    this.lastName = lastName
  }
}
```

## `val` makes fields read-only

```scala
class Person (val firstName: String, val lastName: String)
```

> Tip: if you use Scala to write OOP code, create your fields as `var` fields so you can mutate them. When you write FP code in Scala, you'll generally use case classes instead of classes like this. (More on this later)

## Class constructors

- From what I understand, all statements inside the class declaration is part of the constructor and will be called.

```scala
class Person (var firstName: String, var lastName: String) {
  println("the constructor begins")

  // publicly acessible by default
  var age = 0

  // class specific fields
  private val HOME = System.getProperty("user.home")

  // some methods
  override def toString(): String = s"$firstName $lastName is $age years old"

  def printHome(): Unit = println(s"Home = $HOME")
  def printFullName(): Unit = println(this) // accesses toString()

  printHome()
  printFullName()
  println("you've reached the end of the constructor")
}
```

```scala
// scala repl result
scala> val p = new Person("Kim", "Carnes")
// the constructor begins
// HOME = /Users/al
// Kim Carnes is 0 years old
// you've reached the end of the constructor
// p: Person = Kim Carnes is 0 years old
```

## Other class examples

```scala
class Pizza (var crustSize: Int, var crustType: String)

class Stock(var symbol: String, var price: BigDecimal)

class Socket(val timeout: int, val linger: Int) {
  override def toString = s"timeout: $timoue, linger: $linger"
}

class Address(
  var street1: String,
  var street2: String,
  var city: String,
  var state: String
)
```
