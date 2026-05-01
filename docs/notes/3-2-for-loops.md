# For loops

Some common syntax examples

```scala
val nums = Seq(1,2,3)

for (n <- nums) println(n)

val people = List(
  "Bill",
  "Candy",
  "Karen",
  "Leo",
  "Regina"
)

for (p <- people) println(p)
```

## The `foreach` method

- `people.foreach(println)`

## Using Maps

- Note that "Maps" here is referring to hashmaps
  - Equivalent to Java `HashMap`
  - Like a 1-tier Python Dictionary or 1-tier JS object (more like a key-value pair)

```scala
val ratings = Map(
  "Lady in the Water" -> 3.0,
  "Snakes on a Plane" -> 4.0,
  "You, Me and Dupgree" -> 3.5,
)

for ((name, rating) <- ratings) println(s"Movie: $name, Rating: $rating")

ratings.foreach {
  case(movie, rating) => println(s"key: $movie, value: $string")
}
```
