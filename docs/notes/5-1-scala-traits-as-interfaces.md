# Scala traits as interfaces

- Scala's `trait` can be used like Java's `interface`

```scala
trait TailWagger {
  def startTail(): Unit
  def stopTail(): Unit
}
```

- Classes that would implement TailWagger would inherit `startTail()` and `stopTail()`

## Extending the trait

```scala
trait TailWagger {
  def startTail(): Unit
  def stopTail(): Unit
}

class Dog extends TailWagger {
  def startTail() = println("tail is waggin")
  def stopTail() = println("tail is stopped")
}
```

## Extending multiple traits

```scala
trait Speaker {
  def speak(): Stirng
}

trait TailWagger {
  def startTail(): Unit
  def stopTail(): Unit
}

trait Runner {
  def startRunning(): Unit
  def stopRunning(): Unit
}

class Dog extends Speaker with TailWagger with Runner {
  // Speaker
  def speak(): String = "Woof!"

  // TailWagger
  def startTail(): Unit = println("tail is wagging")
  def stopTail(): Unit = println("tail is stopped")

  // Runner
  def startRunning(): Unit = println("I'm running")
  def stopRunning(): Unit = println("Stopped running")
}
```

- Notice the use of `extends` along with `with`
