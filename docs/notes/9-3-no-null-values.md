# No Null Values

- There is no _null_ values in algebra. Because functional programming is a lot like writing out math equations, there is also no _null_ values in functional programming.
  - Instead use constructes like **Option/Some/None** classes.

## Using Option/Some/None

```scala
def toInt(s: String): Int = {
  try {
    Integer.parseInt(s.trim)
  } catch {
    case e: Exepction => 0
  }
}
```

- The above conversion from string to int function has issues:
  - If a user passes a string "hello", it returns 0 int
  - However, there's no way to distinguish whether a user passed "0" or a random word string.

```scala
def toInt(s: String): Option[Int] = {
  try {
    Some(Integer.parseInt(s.trim))
  } catch {
    case e: Exception => None
  }
}
```

- Explanation of the above improvement:
  - "When an string converts to an integer wrap it as `Some(<integer_here>)`"
  - "Otherwise, return `None`

- Using the above `toInt()` function results in the following:

```
scala> val a = toInt("1")
a: Option[Int] = Some(1)

scala> val a = toInt("foo")
a: Option[Int] = None
```

## Being a consumer of toInt

- So, if they're wrapped with either `Some()`, `Option()`, or `None`, how do we make use of them? You do either of the following:
  - use `match` expression
  - use a for-expression

```scala
// using `match`
toInt(x) match {
  case Some(i) => println(i)
  case None => println("That didn't work.")
}

// diff example wher intend to add them together
val stringA = "1"
val stringB = "2"
val stringC = "3"

// using for-yield
val y = for {
  a <- toInt(stringA)
  b <- toInt(stringB)
  c <- toInt(stringC)
} yield a + b + c
// return Some(6) if all inputs are convertible
// return None if 1 invalid input
```

## Think of `Option` class as container for 0 or 1 items inside

- The `Option` class is the larger type that is represented as either `Some` or `None`
  - `Some` is a container with one item in it
  - `None` is a container, but it has nothing in it

## Using `foreach`

- You can then also think of `Some` and `None` as collection classes that we can use `map`, `filter`, `foreach` methods on.

```scala
toInt("1").foreach(println) // prints 1 since Some(1).foreach(println) is valid
toInt("x").foreach(println) // doesn't print anything since None is just an empty container
```

- You'll need to specify again `Some` vs `None` when deciding to handle the result

```scala
toInt(x) match {
  case Some(i) => println(i)
  case None => println("That didn't work.")
}
```

## Using `Option` to replace null values

```scala
class Address (
  var street1: String,
  var street2: String, // This isn't available globally
  var city: String,
  var state: String,
  var zip: String
)

// To improve the above

class Address2 (
    var street1: String,
    var street2: Option[String], // specify it's optoinal
    var city: String,
    var state: String,
    var zip: String
)

// Therefore, the following are valid:
val santa = new Address(
  "1 Main Street",
  None,
  "North Pole",
  "Alaska",
  "99705"
)
val santa2 = new Address(
  "123 Main Street",
  Some("Apt. 2B"),
  "Talkeetna",
  "Alaska",
  "99676"
)
```

## Other solutions

- Scala also has `Try/Success/Failure` pattern (mainly for throwing exceptions/failures like interacting with API)
