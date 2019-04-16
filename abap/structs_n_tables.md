
ABAP structures, whether or not they're created in a data dictionary or locally in a program, are similar to `structures` in other languages. Likewise for table types created in the data dictionary, they're just `arrays`.

## ABAP Structures

ABAP structures can be identified and created in one of two ways. The first way is to simply define a structure directly in-line in your program using `data/type: begin of` or to create a data dictionary structure globally visible to all other ABAP reports.

```abap
types: begin of struct_example,
  id       type i,      " identification
  name     type string, " last, first name
  age      type i,      " age in years
  birthday type datum,  " birthdate 
end of struct_example.
```

We have a structure, a piece of data that has containers for other pieces of data with in it. In our ABAP code we generally use structures to organize data relevant to one subject. For example sometimes it's related to sales order information, or material information. We just have to declare `data` using the type `struct_example`.

```abap
" include z_struct_example_inc.
data: example_data type struct_example.
example_data-id       = 1.
example_data-name     = 'Some Guy'.
example_data-age      = 26.
example_data-birthday = sy-datum. " sorry, I'm lazy
write : / 'Hello, ', example_data-name
```

This is how all structures in the data dictionary behave as well. The main difference is that the above ABAP structure is only visible within reports or classes that include a file with this structure defined inside it. This can be done quite easily. In reports, it's as simple as

```abap
include z_struct_example_inc.
data: my_example_data type struct_example.
```

## ABAP Tables

A table type is similar to an array in other languages, it's a linear collection of elements accessible by an index or some kind of key. There is support for a few different types of tables within ABAP.

* **Standard**: A normal array with one element appearing after the next.
* **Sorted**: A sorted array based upon a key(s) field. 
* **Hashed**: A non-sorted array that hashes values for quickly searching.

Since a table is just an array of information, the table structure can either be determined by an ABAP structure or an ABAP basic data type.

```abap
" This table is an array of strings. Each element in this table is a string.
data: string_table type standard table of string.

" Instead of a string we're using a structure so that we can collect data.
data: example_table type standard table of struct_example.
``` 

As with arrays, tables also support many of the same operations.

### Appending/Inserting

If you're working with a **sorted** or **hashed** table, than the data needs to be added using `insert`. The `insert` keyword makes sure whichever data you're trying to add to the table is in the right place.

With standard tables `append` can be used. The data is going to be placed on the end of the table after the last added element. 

```abap
data string_table type standard table of string.
data string_1 type string value 'Hallo'.
data string_2 type string value 'Wereld'.
data string_3 type string value 'Hatseflats'.
field-symbols <string> type string.

append string_1 to string_table.
append string_2 to string_table.
append string_3 to string_table.

loop at string_table assigning <string>.
  write : / string_table. 
endloop.
```

### Iteration

Iteration is looping across the elements of the table one after another. You can add conditions to your code to prevent particular rows from being brought into further calculations.

```abap
field-symbols: <string> type string.
loop at string_table assigning <string>.
  write : / <string>.
endloop.

field-symbols: <example> type struct_example.
loop at example_table assigning <example>.
  if ( <example>-id > 5 ).
    write : / <example>-name.
  endif.
endloop.
```

### Modification

The recommended way to modify data in the table (from my perspective) is to assign the table data to a `field-symbol`. `Field-symbols` are similar to how pointers in C and other languages work. They're a variable that represents the actual content of it's assignment. Modifications to field-symbols will be reflected in the table.

```abap
" Using the example data from Appending
field-symbols <string> type string.
read table string_table assigning <string> index 1.
<string> = 'Hello'.
loop at string_table assigning <string>.
  write : / <string>.
endloop.
```

### Deleting 

There is a couple of ways to delete data from a table. Data from a table can be removed based upon the contents of another table, removed by the key index of the table, or a condition can be supplied.

```abap
// TODO examples.
```
