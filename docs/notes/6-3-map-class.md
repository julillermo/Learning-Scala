# The Map Class

> ... an iterable sequence that consists of pairs of keys and values.

- Can be both mutable and immutable. The _mutable_ variant is described here

```scala
val states = Map(
  "AK" -> "Alaska",
  "IL" -> "Illinois",
  "Ky" -> "Kentucky"
)
```

## Creating a mutable Map

```scala
import scala.collection.mutable.Map

val states = collection.mutable.Map("AK" -> "Alaska")

// Adding elements
states += ("AL" -> "Alabama")
states += ("AR" -> "Arkansas", "AZ" -> "Arizona")
states ++= Map("CA" -> "California", "CO" -> "Colorado")

// Removing elements
states -= "AR"
states -= ("AL", "AZ")
states --= List("AL", "AZ")

// Updating Map elements
states("AK") = "Alaska, A Really Big State"

// Traversing a Map
val ratings = Map(
  "Lady in the water" -> 3.0,
  "Snakes on a Plane" -> 4.0,
  "You, Me and Dupree" -> 3.5
)

for ((k,v) <- ratings) println(s"key: $k, value: $v")

ratings.foreach {
  case(movie, rating) => println(s"key: $movie, value: $string")
}
```
