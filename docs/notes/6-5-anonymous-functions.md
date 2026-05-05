# Anonymous Functions

- A concept that primarily stems from functional programming

## Examples

```scala
val ints = List(1,2,3)
val doubleInts = ints.map(_ * 2) // List(2,4,6)

val doubleIntsEquivalent1 = ints.map((i: Int) => i * 2)
val doubleIntsEquivalent2 = ints.map(i => i * 2)

val doubleIntsForLoop = for (i <- ints) yield i * 2
```

## Anonymous functoins with `filter` method

```scala
val ints = List.range(1,10)
val x = ints.filter(_ > 5)
val y = ints.filter(_ < 5)
val z = ints.filter(_ %  2 == 0)
```

## Key points

- _FWIU: It's generally the same as with JavaScript concept for .forEach() .map() .filter(). The longer syntax is even equivalent to JavaScript's anonymous function_

## Digging a little deeper

- You can first assign the anonymous function. _Again, also similar to JavaScript_

```scala
val ints = List(1,2,3)

def double(i: Int): Int = i * 2
val doubledInts = ints.map(double)

def lessThanFive(i: Int): Boolean = if (i < 5) true else false
def lessThanFiveShort(i: Int): Boolean = (i < 5)

val ints2 = List.range(1,10)
val y = ints.filter(lessThanFive)
```
