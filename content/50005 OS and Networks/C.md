# C documentation
---

Things to know about C
| Sign                       | Meaning                                        | Example                                                                                                          |
| -------------------------- | ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `*` during instantiation   | Declare a (datatype) pointer called (ptr_name) | `int *p ;` // Declare an int pointer called p                                                                   |
| `*` during print statement | The contents of the address held in pointer                                               | `printf ("%d\n\n", *ptr_to_some_var);` //Print out the contents of the location pointed to by `ptr_to_some_var` | 
| `&`                        | address of                                     | `p = &a` = address of buffer variable                                                                            |

[Details on `*`](https://www.linuxtopia.org/online_books/programming_books/gnu_c_programming_tutorial/Pointer-operators.html)

New Terminology
calloc
malloc 

Special Notes:
Arrays are pointers in C


printf ("%d\n\n", *ptr_to_some_var);    /* 5 */
"Print out the contents of the location pointed to by `ptr_to_some_var`."

Datatype

Pointers
Void * Return type
CLI program writing
File I/O
Exception Handling

exit vs return
[Resources](https://stackoverflow.com/questions/3463551/what-is-the-difference-between-exit-and-return)
exit will stop the process there and then, but return will stop the function and return to where it was called.

#os