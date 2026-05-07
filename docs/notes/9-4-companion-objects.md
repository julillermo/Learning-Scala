# Companion Objects

> A _companion object_ in Scala is an `object` that's declared in the same file as a `class`, and has the same name as the class. For instance, when the following code is saved in a file named `Pizza.scala`, the `Pizza` object is considered to be a compnaion object of the `Pizza` class

```scala
class Pizza {
  def printFilename() = {
    println(SomeClass.HiddenFilename)
  }
}

object Pizza {
  private val HiddenFilename = "/tmp/foo.bar"
}
```

- companion object and it's class can access each other's private members

## Creating new instances without the new keyword

```scala
val zenMasters = List(
  Person("Nansen"),
  Person("Joshu")
)
```

- Question: how does the above create an instance without the `new` keyword.
  - The above `List()` is actually "syntactic sugar". More explicitly, it's equivalent to `val p = Person.apply("Fred Flintsone")` if the `apply()` method is available in the companion object

```
class Person {
  var name = ""
}

object Person {
  def apply(name: String): Person = {
    var p = new Person
    p.name = name
    p
  }
}
```

### Creating multiple constructors

```
class Person {
  var name = Option[String] = None
  var age: Option[Int] = None
  override def toString = s"$name, $age"
}

object Person {
  // a one-arg constructor
  def apply(name: Option[String]): Person = {
    var p = new Person
    p.name = name
    p
  }

  // a two-arg constructor
  def apply(name: Option[String], age: Option[Int]): Person = {
    var p = new Person
    p.name = name
    p.age = age
    p
  }
}
```

## Adding an unapply method

- _"... adding an `unapply` method lets you de-construct object instances"_
- The `unapply` method in scala is like an _extractor_ method.

```scala
class Person(var name: String, var age: Int)

object Person {
  def unapply(p: Person): Tuple2[String, Int] = (p.name, p.age)
}
```

```
scala> val result = Person.unapply(p)
result: (String, Int) = (Lori,29)
```
