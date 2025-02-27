# **SQL Injection - Explanation for an Interview**

## **Definition**  
SQL Injection (**SQLi**) is a **web security vulnerability** that allows an attacker to **manipulate an application's database** by injecting **malicious SQL queries**. It occurs when **user inputs are not properly sanitized** before being used in SQL statements.

---

## **Types of SQL Injection**  

1. **Error-Based SQLi** → The attacker triggers **database errors** to gain information.  
2. **Union-Based SQLi** → Uses the **UNION SQL operator** to extract data from different tables.  
3. **Boolean-Based SQLi** → The attacker sends **true/false queries** to infer data.  
4. **Time-Based SQLi** → Uses **time delays** (`SLEEP()`, `WAITFOR DELAY`) to check for vulnerabilities.  
5. **Blind SQLi** → The attacker **does not receive error messages** but can still infer data through responses.

---

## **Example of SQL Injection**  

### **Vulnerable Query:**
```sql
SELECT * FROM users WHERE username = 'admin' AND password = 'password123';
' OR '1'='1
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
cursor.execute("SELECT * FROM users WHERE username = ? AND password = ?", (user, password))
