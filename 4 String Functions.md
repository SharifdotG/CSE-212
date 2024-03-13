## **CSE 212 - Database Systems Lab Notes #4**

## **String Functions**

### **What are the string functions in SQL?**

String functions are used to manipulate strings in SQL. Some of the most commonly used string functions are:

- `CONCAT()`: Concatenates two or more strings together.
- `LENGTH()`: Returns the length of a string.
- `LOWER()`: Converts a string to lowercase.
- `UPPER()`: Converts a string to uppercase.
- `SUBSTR()`: Extracts a substring from a string.
- `REPLACE()`: Replaces a substring within a string.
- `TRIM()`: Removes leading and trailing spaces from a string.

#### **CONCAT()**

The `CONCAT()` function is used to concatenate two or more strings together. It takes two or more arguments and returns a single string.

##### **Example**

```sql
SELECT CONCAT('Hello', ' ', 'World');
```

##### **Output**

```sql
Hello World
```

##### **Notes**

- The `CONCAT()` function is used to concatenate two or more strings together.
- It takes two or more arguments and returns a single string.
- The arguments can be strings, numbers, or other data types.
- The `CONCAT()` function can be used to concatenate columns from a table.
- The `CONCAT()` function can be used to concatenate literal values with column values.
- The `CONCAT()` function can be used to concatenate literal values with other literal values.
- The `CONCAT()` function can be used to concatenate the results of other functions.
- The `CONCAT()` function can be used to concatenate the results of subqueries.
- The `CONCAT()` function can be used to concatenate the results of other string functions.
- The `CONCAT()` function can be used to concatenate the results of other aggregate functions.

#### **LENGTH()**

The `LENGTH()` function is used to return the length of a string. It takes a string as an argument and returns an integer value. The length of a string is the number of characters in the string.

##### **Example**

```sql
SELECT LENGTH('Hello World');
```

##### **Output**

```sql
11
```

##### **Notes**

- The `LENGTH()` function is used to return the length of a string.
- It takes a string as an argument and returns an integer value.
- The length of a string is the number of characters in the string.
- The `LENGTH()` function can be used to find the length of a column value.
- The `LENGTH()` function can be used to find the length of a literal value.
- The `LENGTH()` function can be used to find the length of the result of another function.
- The `LENGTH()` function can be used to find the length of the result of a subquery.
- The `LENGTH()` function can be used to find the length of the result of another string function.
- The `LENGTH()` function can be used to find the length of the result of another aggregate function.

#### **LOWER()**

The `LOWER()` function is used to convert a string to lowercase. It takes a string as an argument and returns a new string with all characters converted to lowercase.

##### **Example**

```sql
SELECT LOWER('Hello World');
```

##### **Output**

```sql
hello world
```

##### **Notes**

- The `LOWER()` function is used to convert a string to lowercase.
- It takes a string as an argument and returns a new string with all characters converted to lowercase.
- The `LOWER()` function can be used to convert the value of a column to lowercase.
- The `LOWER()` function can be used to convert a literal value to lowercase.
- The `LOWER()` function can be used to convert the result of another function to lowercase.
- The `LOWER()` function can be used to convert the result of a subquery to lowercase.
- The `LOWER()` function can be used to convert the result of another string function to lowercase.
- The `LOWER()` function can be used to convert the result of another aggregate function to lowercase.

#### **UPPER()**

The `UPPER()` function is used to convert a string to uppercase. It takes a string as an argument and returns a new string with all characters converted to uppercase.

##### **Example**

```sql
SELECT UPPER('Hello World');
```

##### **Output**

```sql
HELLO WORLD
```

##### **Notes**

- The `UPPER()` function is used to convert a string to uppercase.
- It takes a string as an argument and returns a new string with all characters converted to uppercase.
- The `UPPER()` function can be used to convert the value of a column to uppercase.
- The `UPPER()` function can be used to convert a literal value to uppercase.
- The `UPPER()` function can be used to convert the result of another function to uppercase.
- The `UPPER()` function can be used to convert the result of a subquery to uppercase.
- The `UPPER()` function can be used to convert the result of another string function to uppercase.
- The `UPPER()` function can be used to convert the result of another aggregate function to uppercase.

#### **SUBSTR()**

The `SUBSTR()` function is used to extract a substring from a string. It takes three arguments: the string, the starting position, and the length of the substring. It returns a new string containing the specified substring.

##### **Example**

```sql
SELECT SUBSTR('Hello World', 1, 5);
```

##### **Output**

```sql
Hello
```

##### **Notes**

- The `SUBSTR()` function is used to extract a substring from a string.
- It takes three arguments: the string, the starting position, and the length of the substring.
- It returns a new string containing the specified substring.
- The `SUBSTR()` function can be used to extract a substring from the value of a column.
- The `SUBSTR()` function can be used to extract a substring from a literal value.
- The `SUBSTR()` function can be used to extract a substring from the result of another function.
- The `SUBSTR()` function can be used to extract a substring from the result of a subquery.
- The `SUBSTR()` function can be used to extract a substring from the result of another string function.
- The `SUBSTR()` function can be used to extract a substring from the result of another aggregate function.

#### **REPLACE()**

The `REPLACE()` function is used to replace a substring within a string. It takes three arguments: the string, the substring to replace, and the replacement substring. It returns a new string with all occurrences of the substring replaced with the replacement substring.

##### **Example**

```sql
SELECT REPLACE('Hello World', 'Hello', 'Hi');
```

##### **Output**

```sql
Hi World
```

##### **Notes**

- The `REPLACE()` function is used to replace a substring within a string.
- It takes three arguments: the string, the substring to replace, and the replacement substring.
- It returns a new string with all occurrences of the substring replaced with the replacement substring.
- The `REPLACE()` function can be used to replace a substring within the value of a column.
- The `REPLACE()` function can be used to replace a substring within a literal value.
- The `REPLACE()` function can be used to replace a substring within the result of another function.
- The `REPLACE()` function can be used to replace a substring within the result of a subquery.
- The `REPLACE()` function can be used to replace a substring within the result of another string function.
- The `REPLACE()` function can be used to replace a substring within the result of another aggregate function.

#### **TRIM()**

The `TRIM()` function is used to remove leading and trailing spaces from a string. It takes a string as an argument and returns a new string with leading and trailing spaces removed.

##### **Example**

```sql
SELECT TRIM('   Hello World   ');
```

##### **Output**

```sql
Hello World
```

##### **Notes**

- The `TRIM()` function is used to remove leading and trailing spaces from a string.
- It takes a string as an argument and returns a new string with leading and trailing spaces removed.
- The `TRIM()` function can be used to remove leading and trailing spaces from the value of a column.
- The `TRIM()` function can be used to remove leading and trailing spaces from a literal value.
- The `TRIM()` function can be used to remove leading and trailing spaces from the result of another function.
- The `TRIM()` function can be used to remove leading and trailing spaces from the result of a subquery.
- The `TRIM()` function can be used to remove leading and trailing spaces from the result of another string function.
- The `TRIM()` function can be used to remove leading and trailing spaces from the result of another aggregate function.

### **Conclusion**

In this section, we learned about the String Functions in MySQL. The `CONCAT()` function is used to concatenate two or more strings together. The `LENGTH()` function is used to return the length of a string. The `LOWER()` function is used to convert a string to lowercase. The `UPPER()` function is used to convert a string to uppercase. The `SUBSTR()` function is used to extract a substring from a string. The `REPLACE()` function is used to replace a substring within a string. The `TRIM()` function is used to remove leading and trailing spaces from a string.