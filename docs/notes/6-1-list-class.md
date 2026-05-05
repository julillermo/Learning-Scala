# The List Class

- Linear, immutable sequence.
- Cannot be modified; you must create a new `List` from an existing `List` if you want different values

## Creating Lists

```scala
val ints = List(1,2,3)
val names = List("Joel", "Chris", "Ed")

val intsTyped: List[Int] = List(1,2,3)
val namesTyped: List[String] = List("Joel", "Chris", "Ed")
```

## Adding elements to a List

```scala
val a = List(1,2,3)

val b = 0 +: a // (0,1,2,3)
val b2 = List(-1,0) ++:a

val c = a :+ 4 // (1,2,3,5)
```

> Tip: If you want to prepend and append elements to an immutable sequence, use `Vector` instead.

> Because `List` is a linked-list class, you shouldn't try to access the elements of large lists by their index value. For instance, if you ahve a `List` with one million elements in it, accessing an element like `myList(999999)` will take a long time. If you want to access elements like this, use a `Vector` or `ArrayBuffer` instead.

## How to loop over lists

```scala
val names = List("Joel", "Chris", "Ed")

for (name <- names) println(name)
```
