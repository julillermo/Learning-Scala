# Match expressions

- Same concept as with Java's switch statement

```scala
// This is a match statement
// i is an integer
i match {
  case 1 => println("January")
  case 2 => println("February")
  case 3 => println("March")
  case 4 => println("April")
  case 5 => println("May")
  case 6 => println("June")
  case 7 => println("July")
  case 8 => println("August")
  case 9 => println("September")
  case 10 => println("October")
  case 11 => println("November")
  case 12 => println("December")
  case _ => println("Invalid month")
}

// This is a match expression
// i is an integer
val monthName = i match {
  case 1 => "January"
  case 2 => "February"
  case 3 => "March"
  case 4 => "April"
  case 5 => "May"
  case 6 => "June"
  case 7 => "July"
  case 8 => "August"
  case 9 => "September"
  case 10 => "October"
  case 11 => "November"
  case 12 => "December"
  case _ => "Invalid month"
}
```

## Using `match` expression as the body of a method

```scala
def convertBooleanToStringMessage(bool: Boolean): String = bool match {
  case true => "you said true"
  case false => "you said false"
}
```

## Handling alternate cases

```scala
def isTrue(a: Any) = a match {
  case 0 | "" => false
  case _ => true
}

def isOddOrEven = i match {
  case 1 | 3 | 5 | 7 | 9 => println("odd")
  case 2 | 4 | 6 | 8 | 10 => println("even")
  case _ => println("some other number")
}

cmd match {
  case "start" | "go" => println("starting")
  case "stop" | "quit" | "exit" => println("stopping")
  case _ => println("doing nothing")
}
```

- The main thing I'm getting from this is you can add operators within a single case.

```scala
count match {
  case 1 => println("one, a lonely number")
  case x if (x == 2 || x == 3) => println("two's company, three's a crowd")
  case x if (x > 3) => println("4+, that's a party")
  case _ => println("I'm guessing your number is zero or less")
}
```

- You can also include condition statements as a check for each case
- The parenthesis for the conditions are optional

```scala
count match {
  case 1 =>
    println("one, a lonely number")
  case x if (x == 2 || x == 3) =>
    println("two's company, three's a crowd")
  case x if (x > 3) =>
    println("4+, that's a party")
  case _ =>
    println("I'm guessing your number is zero or less")
}
```

- You can write the the statement or expression in the succeeding lines

```scala
count match {
  case 1 => {
    println("one, a lonely number")
  }
  case x if (x == 2 || x == 3) => {
    println("two's company, three's a crowd")
  }
  case x if (x > 3) => {
    println("4+, that's a party")
  }
  case _ => {
    println("I'm guessing your number is zero or less")
  }
}
```

- You can also use curly braces

## Additional examples

```scala
i match {
  case a if 0 to 9 contains a => println("0-9 range: " + a)
  case b if 10 to 19 contains b => println("10-19 range: " + b)
  case c if 20 to 29 contains c => println("20-29 range: " + c)
  case _ => println("Hmmm...")
}

stock match {
  case x if (x.symbol === "XYZ" && x.price < 20) => buy(x)
  case x if (x.symbol === "XYZ" && x.price > 50) => sell(x)
  case x => doNothing(x)
}
```
