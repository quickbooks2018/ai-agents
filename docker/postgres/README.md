# Postgres

### Postgres Network
```bash
docker network create postgres
docker network ls
docker network rm postgres
```

### Postgres
```bash
docker run -id \
  --name postgres-test \
  --restart unless-stopped \
  -e POSTGRES_PASSWORD=asim \
  -e POSTGRES_USER=asim \
  -e POSTGRES_DB=test \
  -p 5432:5432 \
  --network postgres \
  postgres:15.8 
  ```

  ### PG Admin
  ```bash
  docker run -id \
  --name pgadmin \
  --restart unless-stopped \
  -e PGADMIN_DEFAULT_EMAIL=admin@example.com \
  -e PGADMIN_DEFAULT_PASSWORD=admin \
  -p 8080:80 \
  --network postgres \
  dpage/pgadmin4:latest
  ```

### MCP Postgres (Read Only)
```bash
git clone https://github.com/modelcontextprotocol/servers.git
cd servers
docker build -t mcp/postgres -f src/postgres/Dockerfile . 
```

- MCP Postgres Json config
```json
{
  "mcpServers": {
    "postgres": {
      "command": "docker",
      "args": [
        "run", 
        "-i", 
        "--rm", 
        "mcp/postgres",
        "postgresql://asim:asim@host.docker.internal:5432/test"]
    }
  }
}
```
- multiple mcp servers
```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "--init", "-e", "DOCKER_CONTAINER=true", "mcp/puppeteer"]
    },
    "postgres": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "mcp/postgres",
        "postgresql://asim:asim@host.docker.internal:5432/bank_db"]
    }
  }
}
```

### Example (bank_db)
Example of creating a bank_db database and an employees table with a few corrections to the SQL code for successful execution.

Step 1: Create a Database
To create a new database named bank_db, use this command in SQL:
##### Create Database
```bash
CREATE DATABASE bank_db;
```

Step 2: Create a Table (employees)
After creating the database, we can create a table named employees in the bank_db database. Make sure to correct typos ode for creating the employees table:
```bash
CREATE TABLE employees (
    emp_id SERIAL PRIMARY KEY,
    fname VARCHAR(100) NOT NULL,
    lname VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    dept VARCHAR(50),
    salary DECIMAL(10, 2) DEFAULT 30000.00,
    hire_date DATE NOT NULL DEFAULT CURRENT_DATE
);
```
```document
Explanation of the Code
emp_id SERIAL PRIMARY KEY: Automatically generates a unique ID for each employee.
fname VARCHAR(100) NOT NULL: Stores the employee's first name with a maximum of 100 characters.
lname VARCHAR(100) NOT NULL: Stores the employee's last name with a maximum of 100 characters.
email VARCHAR(100) NOT NULL UNIQUE: Stores the email address, which must be unique for each employee.
dept VARCHAR(50): Stores the department name with a maximum of 50 characters.
salary DECIMAL(10, 2) DEFAULT 30000.00: Stores the employee's salary with two decimal places. The default salary is set to 30,000.00.
hire_date DATE NOT NULL DEFAULT CURRENT_DATE: Stores the hire date, which defaults to the current date if not specified.
In DECIMAL(10, 2), the two numbers specify the precision and scale of the decimal values:

10: This is the precision, which is the total number of digits allowed in the number, including both sides of the decimal point.
2: This is the scale, which represents the number of digits allowed to the right of the decimal point.
So, DECIMAL(10, 2) means:

Up to 10 digits in total.
Of those 10 digits, 2 digits are reserved for the decimal (fractional) part.
Example Values
12345678.90 (10 digits in total, with 2 decimal places) - Valid
1234567.89 - Valid
1234567890.12 - Invalid (too many digits)
1234.567 - Invalid (too many decimal places)
With this definition, DECIMAL(10, 2) allows for values up to 99,999,999.99.
```

### Inserting data in tables (query tool)
```bash
INSERT INTO employees (emp_id, fname, lname, email, dept, salary, hire_date) 

      VALUES

(1, 'Raj', 'Sharma', 'raj.sharma@example.com', 'IT', 50000.00, '2020-01-15'),

(2, 'Priya', 'Singh', 'priya.singh@example.com', 'HR', 45000.00, '2019-03-22'),

(3, 'Arjun', 'Verma', 'arjun.verma@example.com', 'IT', 55000.00, '2021-06-01'),

(4, 'Suman', 'Patel', 'suman.patel@example.com', 'Finance', 60000.00, '2018-07-30'),

(5, 'Kavita', 'Rao', 'kavita.rao@example.com', 'HR', 47000.00, '2020-11-10'),

(6, 'Amit', 'Gupta', 'amit.gupta@example.com', 'Marketing', 52000.00, '2020-09-25'),

(7, 'Neha', 'Desai', 'neha.desai@example.com', 'IT', 48000.00, '2019-05-18'),

(8, 'Rahul', 'Kumar', 'rahul.kumar@example.com', 'IT', 53000.00, '2021-02-14'),

(9, 'Anjali', 'Mehta', 'anjali.mehta@example.com', 'Finance', 61000.00, '2018-12-03'),

(10, 'Vijay', 'Nair', 'vijay.nair@example.com', 'Marketing', 50000.00, '2020-04-19');
```

### Querying the Table
```bash
# Retrieve All Employees
SELECT * FROM employees;

# Retrieve Employees in the HR Department
SELECT * FROM employees 
WHERE dept = 'HR';

# Retrieve Employee by ID
SELECT * FROM employees 
WHERE emp_id = 8;
```