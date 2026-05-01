# if/then/else construct

Some basic syntax for an if statement in scala

```scala
if (a == b) doSomething()

if (a == b) {
  doSomething()
}

if (a == b) {
  doSomething()
} else {
  doSomethingElse()
}

if (test1) {
  doX()
} else if (test2) {
  doY()
} else {
  doZ()
}
```

## `if` expressions always return a result

- You can ignore the result, but it's more common for a functional programming language like scala to always return a value
- For this reason, Scala uses its `if` statement as the ternary operator

```scala
val minValue = if (a < b) a else b
```

## Expression-oriented programming (EOP)

- The style of programming where everything returns a value.
  - `val minValue = if (a < b) a else b`
- Lines of code that don't return values are `expressions` (commonly used for their _side-effects_)
  - `if (a == b) doSomething()`
  - `println("Hello")`
