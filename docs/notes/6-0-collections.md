# Scala Collections

> If you're coming to Scala from Java, the best thing you can do is forget about the Java collections classes and use the Scala collections classes as they're intended to be used.

## The main Scala collections classes

- `ArrayBuffer` - an indexed, mutable sequence
- `List` - a linear (linked list), immutable sequene
- `Vector` - an indexed, immutable sequence
- `Map` - the base `Map` (key/value pairs) class
- `Set` - the base `Set` class

> ... wehenver we use the word immutable, it's safe to assume that the class is intended for use in a functional Programming (FP) style. With these classes you don't modify the collection; you apply functional methods to the collection to create a new result.
