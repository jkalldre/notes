Source: https://help.sap.com/doc/abapdocu_752_index_htm/7.52/en-US/abapmethods_general.htm

## Parameters
* There are several types of parameters in ABAP which we will review here:
    * Importing
        * Preferred    
    * Exporting
    * Returning
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
### Returning
### Changing //TODO
### Raising //TODO
### Exceptions //TODO
### Preferred //TODO
