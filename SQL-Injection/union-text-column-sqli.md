# SQL Injection – UNION Attack (Finding a Text Column)

## Lab
PortSwigger Web Security Academy – SQL Injection (UNION attack, finding a column containing text)

## Objective
To understand how UNION-based SQL Injection works and how to identify
which column in the original query supports string (text) data.

## How the Application Works
The application retrieves data from a database using a SQL query.
The results of this query are displayed in the application response.

When user input is unsafely included in the SQL query, it becomes possible
to inject additional queries using the UNION operator.

Conceptual example:
SELECT column1, column2 FROM products WHERE category = 'input';

## Finding the Number of Columns
To determine how many columns are returned by the original query,
the ORDER BY technique was used.

Example inputs:
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--

When an error occurred, it indicated that the column number exceeded
the actual number of columns in the query.

## Confirming Column Count with UNION
After identifying the correct number of columns, the UNION SELECT
statement was used with NULL values.

Example:
' UNION SELECT NULL, NULL--

A successful response confirmed the correct column count.

## Identifying the Text-Compatible Column
To determine which column accepts string data, NULL values were
replaced one at a time with a string value.

Examples:
' UNION SELECT 'test', NULL--
' UNION SELECT NULL, 'test'--

The column where the string appeared in the response was identified
as the text-compatible column.

## Solving the Lab
Once the text-compatible column was identified, the test string was
replaced with the random value provided by the lab.

Example (conceptual):
' UNION SELECT NULL, 'random_value'--

When the value appeared in the page response, the lab was successfully solved.

## Impact
An attacker could use UNION-based SQL Injection to:
- Extract sensitive data from the database
- Enumerate database structure
- Access confidential information

## Prevention
- Use parameterized queries (prepared statements)
- Avoid dynamic SQL query construction
- Validate and sanitize user input
- Apply least-privilege access to database accounts

## Disclaimer
This write-up is for educational purposes only.
Do not test or exploit vulnerabilities on systems without proper authorization.

  -(Sakshyam koirala)
