# Block Structure
- Code is organized into blocks
- Blocks without names are *anonymous blocks*. Not saved in the database, one-time use.
- Useful in creating test units
```PL/SQL
[DECLARE]
	declaration statements;
BEGIN
	execution statements;
	[EXCECPTION]
		exception statement;
END;
/
```
- **Declaration** is used to define *data types*, *structures* and *variables*. Can also be used for declaration
- **Execution** is required in block structure. Must have at least one statement. Contains the execution code. Can be either PL/SQL or SQL
- **Exception** - As the name implies.
> '/' is used to execute the block

# Variables
- Must be declared in declaration block to be usable
- Must be less than 31 characters
- Not case sensitive
- Naming convention states that the variable should be preceded by the data type

| **Prefix** | **Data Type** |
| ---------- | ------------- |
| v_         | VARCHAR2      |
| n_         | NUMBER        |
| t_         | TABLE         |
| r_         | ROW           |
| d_         | DATE          |
| b_         | BOOLEAN       |
## Variable Declaration
- Variable name and data type, terminated with semicolon
- Can specify length constraints on data type in parentheses.
```PL/SQL
DECLARE
	v_first_name    VARCHAR2(20);
	v_last_name     VARCHAR2(20);
	n_employee_id   NUMBER;
	d_hire_date     DATE;
BEGIN
	NULL;
END;
/
```

## Variable Anchor
- Used when selecting values from columns in a database into a set of variables
- Allows the variable to have the same data type as the column.
- Done using `%TYPE` keyword
Selecting columns from the `EMPLOYEES` table
```PL/SQL
DECLARE
	v_first_name    EMPLOYEES.FIRST_NAME%TYPE;
	v_last_name     EMPLOYEES.LAST_NAME%TYPE;
	n_employee_id   EMPLOYEES.EMPLOYEE_ID%TYPE;;
	d_hire_date     EMPLOYEES.HIRE_DATE%TYPE;
BEGIN
	NULL;
END;
/
```

## Variable Assignment
- Done using the assignment operator `:=`  (colon, equal sign)
```PL/SQL
DECLARE
	v_first_name    EMPLOYEES.FIRST_NAME%TYPE;
	v_last_name     EMPLOYEES.LAST_NAME%TYPE;
	n_employee_id   EMPLOYEES.EMPLOYEE_ID%TYPE;;
	d_hire_date     EMPLOYEES.HIRE_DATE%TYPE;
BEGIN
	v_first_name:= 'Mary';
	v_last_name:= 'Magdalene';
	n_employee_id:= 10101010;
	d_hire_date:= TO_DATE('19990101',')
END;
/
```

- Can also be done using the `INTO` of the SQL `SELECT` statement. This moves the values from the SELECT query to the corresponding PL/SQL variables.
```PL/SQL
SET SERVEROUTPUT ON SIZE 1000000
DECLARE
	v_first_name    EMPLOYEES.FIRST_NAME%TYPE;
	v_last_name     EMPLOYEES.LAST_NAME%TYPE;
	n_employee_id   EMPLOYEES.EMPLOYEE_ID%TYPE;;
	d_hire_date     EMPLOYEES.HIRE_DATE%TYPE;
BEGIN
	SELECT employee_id,
		first_name,
		last_name,
		hire_date
	INTO
		v_first_name,
		v_last_name,
		d_hire_date
	FROM employee
	WHERE employee_id=200;
	
	DBMS_OUTPUT.PUT_LINE(v_first_name);
	DBMS_OUTPUT.PUT_LINE(v_last_name);
	DBMS_OUTPUT.PUT_LINE(d_hire_date);
END
/
```
> SET SERVEROUTPUT ON SIZE 1000000  -> Used to echo the database's output to the screen.

## Initialii