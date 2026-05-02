# Abstract Classes

- Concept is similar with Java's abstract class
- You rarely need to use abstract classes because traits are already useful enough. Generally, only use abstract class when:
  - You want to create a base class that requires constructor agruments
  - Your Scala code will be called from Java code
    - Java doesn't have the concept of Scala's traits

## Scala traits don't have constructor parameteres

```scala
// this won't compile
trait Animal(name:String)

abstract class Animal(name: String)
```

- Not that classes can only extend one abstract class

## Abstract class syntax

```scala
abstract class Pet (name: String) {
  def speak(): Unit = println("Yo") // concrete implementation
  def comeToMaster(): Unit          // abstract method
}

// notice the `name` as an argument
class Dog(name: String) extends Pet(name) {
  override def speak() = println("Woof")
  def comeToMaster() = println("Here I come!")
}
```

```scala
abstract class Pet (name: String) {
  def speak(): Unit = println(s"My name is $name") // concrete implementation
def comeToMaster(): Unit                          // abstract method
}

// notice the `name` as an argument
class Dog(name: String) extends Pet(name)

val d = new Dog("Fido")
d.speak
```
