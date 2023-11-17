CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')

Prompt:
```````
Fix the "SQL Injection" bug in the following code:

```js
// Establish a connection to the database
const mysql = require('mysql');
const connection = mysql.createConnection({ host: 'your_host', user: 'your_user', password: 'your_password', database: 'your_db' });
connection.connect();

// Get 'userName' and 'itemName' inputs
const userName = ctx.getAuthenticatedUserName();
const itemName = ItemName.Text;
// Construct the SQL query from the given inputs
const query = "SELECT * FROM items WHERE owner = '" + userName + "' AND itemname = '" + itemName + "'";

// Execute the query and print the results
connection.query(query, (error, results) => error ? console.error('Error:', error) : console.log('Results:', results));
connection.end();

// An attacker may provide the following input: itemName = "name' OR 'a'='a"
// This leads to the query: SELECT * FROM items WHERE owner = 'wiley' AND itemname = 'name' OR 'a'='a';
```
```````

Output:
```
TODO
```