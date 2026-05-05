# Common map methods

## Mutable Map examples

```scala
val m = Map(
  1 -> "a",
  2 -> "b",
  3 -> "c",
  4 -> "d"
)

val keys = m.keys
val values = m.values
val contains3 = m.contains(3)
val ucMap = m.transform((k,v) => v.toUpperCase)
val twoAndThree = m.view.filterKeys(Set(2,3)).toMap // Map (2 -> b, 3 -> c)
val firstTwoElements = m.take(2) // Map(1 -> a, 2 -> b)
```

##
