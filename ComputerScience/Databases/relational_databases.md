# Relational Databases 

## Relational Algebra 
* Algebras consist of operands and operators. 
* In arthimetic, the operands are numbers and the operators are addition, subtraction, multiplication, and division.
* In relational algebra, the operands are relations and the operators are selection, projection, union, set difference, cartesian product, and renaming.
* The input and output of a relational algebra operation is a relation.
* We can think of a relation as a set of tuples that have the same attributes (or schema). Relations are also called tables. 

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
* Natural Join: Set of all concatenated tuples that have the same values on the attributes that are common to both relations. A natural join is denoted as $R \bowtie S$.

## Structured Query Language (SQL)
### SELECT-FROM-WHERE
* SQL is a declarative language that allows users to query, insert, update, and delete data in a relational database.
* The basic query format uses the `SELECT-FROM-WHERE` clause:
``` sql
SELECT <attributes>
FROM <relation>
WHERE <condition>
```
* `SELECT` acts like a projection, `FROM` acts like a cartesian product (if more than one table is specified), and `WHERE` acts like a selection.
### Aggregation
#### Aggregation Functions
* SQL supports aggregation functions like  `COUNT, SUM, AVG, MIN`, and `MAX`. This query returns the number of faculty in the Computer Science department.
``` sql
SELECT COUNT(*)
FROM faculty
WHERE department = 'Computer Science'
```

#### GROUP BY
* We can use the `GROUP BY` clause to group the results of an aggregation function by a set of attributes. 
* `SELECT` must have attributes must be group attributes (attrs used in `GROUP BY`) or aggregation functions.
    ``` sql
    SELECT department, AVG(salary)
    FROM faculty
    GROUP BY department
    ```
    This query returns the average salary of faculty in each department.
* `HAVING` filters groups based on a condition.
    ``` sql
    SELECT department, AVG(salary)
    FROM faculty
    GROUP BY department
    HAVING AVG(salary) > 100000
    ```
    This query returns the average salary of faculty in each department that is greater than $100,000.

### JOINs

### Subqueries
* Subqueries are queries that are nested within another query.
* We can use subqueries in the SELECT, FROM, and WHERE clauses.
* Subqueries can be used whenever a relation can be specified.

#### Scalar Subqueries
* Scalar subqueries return a single value.
* We can use scalar subqueries in the SELECT and WHERE clauses. For example, the following query returns faculty whose salary is greater than the average faculty salary.
``` sql
SELECT name 
FROM faculty
WHERE salary > (SELECT AVG(salary) FROM faculty)
```

#### Table Subqueries
* Table subqueries return a table.
* We can use table subqueries in the FROM and WHERE clauses.
* Comparison operator with subqueries: `IN, EXISTS, ALL, ANY`

## Managing Tables with SQL
### Creating Tables
* We can create tables with the `CREATE TABLE` statement.
``` sql
CREATE TABLE faculty (
    name VARCHAR(50) primary key,
    department VARCHAR(50),
    salary INT
);
```

### Drop Table
* We can drop tables with the `DROP TABLE` statement.
``` sql
DROP TABLE faculty;
```

### Inserting, Updating, and Deleting Tuples
