<h1>Apply Filters to SQL Queries</h1>
<h2>Project description</h2>
As a security professional at a large organization, part of my job is to investigate security issues to help keep the system secure. I recently discovered some potential security issues that involve login attempts and employee machines.
<br /><br />
My task is to examine the organization’s data in their employees and log_in_attempts tables. I’ll need to use SQL filters to retrieve records from different datasets and investigate the potential security issues.

<h2>Retrieve after hours failed login attempts</h2>
I recently discovered a potential security incident that occurred after business hours. To investigate this, I queried the log_in_attempts table to review after hours login activity. The following query identifies all failed login attempts that occurred after 18:00. The time of the login attempt is found in the login_time column. The success column contains a value of 0 when a login attempt failed; either a value of 0 or FALSE can be used in the query to identify failed login attempts.

![SQL01](https://github.com/user-attachments/assets/9094081d-8d9b-493d-a0d2-499d6ed9b351)

The SELECT * FROM log_in_attempts part of the query returns all columns from the log_in_attempts table. The rest of the query, WHERE login_time > '18:00' AND success = FALSE; filters those records to only include ones where login times were after 6 pm and were failed attempts.

<h2>Retrieve login attempts on specific dates</h2>
A suspicious event occurred on 2022-05-09. To investigate this event, I reviewed all login attempts which occurred on this day and the day before: (the date of the login attempt is found in the login_date column)

![SQL02](https://github.com/user-attachments/assets/7a50418f-8d37-4350-b159-3a8c76473798)
![SQL03](https://github.com/user-attachments/assets/ef9b70ea-5dd4-47fb-9592-17228d94d6da)

Here, the logial operator OR has been used to filter results. The two dates included have been separated with OR to get records of all login attempts that occured on 2022-05-09 or 2022-05-08.

<h2>Retrieve login attempts outside of Mexico</h2>
There’s been suspicious activity with login attempts, but the team has determined that this activity didn't originate in Mexico. So I investigated login attempts that occurred outside of Mexico. I used filters in SQL to create a query that identifies all login attempts that occurred outside of Mexico:

![SQL04](https://github.com/user-attachments/assets/a75e5704-13ff-48bb-ab63-d5e43e51d445)
![SQL05](https://github.com/user-attachments/assets/ee929d0f-d3d9-4a5c-8793-e553e27d8dce)
![SQL06](https://github.com/user-attachments/assets/86cb4477-df87-4344-9321-465da910b966)
![SQL07](https://github.com/user-attachments/assets/b1486914-4d48-431d-8749-9cc22734bfb6)

Here, the NOT operator has been used to include all results that are outside Mexico. When referring to Mexico, the country column contains values of both MEX and MEXICO, so I used the LIKE keyword with % to make sure MEX and MEXICO are both excluded (% is a wildcard character in SQL used to substitute one or more characters in a string).

<h2>Retrieve employees in Marketing</h2>
My team wants to perform security updates on specific employee machines in the Marketing department. I'm responsible for getting information on these employee machines and will need to query the employees table to identify all employees in the Marketing department for all offices in the East building. Following is the query that accomplishes this:

![SQL08](https://github.com/user-attachments/assets/afdee5e3-4129-44dd-820a-0bf75ec103bf)

The department of the employee is found in the department column, which contains values that include Marketing. The office is found in the office column. Offices in the East building begin with the string 'East'. Some examples of values in this column are East-170 and East-320. Therefore, to filter for the East building, I used the LIKE keyword with %. 

<h2>Retrieve employees in Finance or Sales</h2>
My team now needs to perform a different security update on machines for employees in the Sales and Finance departments. I used the following query to accomplish this:

![SQL09](https://github.com/user-attachments/assets/9c8e8bd6-56a5-4805-81b9-65b3c1cec6f3)
![SQL10](https://github.com/user-attachments/assets/f5fec83c-846e-4daa-8c14-85b3b36dd50c)

The OR operator ensures that employees from the Sales department as well as Finance department are included in the results. Note that even though both conditions are based on the same column, there is a need to write out both full conditions; department must be specified as the column in both conditions.

<h2>Retrieve all employees not in IT</h2>
My team needs to make one more update to employee machines. The employees who are in the Information Technology department already had this update, but employees in all other departments need it. The following query identifies all employees not in the IT department:

![SQL11](https://github.com/user-attachments/assets/78f9b7e7-a308-4535-a6f4-fa59fdcdacf2)
![SQL12](https://github.com/user-attachments/assets/0ed57c15-4cc2-4cfe-bb5f-5189af616767)
![SQL13](https://github.com/user-attachments/assets/205dfc06-44c1-4d5b-a42f-ff83f45a14c9)
![SQL14](https://github.com/user-attachments/assets/8a2de8d8-5c00-4508-855d-f44fe2412b76)

 
 
 

The NOT operator is used here to exclude all employees from the Information Technology department, and is placed after WHERE.
<h2>Summary</h2>
In this project, I ran SQL queries to retrieve information from a database. I also applied AND, OR, and NOT operators to filter SQL queries to investigate potential security issues and help the system secure.
