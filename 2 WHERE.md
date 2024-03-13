# **CSE 212 - Database Systems Lab Notes #2**

## **WHERE**

The `WHERE` clause is used to filter records. The `WHERE` clause is used to extract only those records that fulfill a specified condition. The `WHERE` clause is used to filter records based on a condition.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

### **Example**

```sql
SELECT name, age
FROM students
WHERE age > 20;
```

### **Output**

```sql
name | age
------------
Jane | 21
```

### **Example**

```sql
SELECT name, age
FROM students
WHERE name = 'John';
```

### **Output**

```sql
name | age
------------
John | 20
```

### **Example**

```sql
SELECT name, age
FROM students
WHERE name = 'John' AND age = 20;
```

### **Output**

```sql
name | age
------------
John | 20
```

### **Note**

- The `WHERE` clause is used to filter records.
- The `WHERE` clause is used to extract only those records that fulfill a specified condition.
- The `WHERE` clause is used to filter records based on a condition.

---

## Conclusion

In this section, we learned about the `WHERE` clause in SQL. We also saw examples of how to use the `WHERE` clause to filter records based on a condition. In the next section, we will learn about the `BETWEEN`, `IN`, and `LIKE` operators in SQL.

---
