# Case Objects

- Like an `object`, but with added features:
  1. serializable
  2. with default `hashCode` implementation
  3. improved `toString` implementation
- `case objects` are often used in 2 places (intead of regular objects):
  1. creating **enumerations**
  2. creating **containers for for "messages"** you want to pass between other objects

## Creating enumerations with case objects

- As shown previously, enumerations are done similar to the following in Scala.

```scala
sealed trait Topping
case object Cheese extends Topping
case object Pepperoni extends Topping
case object Sausage extends Topping
case object Mushrooms extends Topping
case object Onions extends Topping

sealed trait CrustSize
case object SmallCrustSize extends CrustSize
case object MediumCrustSize extends CrustSize
case object LargeCrustSize extends CrustSize

sealed trait CrustType
case object RegularCrustType extends CrustType
case object ThinCrustType extends CrustType
case object ThickCrustType extends CrustType

case class Pizza {
  crustSize: CrustSize,
  crustType: CrustType
  toppings: Seq[Topping]
}
```

## Using case objects as messages

```scala
case class StartSpeakingMessage(textToSpeak: String)
case object StopSpeakingMessage
case object PauseSpeakingMessage
case object ResumeSpeakingMessage

class Speak extends Actor {
  def receive = {
    case StartSpeakingMessage(textToSpeak) =>
      // code to speak the text
    case StopSpeakingMesssage =>
    case PauseSpeakingMessage =>
    case ResumeSpeakingMessage =>
  }
}
```
