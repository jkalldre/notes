## Query

## Insert
### Sample Table
|MANDT|ID|SURNAME|GIVENAME|DOB|
|-----|--|-------|--------|---|

* When inserting from a program you can creating a TYPE of your table. e.g.
```ABAP
DATA: entry TYPE [nameOfTable].
```
* The created variable is treated as a struct and is accessed accordingly with each field acting
as a variable.
* Normal syntax is followed to insert into the table with the VALUES section just plug in the struct.

```ABAP
"So inserting an entry into the table would go like the following.
entry-mandt = 100.
entry-id = 1.
entry-surname = 'DOE'.
entry-givename = 'JANE'
entry-dob = '01/01/1990'.

INSERT INTO [nameOfTable] VALUES entry.
```
* The updated table would look like this.

|MANDT|ID|SURNAME|GIVENAME|DOB|
|-----|--|-------|--------|---|
| 100|1|DOE|JANE| 01/01/1990|

## Update

## Drop
