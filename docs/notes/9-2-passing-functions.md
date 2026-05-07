# Passing Functions Around

- Functional Programming languages allow you to _create functions as variables_
  - JavaScript does this also
- There was a short discussion on whether what you're declaring is a _function_ vs a _method_.
  - FWIU: Scala just calls functions as _methods_ in general, but in my mind I'm reaching for the term function

```scala
val nums = (1 to 10).toList

val doubles = nums.map(_ * 2)
val lessThanFive = nums.filter(_ < 5)

def doubleFn(i: Int): Int = i * 2

val doublesEquivalent = nums.map(doubleFn)
```

## A few examples

```scala
List("foo", "bar").map(_.toUpperCase)
List("foo", "bar").map(_.capitalize)
List("adam", "scott").map(_.length)
List(1,2,3,4,5).map(_ * 10)
List(1,2,3,4,5).filter(_ > 2)
List(5,1,3,11,7).takeWhile(_ < 6)

// equivalent longer syntax for anomyous functions
List("foo", "bar").map(s => s.toUpperCase)
```
