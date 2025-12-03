## Learning Objectives
Students will be able to:
- Convert **dates to text** using `TO_CHAR`
- Convert **text to dates** using `TO_DATE`
- Convert **text to numbers** using `TO_NUMBER`
- Apply formatting models correctly

---

## 1. TO_CHAR

### Purpose
Converts **DATE or NUMBER → VARCHAR2 (text)**

### Syntax
```sql
TO_CHAR(value, format)
```

---

### Example – Date to Text
```sql
SELECT TO_CHAR(SYSDATE, 'YYYY-MM-DD') AS today
FROM dual;
```

### Example – Number to Text
```sql
SELECT TO_CHAR(12345.67, '99,999.99') AS formatted_number
FROM dual;
```

---

### Common Format Models

#### Date Formats
| Format | Meaning |
|--------|----------|
| YYYY | 4-digit year |
| MM | Month number |
| DD | Day |
| MON | Month name |
| DY | Day name |

#### Number Formats
| Format | Meaning |
|--------|----------|
| 9 | Digit |
| 0 | Mandatory digit |
| , | Thousands separator |
| . | Decimal point |

---

## 2. TO_DATE

### Purpose
Converts **VARCHAR2 (text) → DATE**

### Syntax
```sql
TO_DATE(string, format)
```

---

### Example
```sql
SELECT TO_DATE('2025-12-03', 'YYYY-MM-DD') AS order_date
FROM dual;
```

---

### Common Error Example
Wrong:
```sql
SELECT TO_DATE('03-12-2025');
```
Correct:
```sql
SELECT TO_DATE('03-12-2025','DD-MM-YYYY');
```

---

## 3. TO_NUMBER

### Purpose
Converts **VARCHAR2 (text) → NUMBER**

### Syntax
```sql
TO_NUMBER(string)
```

---

### Example
```sql
SELECT TO_NUMBER('1500') + 500 AS total
FROM dual;
```

---

### With Format Model
```sql
SELECT TO_NUMBER('12,500.50','99,999.99') AS amount
FROM dual;
```

---

---

## Practical Examples

### EX1 – TO_CHAR
```sql
SELECT full_name,
       TO_CHAR(birth_date,'DD-MON-YYYY') AS dob
FROM students;
```

---

### EX2 – TO_DATE
```sql
SELECT full_name
FROM students
WHERE birth_date = TO_DATE('01-01-2005','DD-MM-YYYY');
```

---

### EX3 – TO_NUMBER
```sql
SELECT TO_NUMBER('100') * 2 AS result
FROM dual;
```

---

---

## Comparison Summary

| Function | Input Type | Output Type | Use |
|----------|--------------|----------------|-------|
| TO_CHAR | Date / Number | Text | Display formatting |
| TO_DATE | Text | Date | String → date conversion |
| TO_NUMBER | Text | Number | Numeric operations |

---

---

## Lab Exercises

### LAB 1 – TO_CHAR
Display current date as:
```sql
DD/MM/YYYY
```

---

### LAB 2 – TO_DATE
Filter students born after:
```sql
01-01-2000
```

---

### LAB 3 – TO_NUMBER
Convert:
```sql
'2,500.75'
```
into number and add **100** to it.
