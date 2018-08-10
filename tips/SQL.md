# SQL Snippets
- [SQL Snippets](#sql-snippets)
    - [First non null value](#first-non-null-value)
    - [Hierachical queries (Oracle Only)](#hierachical-queries-oracle-only)
        - [Example](#example)

Mainly link to Oracle features

## First non null value
```SQL
COALESCE(expr1, expr2, ..., exprn)
```
Equivalent to 
```SQL
CASE WHEN expr1 IS NOT NULL THEN expr1
    ELSE COALESCE(expr2, ..., exprn) END
```

## Hierachical queries (Oracle Only)
To use when a table contains a hierachical information (id of the parent, ...)
For instance, we can use it to rebuild cascading menu.

### Example

Table relations:

    | ParentID | ChildID |
    | -------- | ------- |
    | 1        | 2       |
    | 1        | 3       |
    | 2        | 4       |

Table items:

    | ID  | Text         |
    | --- | ------------ |
    | 1   | root element |
    | 2   | Item 2       |
    | 3   | Item 3       |
    | 4   | Item 4       |

Request:
```SQL
With myhierachy AS 
    (SELECT parentId,
         childId AS id,
         description
    FROM items, relations
    WHERE items.id = relations.childId(+) )
SELECT concat(lpad(' ',LEVEL*3-3,'_'),description),LEVEL
FROM myhierachy 
CONNECT BY prior id = parentId 
START WITH parentId is null;
```
