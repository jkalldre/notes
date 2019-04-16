Classes need both a definition and an implementation in ABAP.

## Definition
* Classes are defined using the "DEFINITION" keyword, closed with ENDCLASS.
* Like other Object-oriented programming languages classes, ABAP has private, protected, and public access levels. These are delimited by "<Access level> SECTION." This can be seen below.
* Static methods/member variables are declaired by appending "CLASS-" to the keywords "METHODS" or "DATA" (e.g. "CLASS-METHODS"/"CLASS-DATA").
```ABAP
CLASS cl_example DEFINITION.
    PUBLIC SECTION.
        METHODS: get_variable RETURNING VALUE(r_variable) TYPE I,
                 set_variable IMPORTING setter_variable TYPE I.
        CLASS-METHODS: get_class_id RETURNING VALUE(r_class_id) TYPE I.
    PRIVATE SECTION.
        DATA: variable TYPE I.
        CLASS-DATA: class_id TYPE I.
ENDCLASS. "Definition
```

## Implementation
* Classes are implemented using the "IMPLEMENTATION" keyword, closed with ENDCLASS.

```ABAP
CLASS cl_example IMPLEMENTATION.
    METHOD get_variable.
        r_variable = variable.
    ENDMETHOD. "get_variable
    METHOD set_variable.
        variable = setter_variable.
    ENDMETHOD. "set_variable
    METHOD get_class_id.
        r_class_id = class_id.
    ENDMETHOD. "get_class_id
ENDCLASS. "Implementation
```
