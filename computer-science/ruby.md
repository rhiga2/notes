# Ruby
## Overview
* Interpretted, dynamically-typed, object-oriented language
* Pure object-oriented: everything is an object even classes and functions
* Strongly-Typed: type of a variable is not automatically converted.
* Duck Typing: an object is compatible based on which operations it can support rather than its type or class. In the code below, if `obj`
  supports the operations `walk` and `quack`, then the code will run without errors regardless of type.
```
def is_duck(obj):
  obj.walk 
  obj.quack
  puts "Object is a duck"
```
## Functions and Code Blocks
* Always have return types equal to the last expression in the function
```
def increment(i) 
  i + 1 
end
```
* Code Blocks: Functions without names
```
# single line convention
{|i| i+1}

# multi-line convention
do |i|
  i + 1
end
```
## Classes
* Classes can only inherit from one superclass
* Mixins: add additional functionality to classes without inheritance. We determine if a class can extend a mixin using duck typing. 
  For instance, a class can extend `enumerable` if it implements `each` and can extend `comparable` if it implements `<=>`.
* Modules: define mixins
## Type System 
## Metaprogramming
* Metaprogramming: Programs that generate programs
* Open Classes: Freedom to modify any existing class
* `method_missing`: debugging method that is called whenever you call a method on a class or object that does not support the method. This method can be overrided.
