# Hello, World

```scala
object Hello {
    def main(args: Array[String]) = {
        println("Hello, world")
    }
}
```

- An `object` is similar to a `class`, but you specifically use it when you want a single isntance of that class

## Going Deeper: Scala Creates `.class` files.

- You can run `javap Hello` to verify that the JVM can load the generated files from Scala

## Alternative way to do Hello World in Scala

```scala
object Hello2 extends App {
  println("Hello, World")
}
```

- The `App` trait has its own `main` method.

## Two Types of Variables

- `val` for immutable (like JS `const`)
- `var` for mutable (like JS `let`)

Generall use val unless you really need mutability

```scala
val s = "hello"   // immutable
var i = 42        // mutable

val p = new Person("Joel Fleischman")
```

```scala
object Hello3 extends App {
  val hello = "Hello, world"
  println(hello)
}
```
