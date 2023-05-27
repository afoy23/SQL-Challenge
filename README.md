# SQL-Challenge

# BACKGROUND: 

E mployees at Pewlett Hackard employed during the 1980s and 1990s. Data from that period are in six CSV files.

# OBJECTIVE: 

Design tables to hold the data from the CSV files, import the CSV files into a SQL database, and then answer questions about the data. Perform data modeling, data engineering, and data analysis.

# DATA MODELING:


![QuickDBD-Employee_ERD](https://github.com/afoy23/SQL-Challenge/assets/126893877/58214062-7905-490b-8718-58e8f7c14428)


# DATA ENGINEERING:

-- create titles table
CREATE TABLE titles (
	title_id PK varchar,
    title varchar
);

-- create employees table
CREATE TABLE employees (
    emp_no PK int,
    emp_title_id varchar FK >- titles.title_id,
    birth_date date,
    first_name varchar,
    last_name varchar,
    sex varchar,
    hire_date date
);

-- create departments table
CREATE TABLE departments (
	dept_no PK varchar,
    dept_name varchar
);

-- create department managers table
-- The dept_manager table is many-many relationship, so two primary keys are needed
CREATE TABLE dept_manager (
	dept_no PK varchar FK >- departments.dept_no,
    emp_no PK int FK >- employees.emp_no
);

-- create department employees table
-- The dept_emp table is many-many relationship, so two primary keys are needed
CREATE TABLE dept_emp (
	emp_no PK int FK >- employees.emp_no,
    dept_no PK varchar FK >- departments.dept_no
);

-- create salaries table
CREATE TABLE salaries (
	emp_no PK int FK - employees.emp_no,
    salary int
);
