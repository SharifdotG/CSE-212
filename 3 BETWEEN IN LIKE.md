# **CSE 212 - Database Systems Lab Notes #3**

## **BETWEEN, IN, LIKE**

### **BETWEEN**

The `BETWEEN` operator selects values within a given range. The values can be numbers, text, or dates. The `BETWEEN` operator is used with the `AND` operator. The `AND` operator is used to combine two conditions in a `WHERE` clause. The `BETWEEN` operator selects values within a given range, while the `AND` operator combines two conditions in a `WHERE` clause.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

#### **Example**

```sql
SELECT name, age
FROM students
WHERE age BETWEEN 20 AND 21;
```

#### **Output**

```sql
name | age
------------
John | 20
Jane | 21
```

#### **Example**

```sql
SELECT name, age
FROM students
WHERE name BETWEEN 'A' AND 'J';
```

#### **Output**

```sql
name | age
------------
John | 20
```

#### **Notes**

- The `BETWEEN` operator selects values within a given range.
- The `AND` operator is used to combine two conditions in a `WHERE` clause.
- The `BETWEEN` operator is used with the `AND` operator.

### **IN**

The `IN` operator allows you to specify multiple values in a `WHERE` clause. It is used to reduce the use of multiple `OR` conditions in a `WHERE` clause. The `IN` operator is used with a list of values separated by commas. The list of values can be numbers, text, or dates.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

#### **Example**

```sql
SELECT name, age
FROM students
WHERE age IN (20, 21);
```

#### **Output**

```sql
name | age
------------
John | 20
Jane | 21
```

#### **Example**

```sql
SELECT name, age
FROM students
WHERE name IN ('John', 'Jane');
```

#### **Output**

```sql
name | age
------------
John | 20
Jane | 21
```

#### **Notes**

- The `IN` operator allows you to specify multiple values in a `WHERE` clause.
- The `IN` operator is used to reduce the use of multiple `OR` conditions in a `WHERE` clause.
- The `IN` operator is used with a list of values separated by commas.
- The list of values can be numbers, text, or dates.

### **LIKE**

The `LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column. The pattern can be a string or a combination of strings. The `LIKE` operator is used with the `%` and `_` wildcards. The `%` wildcard matches any string of any length, while the `_` wildcard matches any single character.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name LIKE pattern;
```

#### **Example**

```sql
SELECT name, age
FROM students
WHERE name LIKE 'J%';
```

#### **Output**

```sql
name | age
------------
John | 20
Jane | 21
```

#### **Example**

```sql
SELECT name, age
FROM students
WHERE name LIKE 'J_n_';
```

#### **Output**

```sql
name | age
------------
John | 20
```

#### Example

```sql
SELECT name, age
FROM students
WHERE name LIKE 'J%e';
```

#### Output

```sql
name | age
------------
Jane | 21
```

#### **Notes**

- The `LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column.
- The pattern can be a string or a combination of strings.
- The `LIKE` operator is used with the `%` and `_` wildcards.
- The `%` wildcard matches any string of any length, while the `_` wildcard matches any single character.
- The `LIKE` operator is used to search for a specified pattern in a column.

---

## **Conclusions**

In this section, we learned about the `BETWEEN`, `IN`, and `LIKE` operators. The `BETWEEN` operator selects values within a given range. The `IN` operator allows you to specify multiple values in a `WHERE` clause. The `LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column. In the next section, we will learn about the `String Functions` in MySQL.
