Sources: https://www.youtube.com/watch?v=9NGDFx98bvM

## Selection Screen
* A selection screen is one of the four types of user dialogs.
* The selection screens are designed whenever input is required fro mth euser.
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
