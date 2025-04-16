### Introduction to SQL Injection
- SQLi is a web application injection vulnerability that occurs when an attacker injects malicious SQL statements into an application's input fields.
- This occurs when a web application doesn't properly validate user input, allowing an attacker to inject SQL code/queries that can manipulate the database or gain access to sensitive information.
- For eg, suppose a website has a login form that accepts a username and password. If the website does not properly validate the user's input, an attacker could enter a malicious SQL statement into the username field that would allow them to bypass the login process and gain access to the website's database.
- SQLi attacks can have serious consequences including left of the sensitive data, unauthorized access to sensitive systems, and even full system compromise.
- Complex web applications generally use a database for storing data, user credentials or statistics.
- Content Managements Systems(CMSs) as well as simple web pages  can convert to relational databases such as MySQL, MSSQL, SQL Server, Oracle, PostgreSQL, and others.
- To interact with databases entities such as systems operators, programmers, applications and web application use SQL.

##### History of SQL Injection Attacks
- The term "SQL Injection" was coined by Jeff Forristal, also know as "Rain Forest Puppy", in a paper he presented at the DefCon 8 conference in 2000.
- Forristal was one of the first security researchers to publicly document the SQL Injection vulnerability and explain how it could be exploited to gain unauthorized access to databases and sensitive information.
- ![[Pasted image 20250129020445.png]]

##### SQL Injection Impact
- Confidentiality - Since SQL databases generally hold sensitive data, loss of confidentiality is a frequent problem with SQL Injection Vulnerabilities.
- Integrity - Just as it may be possible to read sensitive information, it is also possible to make changes or even delete this information with a SQL Injection Attack.
- Authentication - If poor SQL commands are used to check user names and passwords, it may be possible to connect to a system as another user with no previous knowledge of the password.
- Availability - SQLi attacks can affect the availability of a web app and database and could take the website down due to loss/damage of data.

##### SQL Injection Consequences
- Sensitive Data Exposure / Data Breaches - SQLi attacks can result in authorizes access to sensitive data stored in a database. Attackers maybe able to view or steal confidential information, such as customer data, financial information and intellectual property.
- Data Manipulation - Attackers maybe able to modify or delete data stored in a database, potentially cause data loss or corruption.
- Code Execution - If a database user has administrative privileges, an attacker can gain access to the target system using malicious code.
- Business Disruption - Successful SQLi attacks can lead to business disruption, as organizations work to restore services and prevent further attacks.

### Anatomy of SQL Injection Attacks
![[Pasted image 20250129023200.png]]

### Types of SQL Injection Vulnerabilities
![[Pasted image 20250210181552.png]]

##### In-Band SQL Injection
- In-band SQL Injection is the most common type of SQL Injection attack. It occurs when an attacker uses the same communication channel to send the attack and receive the results..
- In other words, the attacker injects malicious SQL Code into the web application and receives the results of the attack through the same channel used to submit the code.
- In-band SQL Injection attacks are dangerous because they can be used to steal sensitive information, modify or delete data, or take over the entire web application or even the entire server.
	![[Pasted image 20250210182021.png]]
- **Subtypes** - 
	- Error-based SQL Injection : In error-based SQL Injection, the attackers injects SQL Code that causes the web application to generate an error message. The error message can contain valuable information about the database schema or the contents of the database itself, which the attacker can use to further exploit the vulnerability.
		![[Pasted image 20250210182720.png]]
	- Union-based SQL Injection : In union-based SQL injection, the attackers uses the UNION operator to combine the results of  or more SQL queries into a single result set. By manipulating the injected SQL Code, the attacker can extract fata from the Database that they are no authorized to access.

##### Blind SQL Injection
- Blink SQL Injection is a type of a SQL Injection attack where an attacker can exploit a vulnerability in a web application that doesn't directly reveal information about the database or the res

