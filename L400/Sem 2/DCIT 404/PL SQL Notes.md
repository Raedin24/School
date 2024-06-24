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

