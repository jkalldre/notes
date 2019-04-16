## Data Types
Syntax to declare a variable in ABAP
``` ABAP
DATA [variable_name] TYPE [data_type].
"Example:
DATA first_name TYPE string.
```
ABAP Data Types

|Data Type|Initial Field Length|Valid Field Length|Initial Value| Meaning|
|---------|-------------------|-------------------|-------------|--------|
|Numeric|
|I|4|4|0|Integer|
|F|8|8|0| Float|
|P|*|1-16|0|Packed Number|
|Character|
|C|1|1-65535|'...'|Text field (alphanumeric)|
|D|8|8|'00000000'|Date Field (YYYYMMDD)|
|N|1|1-65535|'0...0'|Numeric Text Field (Numeric characters)|
|T|1|6|6|'000000'|Time Field (HHMMSS)|
|X|1|1-65536|X'0...0'|Hexidecimal Field|

## Logic
Logical operators
* Less Than: LT/<
* Less or Equal: LE/<=
* Greater Than: GT/>
* Greater or Equal: GE/>=
* Equal: EQ/=
* Not Equal: NE/<>
 
Control Statements
```ABAP
"If (logical expression == exp below)
IF [not] exp [ and/or [not] exp ].
...
 [ELSEIF exp.
 ...]
 [ELSE.
 ...]
ENDIF.

"Case
CASE case_variable_name.
 WHEN value_1.
 ...
 WHEN value_2.
 ...
 [WHEN OTHERS.
 ...]
ENDCASE.
DO.

"While
WHILE exp.
...
...
ENDWHILE.

"Do Loop
DO n TIMES.
...
...
ENDDO.
```
