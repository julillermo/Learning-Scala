# Command-line I/O

## Writing Output

- Print to STDOUT via `println` (adds a `\n`) and `print()`
- Print to STDERR vai `System.err.println("yikes, an error happened")`

## Reading input

```scala
import scala.io.StdIn.readLine

object HelloInteractive extends App {

  print("Enter your first name: ")
  val firstName = readLine()

  print("Enter your last name: ")
  val lastName = readLine()

  println(s"Your name is $firstName $lastName")

}
```
