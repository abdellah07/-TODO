# What is a SQL Injection Attack?
    • Many web applications take user input from a form
    • A SQL injection attack involves placing SQL statements in the user input

# Bad input : 
    `'or 1=1; -- `
    ′ ; DROP TABLE Users --` 
    
• Using SQL injections, attackers can:
    Add new data to the database
    Modify data currently in the database
    Often can gain access to other user’s system capabilities by obtaining their password


# For Microsoft's SQl Server we can also execute a os commands
    ′ ; exec cmdshell ′net user badguy badpwd′ / ADD --
    Downloading Files
    Backdoor with Netcat 
    Direct Backdoor without  external commands 

# Impact of SQL Injection
    .,
    
    

# SQL Injection: Information Flows
    Inband - data is extracted using the same channel that is used to inject the SQL code.
    
    Out-of-Band - data is retrieved using a different channel (e.g.: an email with the results of the query is generated and sent to the tester)

    Inferential: - there is no actual transfer of data, but the tester is able to reconstruct the information by sending particular requests and observing the resulting behaviour of the website


# SQL Injection: Approaches :
        Error: Asking the DB a question that will cause an error to analyse it
        Union: The SQL UNION is used to combine the results of two or more SELECT SQL statements into a single result.
        Blind: Asking the DB a true/false question and using whether valid page returned or not


# Errors: Finding SQL Injection Bugs :
    1. Submit a single quote as input.
        If an error results, app is vulnerable.
        If no error, check for any output changes.
    2. Submit two single quotes.
        Databases use ’’ to represent literal ’
        If error disappears, app is vulnerable.
    3. Try string or numeric operators.
         Oracle: ’||’FOO
         MS-SQL: ‘+’FOO
         MySQL: ’ ’FOO
         2-2
         81+19
         49-ASCII(1)



# Injecting into SELECT
    Objective: find and exfiltrate sensitive data

# Injecting into INSERT
    Objective: find injection points / rewritable SQL queries

# Injecting into UPDATE
    Objective: bypass normal update conditions

# injection into union
    Objective: access tables / columns not exposed by the web app

    Allows attacker to read any table
        foo’ UNION SELECT number FROM cc--
        Requirements
        Results must have same number and type of columns.
        Attacker needs to know name of other table.
        DB returns results with column names of 1st query


# UNION
    Finding #columns with NULL
        ‘ UNION SELECT NULL--
        ‘ UNION SELECT NULL, NULL--
        ‘ UNION SELECT NULL, NULL, NULL--
    Finding #columns with ORDER BY
        ‘ ORDER BY 1--
        ‘ ORDER BY 2--
        ‘ ORDER BY 3--
    Finding a string column to extract data
        ‘ UNION SELECT ‘a’, NULL, NULL—
        ‘ UNION SELECT NULL, ‘a’, NULL--
        ‘ UNION SELECT NULL, NULL, ‘a’--


# Inference Attacks: Blind SQL Injection
    • Problem: What if app doesn’t print data?
        – typical countermeasure
    • Injection can produce detectable behavior
        – Successful or failed web page.
        – Noticeable time delay or absence of delay.
    • When testing for vulnerability, we know 1=1 is always true
    • For any other injected statements: If the same result is returned, the statement was also true



# Testing for SQL Injections
    • Identify
        – Identify The Injection (Tool or Manual)
        – Determine Injection Type (Integer or String)
    • Approach:
        – Error-Based SQL Injection (Easiest)
        – Union-Based SQL Injection (Great for data extraction)
        – Blind SQL Injection (Worst case....last resort


# Mitigating SQL Injection
    Ineffective Mitigations
        Blacklists
        Stored Procedures
    
    Partially Effective Mitigations
        Whitelists
        Prepared Queries

    Blacklists
        Filter out or Sanitize known bad SQL meta- characters, such as single quotes.

    Whitelist
        Reject input that doesn’t match your list of
        safe characters to accept.
    








# ----------------------------------------------------

Malware: Malicious Software
• Terminology

– Trojan horse: allows remote access to unauthorized users

– Virus: computer program designed to spread (requires human intervention)

– Worm: does not require human intervention

– Adware: ads when application is running

– Spyware: monitors & collects information to be transmitted to a third
party without user knowledge/consent

– Ransomware: asks for a ransom to prevent deletion of data (encrypted
and/or transferred to some other disk)

– Botnets: network of (ro)bot / zombie computers under the control of
attackers and used for perpetrating attacks or sending other vectors