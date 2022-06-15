# Programming Languages
## Dimensions of Programming Languages
### Compiled v Interpreted 
### Statically v Dynamically Typed
### Object-Oriented
### Functional Programming
## Ruby
### Overview
* Interpretted, dynamically-typed, object-oriented language
* Pure object-oriented: everything is an object
### Type System
* Strongly-Typed: type of a variable is not automatically converted.
* Duck Typing: an object is compatible based on which operations it can support rather than its type or class. In the code below, if `obj`
  supports the operations `walk` and `quack`, then the code will run without errors regardless of type.
```
def is_duck(obj):
  obj.walk 
  obj.quack
  puts "Object is a duck"
```
* 
