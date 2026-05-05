# ArrayBuffer Class

- A _mutable_ sequence

```scala
import scala.collection.mutable.ArrayBuffer

val ints = ArrayBuffer[Int]()
val names = ArrayBuffer[String]()

```

- adding elements to an `ArrayBuffer`

```scala
val ints = ArrayBuffer[Int]()
ints += 5 // (5)
ints += 10 // (5,10)
ints += 1 // (5,10,1)

ints += 5 += 6 // (5,10,1,5,6)

ints ++= List(7,8,9) // (5,10,1,5,6,7,8,9)

// removes the first 5 instance
ints -= 5 // (10,1,5,6,7,8,9)

// removes the first 9 instance
ints -= 9 // (10,1,5,6,7,8)

ints --= Array(5,6) // (10,1,7,8)
```

- Additional ways to work in `ArrayBuffer`

```scala
val a = ArrayBuffer(1,2,3)  // ArrayBuffer(1,2,3)
a.append(4)                 // ArrayBuffer(1,2,3,4)
a.appendAll(Seq(5,6))       // ArrayBuffer(1,2,3,4,5,6)
a.clear                     // ArrayBuffer()

val a = ArrayBuffer(9,10)       // ArrayBuffer(9,10)
a.insert(0,8)                   // ArrayBuffer(8,9,10)
a.insertAll(0, Vector(4,5,6,7)) // ArrayBuffer(4, 5, 6, 7, 8, 9, 10)
a.prepend(3)                    // ArrayBuffer(3, 4, 5, 6, 7, 8, 9, 10)
a.prependAll(Array(0,1,2))      // ArrayBuffer(0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

val a ArrayBuffer.range('a', 'h') // ArrayBuffer(a, b, c, d, e, f, g)
a.remove(0)                       // ArrayBuffer(b, c, d, e, f, g)
a.remove(2,3)                     // ArrayBuffer(b, c, g)

val a = ArrayBuffer.range('a', 'h') // ArrayBuffer(a, b, c, d, e, f, g)
a.dropInPlace(2)                    // ArrayBuffer(c, d, e, f, g)
a.dropInPlace(2)                    // ArrayBuffer(c, d, e)
```
