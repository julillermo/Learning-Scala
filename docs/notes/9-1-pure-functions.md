# Pure Functions

- How to define a pure function
  - Output depends only on it's input variables
  - Doesn't mutate (or alter) any hidden or outside state
  - Doesn't read or write data to the outside world.

## Examples of pure functions

- Common math functions are understandably pure functions
  - `abs`
  - `ciel`
  - `max`
  - `min`
  - Scala `String` methods
    - `isEmpty`
    - `length`
    - `substring`
  - Scala collection class methods
    - `drop`
    - `filter`
    - `map`

## Examples of impure functions

- The `foreach` method is impure since it's use is intended to alter values or communicate outside of the scope

> A great hint that `foreach` is impure is that its method signature declares that it returns the type `Unit`. Because it returns nothing, logically the only reason you ever call it is to achieve some side effect. Similarly, any method that returns `Unit` is going to be an impure function

- Other examples of impure functions
  - `getDayofWeek`, `getHour`, and `getMinute` are impure because they rely on information besides their function arguments.

## But impure functions are needed ...

- _"... people make this recommendation:"_
  > Write the core of your application using pure functions, and then write an impure "wrapper" around that core to interact with the outside world. ...
- Techiques exist to interact with the outside world in a "more pure" way. (ex. `IO` Monad)

## Writing pure functions

```scala
def double(i: Int): Int = i * 2

def sum(list: List[Int]): Int = list match {
  case Nil => 0
  case head :: tail => head + sum(tail)
}
```
