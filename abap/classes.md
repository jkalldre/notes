Sources: https://www.tutorialspoint.com/sap_abap/sap_abap_inheritance.htm

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

## Constructors
* Constructors in ABAP function as they would in any other OO programming language. To define a constructor
you simply need to name a method "constructor" and give it an implementation. When the object is created, the
constructor is called.

```ABAP
CLASS sample DEFINITION.
    PUBLIC SECTION.
        METHODS: constructor.
                "optional parameters
ENDCLASS. "sample

CLASS sample IMPLEMENTATION.
    METHOD constructor.
        "constructor functionality
    ENDMETHOD.
ENDCLASS. "sample
```
## Inheritance
* This allows a child (or subclass) to borrow (inherit) methods and/or member variables from a parent (superclass) to avoid redundant
coding.

```ABAP
CLASS Parent Definition.
PUBLIC Section.
Data: w_public(25) Value 'This is public data'.
Methods: ParentM.
ENDCLASS.

CLASS Child Definition Inheriting From Parent.
PUBLIC Section.
Methods: ChildM.
ENDCLASS.

CLASS Parent Implementation.
Method ParentM.
Write: w_public.
EndMethod. ENDCLASS.

CLASS Child Implementation.
Method ChildM.
Skip.
Write: 'Method in child class',
        / w_public.
EndMethod.
ENDCLASS.

Start-of-selection.
Data: Parent Type Ref To Parent,
      Child  Type Ref To Child.
Create Object: Parent, Child.
Call Method: Parent->ParentM,
             child->ChildM.
             
"Outputs:
" This is public data.
" Method in child class.
" This is public data.
```
