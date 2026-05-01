# try/catch/finally expressions

```scala
var text = ""
try {
  text = openAndReadAFile(filename)
} catch {
  case e: FineNotFoundException => println("Couldn't find that file")
  case e: IOException => println("Had an IOExepction trying to read that file"       )
}
```

- Same syntax as the match statement / expression in scala

## Try, catch, and finally

```scala
try {
  // try code here
} catch {
  case foo: fooException => handleFoodException(foo)
  case bar: BarException => handleBarException(bar)
  case _: Throwable => println("Got some other kind of Throwable exception")
} finally {
  // finally code such as closing database connection or handling files
}
```
