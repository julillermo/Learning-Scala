# The Vector Class

- indexed, immutable sequence.
  - Indexed -> meaning that elements can rapidly be accessed by their index value (e.g. `listOfPeople(999999)`)
- Besides being indexed, `Vector` and `List` classes work the same.
- Differences between `Vector` and `List` according to AI chat:
  - `Vector`
    - More memory overhead
    - Not as cheap to attach, prepend, append elements to
    - tree/trie-based index sequence
  - `List`
    - Verify cheap to prepend with `::`
    - Slow random access
    - Cheap `head`/`tail`

```scala
val nums = Vector(1,2,3,4,5)
val strings = Vector("one", "two")
val peeps = Vector(
  Person("Bert"),
  Person("Ernie"),
  Person("Grover")
)
```

```scala
val a = Vector(1,2,3)

val b = a :+ 4
val b2 = a ++ Vector(4,5)

val b3 = 0 +: a
val b4 = Vector(-1,0) ++: a
```

```scala
val names: Vector[String] = Vector("Joel", "Chris", "Ed")

for (name <- names) println(name)
```
