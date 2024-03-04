# Week 9 Deliverables
---
## Introduction
Work out an equivalent class partitioning and boundary value analysis for blackbox testing of your program. Explain all the equivalence classes, examples of boundary/middle values in each equivalence class and the rationale behind your choices.

**Types of input:** 
1. File Path 1
2. File Path 2
3. Combination of header names

## Equivalence Classes
File Path 1 & 2:
| Invalid             | Valid           |
| ------------------- | --------------- |
| File Path not found | File Path found |

Combination of header names
| Invalid                | Valid              |
| ---------------------- | ------------------ |
| Header names not found | Header names found | 

## Boundary Value Analysis
**Valid Inputs in the CSV file**
_Given that the user input for header names is <A,B,C>, and both files can be found_ 

Middle values:
1. Both csv files only have headers <A,B,C> in the correct order AND both files contain the same number of rows in the same order.

Boundary values:
1. Both csv files only have headers <A,B,C> but not in the same order
	- This is valid but the code will need to be able to identify the correct the correct headers when making comparison, instead of naively taking the first three
2. Both csv files do not contain the same number of rows
	- This is valid but the code will need to flag the extra rows as exception, instead of naively ignoring them.
3. Both csv files do not have rows in the same order
	- This is valid but the code will need to identify the right row to compare across both CSV files, as the same ID might be in different rows, instead of naively comparing row n in both CSV files.
4. One or both CSV files are empty
	- This is valid but code will need to stop running instead of creating an error when trying to iterate an empty object.

**Invalid Inputs in the CSV file**
_Given that the user input for header names is <A,B,C>, and both files can be found_ 

Middle values:
1. One or both of the csv files do not have one of the given headers in user input <A,B,C>
	- This is invalid because the columns are not present, making it impossible to do a meaningful comparison. Notify user of error.

Boundary values:
1. One or both of the csv files have extra headers other than the given headers in user input <A,B,C>
	- This is invalid because there are extra columns, which means that even though a row may match in both csv files for headers <A,B,C>, it can differ for other columns with other headers. Such comparison is not meaningful, hence user should be notified of error.

#testing