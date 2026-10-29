# SQL Aggregate Functions — Quick Notes

### 1. What is an Aggregate Function?

An **aggregate function** takes values from **multiple rows** and produces **one summarized result**.

Think:

> **Many rows → One result**

Common aggregate functions:

```sql
COUNT()
SUM()
AVG()
MIN()
MAX()
```

---

### 2. Examples

Suppose we have:

| CITY   | POPULATION |
| ------ | ---------: |
| Mumbai |         10 |
| Pune   |          5 |
| Delhi  |          8 |
| Nagpur |          3 |

#### `COUNT()` → count rows

```sql
SELECT COUNT(*)
FROM CITY;
```

Result:

```text
4
```

#### `SUM()` → add values

```sql
SELECT SUM(POPULATION)
FROM CITY;
```

Result:

```text
26
```

#### `AVG()` → average

```sql
SELECT AVG(POPULATION)
FROM CITY;
```

#### `MIN()` → smallest

```sql
SELECT MIN(POPULATION)
FROM CITY;
```

#### `MAX()` → largest

```sql
SELECT MAX(POPULATION)
FROM CITY;
```

---

# 3. Aggregate vs Normal Function

This is **very important**.

### Normal function

Works **row by row**.

```sql
LENGTH(CITY)
```

Example:

```text
Mumbai → 6
Pune   → 4
Delhi  → 5
```

It does **not combine rows**.

Other examples:

```sql
UPPER(CITY)
LOWER(CITY)
LENGTH(CITY)
```

---

### Aggregate function

Works across **multiple rows**.

```sql
COUNT(CITY)
```

Example:

```text
Mumbai
Pune
Delhi
```

becomes:

```text
3
```

So:

```text
Normal function:
Row → Value

Aggregate function:
Many rows → One value
```

---

# 4. Do I Need `GROUP BY`?

### ❌ Not necessarily!

This is valid:

```sql
SELECT COUNT(*)
FROM STATION;
```

No `GROUP BY` because you want **one total count**.

---

### ✅ Use `GROUP BY` when you want a result for each group

For example:

```sql
SELECT STATE, COUNT(*)
FROM STATION
GROUP BY STATE;
```

Meaning:

> Count the stations **for each state**.

Result could be:

```text
STATE    COUNT
MH       20
GJ       15
DL       10
```

---

# 5. Easy Rule 🧠

Ask yourself:

### "Am I combining multiple rows?"

If **YES** → you're probably using an aggregate function.

```sql
COUNT()
SUM()
AVG()
MIN()
MAX()
```

If you're just transforming/checking **each individual row**:

```sql
LENGTH()
UPPER()
LOWER()
SUBSTRING()
```

→ these are normal/scalar functions.

---

### ⭐ Most important thing to remember

```text
Aggregate function
       ↓
Multiple rows
       ↓
One result
```

```text
GROUP BY
   ↓
Break rows into groups
   ↓
Aggregate each group
```

Example:

```sql
SELECT CITY, COUNT(*)
FROM STATION
GROUP BY CITY;
```

means:

> **Group rows by CITY → count each group.**

And:

```sql
SELECT COUNT(*)
FROM STATION;
```

means:

> **Count everything → one result.**
