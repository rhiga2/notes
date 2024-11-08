# Fluent Python
## Chapter 1: Python Data Model
### Special (Dunder) Methods
* Defining special methods allows language framework to call your code.
  * i.e. slicing and indexing with `[]` call `__getitem__`
* Avoid calling special methods directly!

## Chapter 2: An Array of Sequences
### Container API
* Indexing
* Len
* Contains
### Overview of Built-In Sequences
* Classifications
  * Container v flat sequence
  * Mutable v immutable sequences
* Lists: mutable container sequence
* Tuples: immutable container sequence, records / structs
### List Comprehensions and Generator Expressions
* Listcomps
  * They can do the same thing as map-filter   
* Genexps
### Tuple Unpacking
```python
x, y = (0, 1) # tuple unpacking
```
### Pattern Matching with Sequences
* Match, Subject, Case
* Runtime type checks (see future pattern matching class instances)
* Destructuring v unpacking (what's the difference)
### Pattern Matchin Sequences in Interpreter (Skipped)
### Slicing
* `s[start:end:stride]`
  * `start` inclusive
  * `end` exclusive
  * `stride` (can be negative for reversing)

## Miscellaneous
* Dummy variable `_`
