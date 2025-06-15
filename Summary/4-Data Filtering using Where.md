# LINQ - Lesson 4: Filtering Data with `Where`

In this lesson, we explore how to filter data using the powerful `.Where()` method in LINQ. Filtering is a common operation in most applications, and LINQ provides a clean and expressive way to do it.

---

## Setup Overview

We have:

- A `Car` record with properties such as `Id`, `Make`, and `Model`.
- A `CarRepository` class that includes:
  - `GetCars()` – Returns a collection of 1000 cars.
  - `PrintCars()` – Displays cars on the console.
- The `Program.cs` file fetches the cars and filters them before printing.

---

## What is `Where`?

The `Where` method filters data based on conditions.

### Key Characteristics:
- Evaluates each item in the collection.
- Only returns items that satisfy the condition (`true`).
- Returns an `IEnumerable<T>` of the original type.

---

## Where Overloads

### With Index

```csharp
var filteredCars = cars.Where((car, index) => car.Make == "Ford" && index % 2 == 0);

---

## Exceptions

The `Where` method may throw an `ArgumentNullException` if:

- The **source collection** is `null`.
- The **predicate** (the condition used for filtering) is `null`.

---

## Query Syntax

### No Filter

```csharp
var allCars = from car in cars
              select car;


### With Filter

```csharp
var fordCars = from car in cars
               where car.Make == "Ford"
               select car;

###  Multiple Conditions

```csharp
var selectedCars = from car in cars
                   where car.Make == "Ford" && car.Model == "GT"
                   select car;


### Logical OR

```csharp
var selectedCars = from car in cars
                   where car.Make == "Ford" && (car.Model == "GT" || car.Model == "F350")
                   select car;


### Method Syntax

```csharp
var fordCars = cars.Where(car => car.Make == "Ford");


### With Multiple Conditions

```csharp
var selectedCars = cars
    .Where(car => car.Make == "Ford" && (car.Model == "GT" || car.Model == "F350"));


### Chained Where

```csharp
var filteredCars = cars
    .Where(car => car.Make == "Ford")
    .Where(car => car.Model == "GT");


## Clean Code: Using Helper Method

To keep your code clean, readable, and reusable, extract the filtering logic into a named method:

```csharp
public static bool IsFord(Car car)
{
    return car.Make == "Ford";
}

###  Usage with Method Syntax

```csharp
var fordCars = cars.Where(IsFord);


### Usage with Query Syntax

```csharp
var fordCarsQuery = from car in cars
                    where IsFord(car)
                    select car;
