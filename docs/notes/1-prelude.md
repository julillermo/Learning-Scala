# Prelude: A Taste of Scala

- Assumes some Java experience.
- Already downloaded and installed Scala

## Overview

- Scala code results in a `.class` file that run on the JVM
- It's easy to use Java libraries in Scala

## Hello World

```scala
// Hello.scala
object Hello extends App {
  println("Hello, world")
}
```

- The above can be ran with `scalac Hello.scala`
  - The `scalac` command is just like `javac`.
  - Creates 2 files (same that you would create with `javac`) compatible with the jvm
    - `Hello$.class`
    - `Hello.class`
  - The `Hello application can be ran using the `scala` command

## The Scala in REPL

- Key in `scala` in the terminal, and it would take you to the repl

## Two types of variables

- `val` for immutable (preferred way to use Scala)
- `var` for mutable (ideally reach for only specific reasons)

## Declaring variable types

```scala
val x = 1
val s = "a string"
val p = new Person("Regina")
```

- Inputting the above into the repl, scala returns the inferred type. Types can be explicitly stated as below:

```scala
val x: Int = 1
val s: String = "a string"
val p: Person = new Person("Regina")
```

## Control structures

### `if/else`

```scala
if (test1) {
  doA()
} else if (test2) {
  doB()
} else if (test3) {
  doC()
} else {
  doD()
}
```

- Note that Scala's if/else **returns a value**
- Can be used as a ternary operator

```scala
val x = if (a < b) a else b
```

### match expressions

- In Scala, the `match` is like the switch-case statement in JavaScript

```scala
val result = i match {
  case 1 => "one"
  case 2 => "two"
  case _ => "not 1 or 2"
}

val booleanAsString = bool match {
  case true => "true"
  case false => "false"
}

def getClassAsString(x: Any): String = x match {
  case s: String => s + " is a String "
  case i: Int => "Int"
  case f: Float => "Float"
  case l: List[_] => "List"
  case p: Person => "Person"
  case _ => "Unknown"
}
```

### `try/catch`

```scala
try {
  writeToFile(text)
} catch {
  case fnfe: FileNotFoundException => println(fnfe)
  case ioe: IOException => println(ioe)
}
```

### for loops and expressions

```scala
for (arg <- args) println(arg)

// "x to y" syntax
for (i <- 0 to 5) println(i)

// "x to y by" syntax
for (i <- to 10 by 2) println(i)

// Add the `yield` keyword with for loops to yield a result.
val x = for (i < 1 to 5) yield i * 2

// Iterating over a list of strings
val fruits = List("apple", "banana", "lime", "orange")
val fruitLenghs = for {
  f <- fruits
  if f.length > 4
} yield f.length
// List(5, 6, 6)
```

### `while` and `do/while`

```scala
while(condition){
  statement(a)
  statement(b)
}

do {
  statement(a)
  statement(b)
}
while(condition)
```

## Classes

```scala
class Person(var firstName: String, var lastName: String) {
  def printFullName() = println(s"$firstName $lastName")
}

val p = new Person("Julia", "Kern")
println(p.firstName) // Julia
p.printFullName() // Julia Kern
p.lastName = "Manes"
p.printFullName() // Julia Manes
```

```scala
class Pizza (
  var crustSize: CrustSize,
  var crustType: CrustType,
  var toppings: ArrayBuffer[Topping]
) {
  def addTopping(t: Topping): Unit = toppings += t
  def removeTopping(t: Topping): Unit = toppings -= t
  def removeAllToppings(): Unit = toppings.clear()
}
```

- The `ArrayBuffer` is like Java's `ArrayList`
  - Based on AI Chat, think of `ArrayBuffer` like `const arr: number[] = []` in TypeScript. It's erquivalent to an `Array` in JavaScript

## Scala methods

- Like in TypeScript, return types are optional
- _It seems to me that the following examples are FUNCTIONS, in general, but are METHODS once within the context of a Class_

```scala
def sum(a: Int, b: Int): Int = a + b
def concatenate(s1: String, s2: String): String = s1 + s2

def sumInfer(a: Int, b: Int) = a + b
def concatenateInfer(s1: String, s2: String) = s1 + s2

val x = sum(1,2)
val y = concatenate("foo", "bar")
```

## Traits

- Will be discussed in greater detail later

```scala
trait Speaker {
  def speak(): String // has no body, so it's abstract
}

trait TailWagger {
  def startTail(): Unit = println("tail is wagging")
  def stopTail(): Unit = println("tail is stopped")
}

trait Runner {
  def startRunning(): Unit = println("I'm running")
  def stopRunning(): Unit = println("Stopped running")
}

// Extend the traits by adding details to the `speak` method
class Dog(name: String) extends Speaker with TailWagger with Runner {
  def speak(): String = "Woof!"
}

class Cat extends Speaker with TailWagger with Runner {
  def speak(): String = "Meow"
  override def startRunning(): Unit = println("Yeah ... I don't run")
  override def stopRunning(): Unit = println("No Need to stop")
}
```

- Classes can build on top of these traits by extending them.
  - I think there's nothing like this from the languages I've used before

## Collection of classes

- It's possible to use the Java collection classes in Scala. People do this when coming from Java and still learning Scala.
- Some basic Scala collection of classes:
  - `List`
  - `ListBuffer`
  - `Vector`
  - `ArrayBuffer`
  - `Map`
  - `Set`

### Populating lists

```scala
val nums = List.range(0, 10)
val nums2 = (1 to 10 by 2).toList
val letters = ('a' to 'f').toList
val letters2 = ('a' to 'f' by 2).toList
```

### Sequence methods

```scala
val nums = (1 to 10).toList
val names = List("joel", "ed", "chris", "maurice")

names.foreach(println)
/*
  joel
  ed
  chris
  maurice
 */

nums.filter(_ < 4).foreach(println)
/*
  1
  2
  3
 */

val doubles = nums.map(_ * 2)
// doubles: List[Int] = list(2 ,4, 6, 8, 10, 12, 14, 16, 18, 20)

val capNames = names.map(_.capitalize)
// capNames: List[String] = List(Joel, Ed, Chris, Maurice)

val lessThanFive = nums.map(_ < 5)
// lessThanFive: List[Boolean] = List(true, true, true, true, false, false, false, false, false, false)

val foldleft = nums.foldLeft(0)(_ + _)
// ((((((((((0 + 1) + 2) + 3) + 4) + 5) + 6) + 7) + 8) + 9) + 10) = 55

val foldright = nums.foldRight(1)(_ * _)
// 1 * (2 * (3 * (4 * (5 * (6 * (7 * (8 * (9 * (10 * 1))))))))) = 3628800

val foldleft = nums.foldLeft(0)(_ - _)
// ((((((((((0 - 1) - 2) - 3) - 4) - 5) - 6) - 7) - 8) - 9) - 10) = -55

val foldright = nums.foldRight(1)(_ - _)
// 1 - (2 - (3 - (4 - (5 - (6 - (7 - (8 - (9 - (10 - 1))))))))) = -4
```

- Note that the following two are equivalent
  - `value doubles = nums.map(_ * 2)`
  - `value doubles = nums.map(x => x * 2)`
    - I might prefer this, but I'm not sure yet.

## Tuples

- As with Python, tuples are like a list that don't contain the same type
- "A tuple can contain between two and 22 values, and all of the values can have different types."
  - `(11, 11.0, "Eleven")`
  - The above is referred to as `Tuple3` because it contains three elements

Example use of a tuple:

```scala
def getAaplInfo(): (String, BigDecimal, Long) = {
  // get the stock symbol, price, and volume
  ("APPL", BigDecimal(123.45), 101202303L)
}

val t = getAaplInfo()

// Accessing the tuple variable
t._1
t._2
t._3

// Accessing tuple via pattern matching
val (symbol, price, volum) = getAaplInfo()
```

## What we haven't shown

- Strings and built-in numeric types
- Packaing and imports
- How to use Java collectsions classes in Scala
- How to use Java libraries in Scala
- How to build Scala Projects
- How to perform unit testing in Scala
- How to write Scala shell scripts
- Maps, Sets, and other collections classes
- Object-oriented programming
- Functional programming
- Concurrency with Futures
- Others
