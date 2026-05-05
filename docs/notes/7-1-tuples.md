# Tuples

- store _heterogenous (different)_ items in the same container.
- can contain between 2 to 22 items

```scala
class Person(var name: String)

// Instead of create an ad-hoc class to capture different types into 1 instance (like the following)
class SomeThings(i: Int, s: String, p: Person)

val t = (3, "Three", new Person("Al"))
```

```
scala> val d = ("Maggie", 30)
d: (String, Int) = (Maggie, 30)

scala> case class Person(name: String)
defined class Person

scala> val t = (3, "Three", new Person("David"))
t: (Int, java.lang.String, Person) = (3, Three, Person(David))
```

## Accessing tuples

```scala
t._1
t._2
t._3
```

## Returning a tuple from a method

```scala
def getStockInfo = {
  // ...
  ("NFLX", 100.00, 101.00) // this is a Tuple3
}

// Like JS decomposition?
val (symbol, currentPrice, bidPrice) = getStockInfo
```
