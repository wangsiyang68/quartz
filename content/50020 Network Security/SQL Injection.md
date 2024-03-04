`1=1` predicate looks useless but it is useful in SQL injection attacks as it will cause database to dump everything
Some prerequisite/trial and error gain knowledge:
- Name of the database to modify
- How to escape the remaining command from the server (depends on what DB is the server using)

Countermeasures:
1. Filtering and encoding data
2. Prepared statement
	- Separate the data and code by sending them in separate channels to the database server