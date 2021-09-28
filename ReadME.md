# MODULE 7 EMPOYEE DATABASE CHALLENGE


## 1. OVERVIEW OF THE ANALYSIS

This analysis will help Bobby and his manager prepare for the "silver tsunami" as many current employees are reaching the retirement age.
The analysis has two deliverables:
* Deliverable 1: Determine the number of retiring employees per title
* Deliverable 2: Identify employees who are eligible to participate in a mentorship program.

The results of this analysis are included in two separe folders. 
* The Queries folder includes the SQL file named "Employee_Database_challenge.sql".
* The Data folder including the retirement_titles.csv, unique_titles.csv, retiring_titles.csv, and mentorship_eligibilty.csv files.  

## 2. Results:

### 2.1 Retirement Titles
This table shows 133,776 employees about to retire. However, as you can see in the firs cells there are duplicate names. For example, Chirstian Koblick appears to have worked as an Engineer from Dec 1st 1986 to Dec 1st 1995. Then it appears to work as a Senior Engineer from Dec 1st 1995 until now. 

### 2.2 Unique Titles
The table shows that there are 90,398 employees about to retire.  It is called "Unique Titles" because takes into account  the many titles that an employee could have had during their career. This table holds the latest or most recent title of the employee.

### 2.3 Retiring titles
This table shows the amount of employees that are about to retiree per title.  As you can see, most of them are Engineers followed by Senior Staff. Then there are about 13,207 staff members about to retire and 10,062 Senior Engineer.  It would be interesting to know what constitues a senior engineer to know how knowledgeable  or experienced they are. For example, if a senior engineer is stablished by having more than 20 years of work experience, probably it would be difficult to replace. However, if it is  defined as having more than 5 years of experience, then it could be easier to replace.  The las tree categories are 4500 Technique Leaders, 4391 Assistand Engineer and 6 Managers. 

### 2.4 Mentorship Eligibility
There are 1549 employees eligibles for the mentorship program. They were born in 1965 and currently work at the company. Somehting useful would be to know how many employees per title are eligible for the program, as well as from which departments they belong. Please see the summary section for this additional analysis. 



## 3. SUMMARY

The summary addresses the two questions and contains two additional queries or tables that may provide more insight. (5 pt)

### 3.1 Deliverable 1 - Retirement Employee per Title

From the Retirement Titles table I believe we could obtain the amount of Titles an employee has had during their career at the company. With this information we could know about career paths opportunities in the company. This would be beneficial for future employees, as they would have an idea about what they could aspire to at the company. 

From the Unique Titles table I believe it would be beneficial to add a "gender" column. Nowadays companies are asked to hire an equitable amount of men and women because of gender equality and further women's rights. I believe knowing how gender is currently distributed would give an idea about if they are in need to have a gender equality policy at the company. 

### 3.2 Deliverable 2 - Mentorship Eligibility

It would be useful to have a Mentorship eligibility table group by Title. So we could have an idea of how many employees will be participating from each position level.

I used the below SQL code to obtain this information.

*Count of mentorship per title

        select count (mentorship_eligibility.emp_no), mentorship_eligibility.title
        into mentorship_eligibility_Titles
        from mentorship_eligibility
        group by mentorship_eligibility.title
        order by count (mentorship_eligibility.emp_no) DESC;

These are the results:
* Assistant Engineer 78
* Engineer 501
* Senior Engineer 169
* Senior Staff 569
* Staff 155
* Technique Leader 77
* TOTAL 1549 

Another data that would be useful to know would be to group the table by departments. 

I used the below SQL code to obatain this information.

*Count of mentorship per Department

First I added the department number to the mentorship_eligibility table. Then I performed a count by department. 

-- Count of mentorship per Department

        select * from deliverable_2_info;
        select count (deliverable_2_info.emp_no), deliverable_2_info.dept_no
        into mentorship_eligibility_dept
        from deliverable_2_info
        group by deliverable_2_info.dept_no
        order by count (deliverable_2_info.emp_no) DESC;

These are the results:
* 117 - D001 Marketing
* 064 - D002 Finance
* 097 - D003 Human Resources
* 322 - D004 PRoduction
* 396 - D005 Development
* 086 - D006 Quality Management
* 244 - D007 Sales
* 103 - D008 Research
* 120 - D009 Customer Service

According to the results the deparment with the highest mentorship eligible participants would be Development and the least would be Finance. 
