# Common Sequence Methods

- Benefit of having built-in approaches to common for loops you'd have to reimplement yourself (or interpret someone else's implementation)
- List of most commonly used methods
  - `map`
  - `filter`
  - `foreach`
  - `head`
  - `tail`
  - `take`, `takeWhile`
  - `drop`, `dropWhile`
  - `reduce`

## Methods don't mutate the collection

- They return a new collection with where the fuction has been applied elements.

- Selected methods (didn't incude all, since generally the same idea as in JavaScript)
  - `head`
    - return the firt element
  - `tail`
    - return everything but the first element
  - `take`
    - I believe this copies up to the n-th element from a list
    - `nums.take(6)` -> copie the first 6 elements
  - `takeWhile`
    - The takeWhile copies based on a condition
    - `nums.takeWhile(_ < 5)` -> copies everything less thatn 5
  - `drop`
    - opposite of `take`
  - `dropWhile`
    - opposite of `takeWhile`
