# Javascript
---

## Datatypes
JS does not require numbers to be declared as integers or floats. However, they need to be declared as var, which makes the variable **global**. 

var inside a function does not require the variable to be different from outside global variable, and is **local** within the function.

However, var inside a block like if-else block will overwrite the variable outside. If want same name, but not overwrite, use **let** keyword

**const** keyword will make a data value fixed forever

**Warning:** Javascript is not transitive, i.e. a == b, b == c does not mean that a == c

## Common functions
| python               | javascript                                |
| -------------------- | ----------------------------------------- |
| print("Hello World") | alert("Hello World")                      |
| type()               | typeof()                                  |
| list[a:b]            | name.slice(a,b) (last index not included) |
| input("question")    | prompt("question")                                          |

## Template literals
Idea is similar to fstring placeholders in Javascript

## Operators
There is no // operator in javascript
unary plus is to coerce string into number

## Comparison operator
=== is strict equals to checker, will check if something is equal in value **AND TYPE**
```
0 == [] #true
0 === [] #false
NaN == NaN #false haha big brain
```

## Special operators
conditional comma delete in instanceof new this typeof void

## Conditionals
If else is similar to java
got switch statement, which requires a break, because the program will read 
- looks ugly because of break

## Tricky!!
need to convert integers received from prompt into a number

## Arrays
use python list as a mental model
no negative indexing though
if you add in a new element in an index that exceed the length of the array, it will automatically extend the array and add that element

Useful methods
- pop() and push()
- shift() and unshift() -- unshift appends new array to the start
- reverse()
- sort()
	- inbuilt sort by default will sort the elements as strings. So if need to sort as values, then need to give a sorting function as a parameter (java vibesss)
- concat()
- slice()
- splice()
	- to remove one or more items
	- can also replace and insert items too though!
- indexOf and lastIndexOf()
- every(),some() and map() methods
	- every is like the **and** function and some is the **or** function
	- map perform function on each element of array
- includes() 
- similar function as (3 **in** array)
- flat()

## Interesting stuff to know
`=>` is a lambda function very interesting to use with map
OOP not recommended but prototype iz good
#webp