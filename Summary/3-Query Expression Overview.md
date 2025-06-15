# 3. Query Expression Overview

Before diving into code, it’s important to understand some core concepts that make LINQ powerful and developer-friendly.

---

## 1. Support for Multiple Data Sources

LINQ allows querying and transforming data from various sources using a unified syntax.

You can write one query style for:

- SQL databases
- In-memory collections (arrays, lists)
- XML documents
- JSON files
- NoSQL databases like MongoDB (with LINQ providers)

This eliminates the need to learn a separate query language for each data type.

---

## 2.  Works Natively with C#

LINQ is built into the C# language, so:

- You don't need SQL or XQuery to work with data.
- Writing queries is intuitive if you already know C#.
- You get full IntelliSense and compiler support.

---

## 3. Strongly Typed Queries

LINQ is **strongly typed**, meaning:

- The data types are known at compile-time.
- Errors are caught early during development.
- You get type-safe queries with IntelliSense support.

This improves both reliability and readability.

---

## 4.  Two Ways to Write Queries

LINQ provides **two syntaxes** for writing queries:

### A.  Query Syntax

SQL-like syntax using `from`, `where`, and `select`.

```csharp
var evenNumbers = from n in numbers
                  where n % 2 == 0
                  select n;
```
### B. Method Syntax (Extension Methods)

Uses extension methods like `.Where()` and `.Select()`:

```csharp
var evenNumbers = numbers.Where(n => n % 2 == 0);
```

### Syntax Comparison Notes

- **Both styles produce the same result and performance.**
- **Method syntax is more popular in real-world development.**
- **You can combine both syntaxes in a single query.**

**Example:**

```csharp
var count = (from n in numbers
             where n > 10
             select n).Count();
```
## 5. Method Syntax for Some Operations

Some operations do **not** have equivalents in **query syntax**, so you **must use method syntax** for them. These include:

- `Count()`
- `Max()`
- `Min()`
- `Average()`

### Examples

```csharp
var maxValue = numbers.Max();
var totalCount = numbers.Count();
```
