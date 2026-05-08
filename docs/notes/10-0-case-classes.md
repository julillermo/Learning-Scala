# Case Classes

- Particularly useful for functional programming
- Has all the functionality of a regular class
- Adding `case` in front of the `class` keyword provides the following benefits:
  - `"Case class constructor parameters are public 'val' fields by default, so accessor methods are generated for each parameter"`
  - An `apply` method is automatically created in the companion object of the class. (no need to use `new` when declaring)
  - An `unapply` method is automatically created in the companion obect.
  - A `copy` method is generated in the class.
  - The `equals` and `hashCode` methods are generated, letting you comapre obects and use them as keys in maps
  - A default `toString` method is generated

## No need to declare `new` with `apply` present

```
scala> case class Person(name: String, relation: String)
defined class Person

// "new" not needed before Person
scala> val christina = Person("Christina", "niece")
christina: Person = Person(Christina,niece)
```

## No mutator methods

- I believe this means you can always access the methods from within a `case class`, but you can't mutate them

```
scala> christina.name
res0: String = Christina

scala> christina.name = "Fred"
<console>:10: error: reassignment to val
       christina.name = "Fred"
```

## The `unapply` method

```scala
trait Person {
  def name: String
}

case class Student(name: String, year: Int) extends Person // note the `case class` declaration
case class Teacher(name: String, specialty: String) extends Person // note the `case class` declaration

// The presence of `unapply` allows us to do the following
def getPrintableString(p: Person): String = p match {
  case Student(name, year) =>
    s"$name is a student in Year $year."
  case Teacher(name, whatTheyTeach) =>
    s"$name teaches $whatTheyTeach."
}
```

- The `case Student(name, year) => ...` and `case Teacher(name, whatTheyTeach) => ...` patterns work because `Student` and `Teacher` are case claseses.

> The Scala standard is that an `unapply` method returns the case class constructor fields in a tuple that's wrapped in an `Option`.

```scala
val s = Student("Al", 1)
val t = Teacher("Bob Don", "Mathematics")
```

- In REPL, the above looks like the following

```
scala> getPrintableString(s)
res0: String = Al is a student in Year 1.

scala> getPrintableString(t)
res1: String = Bob Donnan teaches Mathematics.
```

## The `copy` method of a `case class`

- Helpful for **cloning an object** and **updating one or more fields**
  - I assume "updating a field" here refers to create a new `Class` with updated fields from an existing class

```scala
case class BaseballTeam(name: String, lastWorldSeriesWin: Int)

val cubs1908 = BaseballTeam("Chicago Cubs", 1908)
// cubs1908: BaseballTeam = BaseballTeam(Chicago Cubs,1908)

val cubs2016 = cubs1908.copy(lastWorldSeriesWin = 2016)
// cubs2016: BaseballTeam = BaseballTeam(Chicago Cubs,2016)
```

## The `equals` and `hashCode` methods

```scala
case class Person(name: String, relation: String)

val christina = Person("Christina", "niece")
// christina: Person = Person(Christina,neice)

val hanna = Person("Hanna", "neice")
// hannah: Person = Person(Hannah,niece)

christina == hanna // false
```

## The `toString` methods

- Continuing on the previos

```
scala> christina
res0: Person = Person(Christina,niece)
```

## The biggest advantage

> ... "the biggest advantage of case classes si that they suport pattern matching." Pattern matching is a major feature of FP languages ...
