# The most used Scala Build Tool (SBT)

- sbt is the first built tool for scala
- Technically, you can also build your project with tools like Ant, Maven, Gradle, etc.

## The `sbt` directory structure

```
build.sbt
project/
src/
-- main/
    |-- java/
    |-- resources/
    |-- scala/
|-- test/
    |-- java/
    |-- resources/
    |-- scala/
target/
```

- You can supposedly use the `sbt new` command to initialize a project (+contains more that what's discussed in this introduction).

## Creating a first `build.sbt` file

```sbt
// build.sbt
name := "HelloWorld"
version := "1.0"
scalaVersion := "2.13.18"
```

## A "Hello, world" program

- Typically, you should include your scala files within `./main/scala/` and `./test/scala/`, but for demonstration, place `HelloWorld.scala` at the root

```scala
// HelloWorld.scala
object HelloWorld extends App {
  println("Hello, world")
}
```

- Run the `sbt run` command to compile and run your project.
- Alternatively, you can also run `sbt` separately and then execute `run` once inside the sbt environment
