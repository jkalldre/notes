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
* When calling a method that has more than one parameter you must explicity assign each actual parameter is assigned to which formal parameter.
* If only one parameter present then the actual parameter can be provided without the formal, and it will be assigned to the only, or preferred parameter.
* Calling a function requires the special "CALL FUNCTION" syntax and parameters must be explicitly assigned.
```ABAP
FUNCTION example1
        IMPORTING p1 TYPE 1.
...
ENDFUNCTION. "example

"call example1
CALL FUNCTION 'example1'
        EXPORTING p1 = 123.
```
```ABAP
"Class example
CLASS tester DEFINITION.
        CLASS-METHODS: oneimport
                          IMPORTING p1 TYPE I,
                       twoimport
                          IMPORTING p1 TYPE I
                                    p2 TYPE I,
                       changing_exporting_param
                          IMPORTING p1 TYPE I
                          CHANGING  p2 TYPE I.
ENDCLASS.

CLASS tester IMPLEMENTATION.
        method oneimport.
        ...
        endmethod. "oneimport
        method twoimport.
        ...
        endmethod. "twoimport
        method changing_exporting_param.
        ...
        endmethod. "changing_exporting_param
ENDCLASS. "tester

START-OF-SELECTION.
        DATA: tmp TYPE I. "for third example
        "no formal parameter needed since one param is given and is an import
        tester=>oneimport( 123 ).
        "because both parameters are imports, no parameter type is needed but formal parameter is req.
        tester=>twoimport( p1 = 123    
                           p2 = 456 ). 
        "Because not all of the parameters are imports, the parameter type is now required explicitly.
        tester=>changing_exporting_param( EXPORTING p1 = 123
                                          CHANGING  p2 = tmp ).
```

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

