# **CSE 212 - Database Systems Lab Notes #1**

## **SELECT, FROM, DROP**

### **SELECT**

The `SELECT` statement is used to select data from a database. The data returned is stored in a result table, called the result set.

```sql
SELECT column1, column2, ...
FROM table_name;
```

### **FROM**

The `FROM` clause is used to specify the table from which you want to select data.

```sql
SELECT column1, column2, ...
FROM table_name;
```

### **DROP**

The `DROP` statement is used to delete a table from the database.

```sql
DROP TABLE table_name;
```

### **Example**

```sql
SELECT name, age
FROM students;

DROP TABLE students;
```

### **Output**

```sql
name | age
------------
John | 20
Jane | 21
```

### **Note**

- The `SELECT` statement is used to select data from a database.
- The `FROM` clause is used to specify the table from which you want to select data.
- The `DROP` statement is used to delete a table from the database.

---

## Conclusion

In this section, we learned about the `SELECT`, `FROM`, and `DROP` statements in SQL. We also saw an example of how to use these statements to select data from a table and delete a table from the database. In the next section, we will learn about the `WHERE` clause, which is used to filter records based on a condition.

---
