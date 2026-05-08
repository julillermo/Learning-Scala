# Scala Futures

- Will cover parallel and concurrent applications in Scala
- You can still reach for Java `Thread` in scala, but Scala `Future` makes parallel/concurrent work simpler.

> "A `Furure` rerepents a value which may or may not currently be available, but will be available at some point, or an exception if that value could not be made available."

**Single-threaded example**

```scala
def aShortRunningTask(): Int = 42
val x = aShortRunningTask
```

**Future variant**

```scala
def aLongRunningTask(): Future[Int] = ???
val x = aLongRunningTask
```

- In the above, the value for `x` may or may not be currently available, but eventually will be
- The `Future` variant expects a long running task, and it Scala assigns it on a separte thread that will communicate back after completion.

## An example in the REPL

- FWIU: This generally feels like a `promise` in JavaScript/TypeScript

```
import scala.concurrent.Future
import scala.concurrent.ExecutionContext.Implicits.global
import scala.util.{Failure, Success}

scala> val a = Future { Thread.sleep(10*1000); 42 }
a: scala.concurrent.Future[Int] = Future(<not completed>)

scala> val b = a.map(_ * 2)
b: scala.concurrent.Future[Int] = Future(<not completed>)
```

- You see `Future(<not completed>)`, but if you revisit it later on, by accessing the value, a result is available

```
scala> a
val res0: scala.concurrent.Future[Int] = Future(Success(42))

scala> b
val res1: scala.concurrent.Future[Int] = Future(Success(84))
```

- _"The value in a `Future` is always an instance of one of the `Try` types: `Success` or `Failure`."_
  - You can use the `Try` pattern to make use of a `Future` value
  - FWIU: Yes, this does feel a lot like promies in JavaScript/TypeScript
  - ALERT: It would appear that Scala also has a `Promise` keyword, just to be clear.

```scala
a.onComplete {
  case Success(value) => println(s"Got the callback, value = $value")
  case Failure(e) => e.printStackTrace
}
```

## An example application

- example using multiple futures.
  - How to create futures
  - How to combine multiple futures in a `for` expression and then into a single result
  - How to work with the returned result

### potentially slow-running method

- Reach for third-party APIs can be slow and eventually even fail. These are often run with the use of `Future`.
- Notice in the following code example that passing a code block to a `Future` constructor, it already runas as a `Future`

```scala
// an example call to a third-party
def getStockPrice(stockSymbol: String): Future[Double] = Future {
  var r = scala.util.Random
  var randomSleepTime = r.nextInt(3000)
  val randomPrice = r.nextDouble * 1000
  sleep(randomSleepTime)
  randomPrice
}
```

- The following example is for when you want the result to be acted on when all 3 stock prices have returned a value. Kind of like a `Promise.all()` in JavaScript.
- Notice that functions can be declared at the later part of the class/object, and the code above is executed in sequencef

```scala
package futures

import scala.concurrent.ExecutionContext.Implicits.global
import scala.concurrent.Future
import scala.util.{Failure,Success}

object MultipleFutures extends App {
  // use this to determine the "delta time" below
  val startTime = currentTime

  // (a) create three futures
  val aaplFuture = getStockPrice("AAPL")
  val amznFuture = getStockPrice("AMZN")
  val googFuture = getStockPrice("GOOG")

  // (b) get a combined result in a for-expression
  val result: Future[(Double, Double, Double)] = for {
    aapl <- aaplFuture
    amzn <- amznFuture
    goog <- googFuture
  } yield (aapl, amzn, goog)

  result.onComplete{
    case Success(x) => {
      val totalTime = deltaTime(startTime)
      println(s"In Success case, time delta: ${totalTime}")
      println(s"The stock prices are: $x")
    }
    case Failure(e) => e.printStackTrace
  }

  // important for a short parallel demo: you need to keep
  // the JVM's main thread alive
  sleep(5000)

  def sleep(time: Long): Unit = Thread.sleep(time)

  // a simulated web service
  def getStockPrice(stockSymbol: String): Future[Double] = Future {
    var r = scala.util.Random
    val randomSleepTime = r.nextInt(3000)
    println(s"For $stockSymbol, sleep time is $randomSleepTime")
    val randomPrice = r.nextDouble * 1000
    sleep(randomSleepTime)
    randomPrice
  }

  def currentTIme = System.currentTimeMillis()
  def deltaTime(t0: Long) = currentTime - t0
}
```

### The `for` expression

- _"Whenever `aapl`, `amzn`, `goog` all return with their values, combine them in a tuple, and assign that value to the variable `result`"_

### About the `sleep` call

- This keeps the main thread of the JVM alive for five seconds (for demonstration purposes)
- Without it, JVM's thread will exit before the Futures complerte. This usually isn't an issue in real-world applications, but this is required for demos/prototypes like this.

## Other Future methods

- `onComplete`
- `onSuccess`
- `onFailure`
- `filter`
- `foreach`
- `map`
- `andThen`
- `fallbackTo`
- `recoverWith`
