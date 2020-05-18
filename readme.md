# Database Connection

Database_Connection is a snippet that wraps around mysql-connector and provides some easy to use yet basic functionalities for querying a MySQL database.

## Requirements

The snippet utilises mysql-connector so you will need to grab it with pip:

```bash
pip install mysql-connector
```

Or:

```bash
pip install -r requirements.txt
```

## Usage

Just copy the scipt in your working directory and instantiate the class like below:

```python
from DatabaseConnection import DatabaseConnection

db = DatabaseConnection(database_name, host, user, password)
```

There are 4 types of queries supported:
- Select data --> DatabaseConnection.select_data
- Update data --> DatabaseConnection.update_row
- Insert data --> DatabaseConnection.insert_data
- Custom query --> DatabaseConnection.custom_query

### General format of usage

All types of queries are executed with the same format which is the following:

```python
db.run_query(db.select_data, arguments)
```

The arguments variable has a standard format that you can retrieve with a built-in function or you can create on your own:

```python
arguments = db.create_template_arguments()

arguments = {
	'table_name': '',   # String    / Is the table name in the db                               / Mandatory
	'columns': [],      # List      / Are the columns we updating/selecting/inserting           / Mandatory
	'data': [],         # List      / Are the data we are inserting/updating                    / Used for inserting and updating queries
	'where_cols': [],   # List      / Are the columns for the where clause (e.g., id_entry)     / Used for updating and selecting queries
	'where_values': []  # List      / Are the expressions of the where clause                   / Used for updating and selecting queries
}
```

After running the query you can access the results by doing:

```python
results = db.output
```

### Comments on usage

Some comments on usage of each function that corresponds to a query type:
- Selecting Data
  - You can select all columns if in the columns element of arguments you enter ```"*"```.
- Updating Data
  - You can update only a single row at a time. For updating multiple rows, use the function in a loop.
- Inserting Data
  - If the data element of the arguments variable contains values, then you are inserting a single row.
  - You can insert multiple rows if you pass a list or tupe in the data element.


<p align="center" style="margin-top: 10px;"><a href="https://aethon.gr" target="_blank"><img src="https://aethon.gr/wp-content/uploads/2019/07/AETHON_logo_animated.gif" width="100" height="100" align="center"/></a></p>
  
