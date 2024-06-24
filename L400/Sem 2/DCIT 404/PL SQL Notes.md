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
- Naming convention

| **Prefix** | **Data Type** |
| ---------- | ------------- |
| v_         | VARCHAR2      |
| n_         | NUMBER        |
| t_         | TABLE         |
| r_         | ROW           |
| d_         | DATE          |
| b_         | BOOLEAN       |
