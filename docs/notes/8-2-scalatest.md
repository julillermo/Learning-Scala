# Using ScalaTest with `sbt`

- One of the testing libraries for Scala projects.

## Creating the project directory structure

- expects the same directory structure discussed in (the sbt chapter)[[8-1-sbt]]

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

## Creating the `build.sbt` file

- Same as (the sbt chapter)[[8-1-sbt]], but include `libraryDependencies`. What this does is, _"... tell sbt to include the dependencies (jar files) that are needed to run ScalaTest"_

```
name := "HelloScalaTest"
version := "1.0"
scalaVersion := "2.13.18"

libraryDependencies +=
    "org.scalatest" %% "scalatest" % "3.2.19" % Test
```

## Create a Scala file

- Create a `Hello.scala` file in `mkdir src/main/scala/simpletest`

```scala
package simpletest

object Hello extends App {
    val p = new Person("Alvin Alexander")
    println(s"Hello ${p.name}")
}

class Person(var name: String)
```

## Your first ScalaTest tests

- _"... a simple way to get started is to write tests using the ScalaTest "FunSuite."_
- Create the equiavalent directory in the `src/test/` folder
  - `mkdir src/test/scala/simpletest`
- Create `HelloTests.scala` file there
- Notes on the test file below:
  - class should extend `AnyFunSuite`
  - similar to How tests are done in `Jest` or `Vitest`
  - supposedly similar to using `JUnit`

- Run using `sbt run`
  - I assume individually executing `sbt` and `run` also works

```scala
package simpletest

import org.scalatest.funsuite.AnyFunSuite

class HelloTests extends anyFunSuite {
  // test 1
  test("the name is set correctly in constructor") {
    val p = new Person("Barney Rubble")
    assert(p.name == "Barney Rubble")
  }
  // test 2
  test("a Person's name can be changed") {
    val p = new Person("Char Johnson")
    p.name = "Ochocinco"
    assert(p.name == "Ochocinco")
  }
}
```

- A Behavrior Driven Development philosophy was discussed after this chapter, but I skipped it
