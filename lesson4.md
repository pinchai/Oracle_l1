
# Oracle NULL Functions & Conditional Expressions – Lesson

## Learning Objectives
- Handle NULL values using NVL, NVL2, and NULLIF
- Apply conditional logic using CASE and DECODE

---

## 1. NVL
**Syntax**
```sql
NVL(expression, replacement_value)
```

**Example**
```sql
SELECT full_name,
       NVL(phone, 'No Phone') AS contact
FROM students;
```

---

## 2. NVL2
**Syntax**
```sql
NVL2(expression, value_if_not_null, value_if_null)
```

**Example**
```sql
SELECT full_name,
       NVL2(email, 'Has Email', 'No Email') AS email_status
FROM students;
```

---

## 3. NULLIF
- If two expressions are equal → return NULL
- If not equal → return first expression

```sql
SELECT
    NULLIF(100, 100) AS result1,
    NULLIF(100, 50) AS result2
FROM dual;
```

---

## 4. CASE
```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ELSE default_result
END
```

**Example**
```sql
SELECT full_name,
       CASE
           WHEN score >= 90 THEN 'A'
           WHEN score >= 80 THEN 'B'
           WHEN score >= 70 THEN 'C'
           WHEN score >= 60 THEN 'D'
           ELSE 'F'
       END AS grade
FROM students;
```

---

## 5. DECODE
```sql
DECODE(expression,
       search1, result1,
       search2, result2,
       default)
```

**Example**
```sql
SELECT full_name,
       DECODE(score,
              90, 'Excellent',
              80, 'Good',
              'Average') AS grade
FROM students;
```

---

## Practice

### EX1 – NVL
```sql
SELECT NVL(email, 'Unknown') FROM students;
```

### EX2 – NVL2
```sql
SELECT full_name,
       NVL2(phone, 'Available', 'Missing')
FROM students;
```

### EX3 – NULLIF
```sql
SELECT total / NULLIF(quantity, 0)
FROM orders;
```

### EX4 – CASE
```sql
SELECT full_name,
       CASE
           WHEN score >= 60 THEN 'Pass'
           ELSE 'Fail'
       END AS result
FROM students;
```

### EX5 – DECODE
```sql
SELECT full_name,
       DECODE(score,
              90, 'A',
              80, 'B',
              70, 'C',
              'F') AS grade
FROM students;
```
