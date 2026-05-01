# Supplying default values for constructor parameters

```scala
class Socket(var timeout: Int = 2000, var linger: Int = 3000) {
  override def toString = s"timeout: $timeout, linger: $linger"
}

new Socket()
new Socket(1000)
new Socket(4000,6000)
```

## Named parameters

```scala
class Socket(var timeout: Int, var linger: Int) {
  override def toString = s"timeout: $timeout, linger: $linger"
}

val s = new Socket(timeout=2000, linger=3000)
```
