# SQL Formation System

A single-file web app that parses Java/Spring log output, extracts SQL queries, substitutes `?` placeholders with actual parameter values, and displays nicely formatted SQL.

## Features

- **Log parsing** — paste raw Java/Spring log text; SQL statements and their parameters are extracted automatically
- **Parameter substitution** — replaces `?` placeholders using `> param:[1-value][2-value]` lines from the log
- **Raw SQL mode** — paste semicolon-delimited SQL directly (no log wrapper needed)
- **Structured formatting** — each clause (`SELECT`, `FROM`, `WHERE`, `JOIN`, `ORDER BY`, etc.) is formatted with consistent indentation
- **Syntax highlighting** — keywords, string literals, and numeric values are colour-coded
- **Copy button** — one click copies the formatted SQL for each statement
- **Download** — export all results as a `.txt` file
- **Selection jump** — select any text in the input and a badge appears showing which SQL # it belongs to; click to scroll directly to that card
- **Responsive** — side-by-side on desktop, stacked on mobile

## Usage

Open `index.html` in any modern browser — no build step, no dependencies.

### Log format

```
2026-05-07 09:44:31,703 http-nio-8080-exec-9 [INFO ] SomeService - SELECT col FROM table WHERE id = ?
> param:[1-42]
```

### Raw SQL format

```sql
SELECT ProductID, ProductName FROM Products WHERE CategoryID = 1;
UPDATE Products SET Price = 99 WHERE ProductID = 5;
```

## Output example

```sql
SELECT
    ProductID,
    ProductName
FROM
    Products
INNER JOIN Categories
    ON  Products.CategoryID = Categories.CategoryID
WHERE
    CategoryID = 1
ORDER BY
    ProductName
```

## Tech

Plain HTML + CSS + JavaScript — zero dependencies, zero build tooling.
