# Scala traits like abstract classes

```scala
trait Pet {
  def speak = println("yo") // CONCRETE implementation
  def comeToOwner(): Unit   // ABSTRACT
}

class Dog(name: String) extends Pet {
  def comeToOwner(): Unit = println("Woo-hoo, I'm coming!")
}
```

- Classes that extend a trait should implement the abstract methods
  - AI Chat says you'll get a compile time error if this isn't accomplished
- There is no need to redefine a concrete implemenetation unless you wanted to override it.

## Overriding an implemented method

```scala
class Cat extends Pet {
  // override 'speak'
  override def speak(): Unit = println("meow")
  def comeToMaster(): Unit = println("That's not gonna happen")
}
```

## Mixxing in multiple traits that have behaviors

```scala
trait Speaker {
    def speak(): String   //abstract
}

trait TailWagger {
    def startTail(): Unit = println("tail is wagging")
    def stopTail(): Unit = println("tail is stopped")
}

trait Runner {
    def startRunning(): Unit = println("I'm running")
    def stopRunning(): Unit = println("Stopped running")
}

class Dog(name: String) extends Speaker with TailWagger with Runner {
    def speak(): String = "Woof!"
}

class Cat extends Speaker with TailWagger with Runner {
    def speak(): String = "Meow"
    override def startRunning(): Unit = println("Yeah ... I don't run")
    override def stopRunning(): Unit = println("No need to stop")
}
```

## Mixing traits on the fly

```scala
trait TailWagger {
    def startTail(): Unit = println("tail is wagging")
    def stopTail(): Unit = println("tail is stopped")
}

trait Runner {
    def startRunning(): Unit = println("I'm running")
    def stopRunning(): Unit = println("Stopped running")
}

class Dog(name: String)

val d = new Dog("Fido") with TailWagger with Runner
```

- Even if the class initialization didn't specify traits to build from, you can do so when you instantiate a new instance of that class
- According to AI, `extends` and `with` generally perform the same action.
