# Functional Error Handling in Scala

- Again, there are no null values in Scala because of its closeness to algebra representation because of functional programming.
  - However, you can still encounter exceptions when external servers you're connecting to are down or unavailab.e

## Option/Some/None

```scala
def toInt(s: String): Option[Int] = {
  try {
    Some(Integer.parseInt(s.trim))
  } catch {
    case e: Exception => None
  }
}

// I think the toInt() below pass to the match syntax
toInt(x) match {
  case Some(i) => println(i)
  case None => println("That didn't work.")
}

val y = for {
  a <- toInt(stringA)
  b <- toInt(stringB)
  c <- toInt(stringC)
} yield a + b + c
```

## Try/Success/Failure

- `Try` allows us to catch exceptions
- `Failure` contains the exception

```scala
import scala.util.{Try,Success,Failure}

// Without specifying a way to handle the exception, the following just throws it.

def toInt(s: String): Try[Int] = Try {
    Integer.parseInt(s.trim)
}

// Using the following inside REPL will show success:
//  scala> toInt("1")
//  val res1: scala.util.Try[Int] = Success(1)

// Using the following inside REPL will show the error:
//  scala> toInt("boo")
//  val res0: scala.util.Try[Int] = Failure(java.lang.NumberFormatException: For input string: "boo")

def toIntOneLine(s: String): Try[Int] = Try(Integer.parseInt(s.trim))

// an example to handle the exceptions using match
toInt(x) match {
  case Success(i) => println(i)
  case Failure(s) => println(s"Failed. Reason: $s")
}

// an example to handle the exceptions using for
val y = for {
  a <- toInt(stringA)
  b <- toInt(stringB)
  c <- toInt(stringC)
} yield a + b + c


// The above returns Success(<yield_value>) if all are valid.
// Returns `Failure` if contains string not convertible to int.
```

## Even more ...

- Other similar patterns like these are `Either/Left/Right` (built-in to Scala)
  - The `Option/Some/None` and `Try/Success/Failure` are more common and ideal to start out learning
- The `Try/Success/Failure` is generally for throwing exceptions
- The `Option/Some/None` is generally for avoiing null values.
