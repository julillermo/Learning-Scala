# For Expressions

- The book will refer to the concept discussed here as `for-expressions` to disnguish then from for loops.
- Unlike for loops that get used for side-effects, `for-expressions` are used to _create new collectsions from existing collectoins_
- In [for loops](./3-2-for-loops.md), we used `for` and `foreach` with **side effects**

```scala
val nums = Seq(1,2,3)

val doubledNums = for (n <- nums) yield n * 2
// List(2,4,6)
```

```scala
val names = List("adam", "david", "frank")

val ucNames = for (name <- names) yield name.capitalize
// Adam, David, Frank
```

## The `yield` keyword

- "I want to yield a new collection from the existing collection that I'm iterating over in the for-expression, using the algorithm shown."

## Using a block of code after yield

```scala
val names = List("_adam", "_david", "_frank")

val capNames = for (name <- names) yield {
  val nameWithoutUnderscore = name.drop(1)
  val capName = nameWithoutUnderscore.capitalize
  capName // The last line is the returned expression, just like in Haskell.
}
```

A shorter version of the above would be the following:

```scala
val capNames = for (name <- names) yield name.drop(1).capitalize

// equivalently

val capNamesEquivalent = for (name <- names) yield { name.drop(1).capitalize}
```
