Source: https://help.sap.com/doc/abapdocu_752_index_htm/7.52/en-US/abapmethods_general.htm,
        https://archive.sap.com/discussions/thread/914801

## Parameters
* There are several types of parameters in ABAP which we will review here:
    * Importing
        * Preferred    
    * Exporting
    * Returning Value()
    * Changing
    * Raising
    * Exceptions

* These parameter "prefixes" determine how the function/method will interact with the given variable. 
### Importing
```ABAP 
... IMPORTING parameter TYPE [type].
```
* This defines input parameters, information flowing *into* a function. When the function is called, data must be provided for all *non-optional* input parameter. These are pass-by-reference and *constant*, they cannot be changed within the function.
#### Preferred Parameter
* An input parameter can be mared as a **PREFERRED PARAMETER** *IFF* all input parameters are marked optional.
* Marking a parameter preferred implicitly sets it to optional, not *explicitly* marking the parameter as OPTIONAL or DEFAULT will resort in syntax warnings
* Example: If a function has several optional parameters and the function func( a ) is called, the parameter /a/ will be assigned to the preferred parameter.
```ABAP
FUNCTION example
    IMPORTING p1 TYPE I DEFUALT 123
    IMPORTING p2 TYPE string OPTIONAL
    IMPORTING p3 TYPE i OPTIONAL
    PREFERRED PARAMETER p3.
...
ENDFUNCTION.
```

### Exporting
* Defines output parameters, pass-by-value and is returned to the actual parameter after the method is ended successfully.
* Exporting defined for pass-by-reference acts as an input/output parameter. As such it is not initialized when a method starts and should not be read before the first write
```ABAP
" TODO Example method call
```

### Returning value()
* If a returning parameter is used, no other parameters may be marked exporting or changing.
* Methods/Functions using the Returning parameter are known as functional methods as they only allow one return value, and are passed-by-value.
* Functional Methods can be used within various expressions.
    * Logical expressions: IF, ELSEIF, WHILE, CHECK, WAIT
    • Case conditions: CASE, WHEN
    • Arithmetic expressions and bit expressions: COMPUTE
    • Sources of values as a local copy: MOVE
    • Search clauses for internal tables, assuming that the operand is not a component of the table row: LOOP AT ... WHERE

##### Exporting VS Functional: Checking a boolean
```ABAP
"Exporting
method( IMPORTING value = boolean_variable ).
IF boolean_variable eq 'X'.
...

"Functional
IF method() eq 'X'.
...

```
### Changing //TODO
### Raising //TODO
### Exceptions //TODO

