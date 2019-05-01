Sources: https://www.youtube.com/watch?v=9NGDFx98bvM

## Selection Screen
* A selection screen is one of the four types of user dialogs.
* The selection screens are designed whenever input is required from the user.
* Both single value input or complex value input can be provided using selection screens.

```ABAP
"Syntax for declaring parameters.
PARAMETERS <P_NAME> TYPE <TABLE-FIELDNAME>.
PARAMETERS <P_NAME> AS CHECKBOX.
PARAMETERS <P_NAME> RADIOBUTTONGROUP <GROUP_NAME>
           <P_NAME2> RADIOBUTTONGROUP <GROUP_NAME>
           <P_NAME2> RADIOBUTTONGROUP <GROUP_NAME>.
           
"EX on parameters:
DATA: wa_example TYPE <tablename>.
PARAMETERS p1 TYPE <tablename>-<fieldname>.

SELECT SINGLE * FROM <tablename> INTO wa_example WHERE <fieldname> = p1.

WRITE:/ wa_example-<fieldname>,
        wa_example-<fieldname1>,
        wa_example-<fieldname2>.

"EX on checkboxes
PARAMETERS p_check AS CHECKBOX.
IF p_check = 'X'.
  WRITE:/ 'CheckBox is selected.'.
ELSE.
  WRITE:/ 'CheckBox is not selected.'.
ENDIF.

```

### Multiple Selection screens
```ABAP
START-OF-SELECTION.
    DATA: wa_test TYPE yjka_sample1.
    PARAMETERS menu_sel TYPE I.

    SELECTION-SCREEN BEGIN OF SCREEN 100.
        "Specify parameters
    SELECTION-SCREEN END OF SCREEN 100.
    SELECTION-SCREEN BEGIN OF SCREEN 200.
        "Specify parameters
    SELECTION-SCREEN END OF SCREEN 200.

    CASE menu_sel.
        WHEN 1.
            CALL SELECTION-SCREEN 100.
            "do stuff with inputs
        WHEN 2.
            CALL SELECTION-SCREEN 200.
            "do stuff with inputs
    ENDCASE.
```
