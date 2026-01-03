# SQL Injection – Authentication Bypass

## Lab
PortSwigger Web Security Academy – SQL Injection (Login bypass)

## Objective
To understand how SQL Injection can be used to bypass
authentication mechanisms.

## How Authentication Works
The application verifies login credentials using a SQL query
that checks both username and password.

Conceptual example:
SELECT * FROM users WHERE username = 'input' AND password = 'input';

## Testing Input
Injected payload in username field:
'--

Password field:
(any value)

## Observation
The application logged in successfully without validating
the password.

The SQL comment operator (--) caused the password condition
to be ignored by the database.

## Impact
An attacker can log in as any user without knowing the password,
leading to full account compromise.

## Prevention
- Use parameterized queries
- Avoid building SQL queries via string concatenation
- Implement proper input validation

  :(Sakshyam koirala)
