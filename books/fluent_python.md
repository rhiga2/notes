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
  * Homogenous v non-homogenous sequences
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
### Pattern Matching Sequences in Interpreter (Skipped)
### Slicing
* `s[start:end:stride]`
  * `start` inclusive
  * `end` exclusive
  * `stride` (can be negative for reversing)
* Multi-dimensional slicing
### + and * Operators
* Does not modify operands
* Inplace versions: += and *=
 * In-place in mutable, reassigns if immutable
 * If `__iadd__` not implemented, defaults to + and assignment but this may not occur in-place.
 * Strange behavior of in-place update putting a mutable object in an immutable object.
  * Performs concate on the mutable list
  * Errors when it tries to assign the value back to an immutable tuple.
* Inplace expressions should return None!
### Alternative to Lists
* Arrays: mutable, flat sequence. Contains only numbers
* Memory views (Skipped)
* Numpy Ndarrays
  * Scipy, pandas, scikit-learn
* Double ended queues (deques)
* Heap (priority) queue

# Chapter 3: Dictionaries and Sets
* Hash tables underlie dicts, sets, and frozensets 

## Miscellaneous
* Dummy variable `_`
