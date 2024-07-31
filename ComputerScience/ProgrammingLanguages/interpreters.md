# Interpreters 
* Interpreters are programs that read and execute code. They are used to run code written in high-level programming languages.
* Interpreters are different from compilers in that they execute code directly, without generating an intermediate machine code or executable file.

## Components of an Interpreter
* Main components of an interpreter: 
    * Parser: takes in text and outputs an abstract syntax tree (AST).
    * Environment: data structure to keep track of vars and vals.  
    * Evaluator: takes in an AST and executes it.
    * Top-level function (i.e. REPL)

## Evaluator 
* The evaluator takes in an AST and executes it given the current environment.
* Here are the types that the evaluator will work with:
    * Values: e.g. `1`, `True`
    * Expressions: e.g. `1 + 2`
* Example of interpreters that supports integers and functions (no bools etc...)
### Values and Expressions
* Definition of values (we will go over closures later)
```haskell
data Val = IntVal Integer
         | Closure [String] Exp Env
         | ExnVal String -- exception value
   deriving(Show, Eq)
```
* Definition of expressions: 
```haskell
data Exp = IntExp Integer -- integer literal
         | IntOpExp String Exp Exp -- expr with arithmetic operation
         | VarExp String -- variable reference
         | LetExp String Exp Exp -- let expression
         | FunExp [String] Exp -- function definition
         | AppExp Exp [Exp] -- function application
   deriving(Show,Eq)
``` 
* The evaluation function takes in an expression and an environment and returns a value.
```haskell
eval :: Exp -> Env -> Val
```

### Evaluation of Literals and Operations
* Evaluation of literals is straightforward. We just return the corresponding value.
```haskell
eval (IntExp n) env = IntVal n
``` 
* To evaluate operations, we need to lift operation in Haskell to our interpreter. To do the we need a map with op name -> Haskell op 
```haskell
intOps = [("+",(+)), ("-", (-)), ("*", (*)), ("/", (div))]

liftIntOp :: (Integer -> Integer -> Integer) -> Val -> Val -> Val
liftIntOp f (IntVal i1) (IntVal i2) = IntVal (f i1 i2)
liftIntOp _ _ _ = ExnVal "type error"
```
* Evaluate operation
```haskell
eval (IntOpExp op e1 e2) = let
    v1 = eval e1 env
    v2 = eval e2 env
    in case (lookup op intOps) of
        Just f -> liftIntOp f v1 v2
        Nothing -> ExnVal "unknown operator"

```

### Evaluation of Variables Reference and Let Expressions
* To evaluate a variable reference, we look up the variable in the environment.
```haskell
eval (VarExp x) env = case (lookup x env) of
    Just v -> v
    Nothing -> ExnVal ("unbound variable")
```
* To evaluate let expressions, we evaluate the first expression and add the variable to the environment before evaluating the second
```haskell
eval (LetExp x e1 e2) = let
    v1 = eval e1 env
    in eval e2 (insert x v1 env)
```

### Closures and Evaluation of Functions and Function Application
* In the function defintion, somes function can refer to external variables that may not be defined during application time. 
* Closure capture the environment at the time of function definition. A function definition evaluates to a closure. 
```haskell
eval (FunExp args e) env = Closure args e env
```
* To evaluate function application, we evaluate the function def, the arguments, and then evaluate the body with arg mappings and closure environment.
```haskell
eval (AppExp fexp args) env = let 
    Closure argnames body clenv = eval fexp env
    argvals = map (\arg -> eval arg env) args
    argmapping = zip argnames argvals
    newenv = foldr (\(name, val) temp -> insert name val temp) clenv argmapping
    in eval body newenv
```