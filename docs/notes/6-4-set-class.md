# The Set Class

- Can be both mutable and immutable. The _mutable_ variant is described here

```scala
import scala.collection.mutable.Set

val set = Set[Int]()

set += 1 // Set(1)
set += 2 += 3 // Set(1,2,3)
set ++= Vector(4,5) // Set(1,2,3,4,5)

// You can only add unique values to a set
set += 2 // Set (1,2,3,4,5)
```

- Use `.add` method to include and return a boolean if successful

```scala
// continuing from above
set.add(6) // returns true
set.add(5) // returns false (already existing)
```

## Deleting elements from a Set

```scala
import scala.collection.mutable.Set

val set = Set[Int](1,2,3,4,5)

set -= 1 // Set(2,3,4,5)
set -= (2,3) // Set (4,5)
set --= Array(4,5) // Set()

// Using clear() and remove() methods
```

- Using `.clear()` and `.remove()` methods

```scala
import scala.collection.mutable.Set

var set = Set[Int](1,2,3,4,5)
set.clear() // Set()

set = Set[Int](1,2,3,4,5)
set.remove(2) // returns true -> set mutated to (1,3,4,5)
set.remove(2) // returns false -> failed to remove
```
