# SQL Injection – UNION Attack (Retrieving Data from Other Tables)

## Lab
PortSwigger Web Security Academy – SQL Injection (UNION attack, retrieving data from other tables)

## Objective
To understand how UNION-based SQL Injection can be used to retrieve
data from other database tables when user input is unsafely included
in a SQL query.

## How the Application Works
The application filters products using a SQL query that directly
includes user-controlled input.

Because the query results are reflected in the application response,
it becomes possible to inject a UNION SELECT statement and retrieve
data from additional database tables.

Conceptual example:
SELECT column1, column2 FROM products WHERE category = 'input';

## Identifying Column Count and Data Types
To determine how many columns are returned by the original query,
UNION-based testing was performed using string values.

Example input:
' UNION SELECT 'abc','def'--

The successful response indicated that:
- The query returns two columns
- Both columns support text data

## Retrieving Data from Another Table
After identifying compatible columns, a UNION SELECT statement was
used to retrieve data from another database table.

Conceptual example:
' UNION SELECT username, password FROM users--

The application response displayed data from the users table,
including privileged account information.

## Impact
An attacker could use this vulnerability to:
- Extract sensitive data from the database
- Access user credentials
- Compromise privileged accounts

In real-world applications, this could lead to serious security
breaches and full system compromise.

## Prevention
- Use parameterized queries (prepared statements)
- Avoid dynamic SQL query construction
- Validate and sanitize all user input
- Apply least-privilege access to database accounts

## Disclaimer
This write-up is for educational purposes only.
Do not test or exploit vulnerabilities on systems without proper authorization.


  -(Sakshyam koirala)
