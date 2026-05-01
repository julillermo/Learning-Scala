# Types

## The Type is Optional

- Like TypeScript, you aren't required to annotate with types
- Like TypeScript, you can also help the type checker by being explict with what type something is. Helpful to avoid the compiler making the wrong assumption on types.

## Built-in Types

```scala
val b: Byte = 1
val x: Int = 1
val l: Loong = 1
val s: Short = 1
val d: Double = 2.0
val f: Float = 3.0

var bInt = BigInt(1234567890)
var bDecimal = BigDecimal(123456.789)

val name: String = "Bill"
val c: Char = 'a'
```

- If assigning a whole number, will generally default to `Int` type
- If assigning a number with a decimal place, will generally default to a Double
  - You'd need to explictly set Float if you want to use Float
- Note that Scala inherits how it handles `String` and `Char` from Java.
  - The `String` is not a list of `Char`, unlike in languages like JavaScript and Python
  - You need the `.charAt(i)`, `.toCharArray`, `toList` methods to get the element of the string.

## Notes about strings

### Appending strings

```scala
val firstName = "John"
val mi = 'C' // char
val lastName = "Doe"

val name = firstName + " " + mi + " " + lastName

// string interpolation
val name = s"$firstName $mi $lastName"

println(s"Name: $firstName $mi $lastName")
println(s"1+1 = ${1+1}")
```

- preceeding with `f` allows to use of `printf()` style printing

### Multiline strings

```scala
val speech = """Four score and
              seven years ago
              our fathers ..."""

// Below makes sure to the outputted text to the left
val speech2 = """Four score and
              |seven years ago
              |our fathers ...""".stripMargin
```
