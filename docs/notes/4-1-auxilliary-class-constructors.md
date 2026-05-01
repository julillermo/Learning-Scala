# Auxilliary-class-constructors

Rules to know

- Each auxilliary constructor must have a different signature (different paremeter lists)
- Each constructor must call one of the previously defined constructors

```scala
val DefaultCrustSize = 12
val DefaultCrustType = "THIN"

class Pizza (var crustSize: Int, var crustType: String) {
  //one-arg auxiliary constructor
  def this(crustSize: Int) = {
    this(crustSize, DefaultCrustType)
  }

  // one-arg auxillary constructor
  def this(crustType: String) = {
    this(DefaultCrustSize, crustType)
  }

  // zero-arg auxiliary constructor
  def this() = {
    this(DefaultCrustSize, DefaultCrustType)
  }

  override def toString = s"A $crustSize inch pizza with a $crustType crust"
}

// different way to create Pizza
val p1 = new Pizza(DefaultCrustSize, DefaultCrustType)
val p2 = new Pizza(DefaultCrustSize)
val p3 = new Pizza(DefaultCrustType)
val p4 = new Pizza

// I think the above works because they're types are different
```

# Default parameters

- Because of this, you likely wouldn't reach for auxilliary constructors that often

```scala
class Pizza(
  var crustSize: Int = DefaultCrustSize
  var crustType: String = DefaultCrustType
)
```
