# SQL Injection in WHERE Clause

## Lab
PortSwigger Web Security Academy – SQL Injection (WHERE clause)

## Objective
To understand how user input is processed inside a SQL WHERE condition
and how improper handling leads to SQL Injection.

## How the Application Works
The application uses user input to filter data.
The input is directly included inside a SQL WHERE clause.

Example (conceptual):
SELECT * FROM products WHERE category = 'user_input';

## Testing the Input
Input used:
'

## Observation
Injecting a single quote caused a change in application behavior,
indicating that the input was being interpreted as part of the SQL query.

## Exploitation
Payload used:
' OR '1'='1 but in actual field i used this as '+OR+1=1--(i learn -- this makes all condition as comment after this )

This makes the WHERE condition always true, returning all records.

## Impact
An attacker could access data beyond intended restrictions.

## Prevention
- Use parameterized queries (prepared statements)
- Validate and sanitize user input
- Use secure ORM practices
