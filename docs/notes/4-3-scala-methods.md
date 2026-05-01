# A first look at Scala methods

> In Scala, _methods_ are defined inside classes (just like Java), but for testing purposes you can also create them in the REPL. This lesson will show examples of methods so you can see what the syntax looks like.

## Showing the return type

```scala
def double(a: Int): Int = a * 2
```

## Multiline methods

```scala
def addThenDouble(a: Int, b: Int): Int = {
  val sum = a + b
  val doubled = sum * 2
  doubled // return value
}
```
