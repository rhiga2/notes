# Relational Databases 

## Relational Algebra 
* Algebras consist of operands and operators. 
* In arthimetic, the operands are numbers and the operators are addition, subtraction, multiplication, and division.
* In relational algebra, the operands are relations and the operators are selection, projection, union, set difference, cartesian product, and renaming.
* The input and output of a relational algebra operation is a relation.
* We can think of a relation as a set of tuples that have the same attributes (or schema). 

### Base Operators
* Selection: Set of all tuples that satisfy a condition. 
    ``` math
    ```
* Projection: Set of all tuples with only the specified attributes. We remove duplicate tuples in a projection.
* Union: Set of all tuples in either relation
* Set Difference: Set of tuples in the first relation that are not in the second relation.
* Cartesian Product: Set of all tuples that are the concatenation of a tuple in the first relation and a tuple in the second relation.
* Rename: Set of all tuples with the same attributes but different names.

### Derived Operators
* Intersection: Set of all tuples that are in both relations. We can express an intersection with the set difference operator:
    ``` math 
    R \cap S = R - (R - S)
    ```
* Theta Join: Set of all concatenated tuples that satisfy a condition. We can express a theta join with the cartesian product and selection operators:
    ``` math
    R \bowtie_{\theta} S = \sigma_{\theta}(R \times S)
    ```
* Natural Join: Set of all concatenated tuples that have the same values on the attributes that are common to both relations. We can express a natural join with the theta join operator. 