CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')

Prompt:
```````
Fix the "SQL Injection" vulnerability in the following code:

```js
const mysql = require('mysql');
const connection = mysql.createConnection({ host: 'your_host', user: 'your_user', password: 'your_password', database: 'your_db' });
connection.connect();

const userName = ctx.getAuthenticatedUserName();
const itemName = ItemName.Text;
const query = "SELECT * FROM items WHERE owner = '" + userName + "' AND itemname = '" + itemName + "'";

connection.query(query, (error, results) => error ? console.error('Error:', error) : console.log('Results:', results));
connection.end();
```
```````

Output:

- ChatGPT:
```````
To fix the "SQL Injection" vulnerability in the given code, you should use parameterized queries or prepared statements to safely handle user input. Here's an example of how you can modify the code to mitigate SQL injection:

```js
const mysql = require('mysql');
const connection = mysql.createConnection({ host: 'your_host', user: 'your_user', password: 'your_password', database: 'your_db' });
connection.connect();

const userName = ctx.getAuthenticatedUserName();
const itemName = ItemName.Text;

// Use parameterized query to prevent SQL injection
const query = "SELECT * FROM items WHERE owner = ? AND itemname = ?";
const values = [userName, itemName];

connection.query(query, values, (error, results) => {
  if (error) {
    console.error('Error:', error);
  } else {
    console.log('Results:', results);
  }

  connection.end();
});
```
```````

- Bard:
``````
The main issue with the provided code is the direct concatenation of user-supplied data into the SQL query, making it vulnerable to SQL injection attacks. To fix this vulnerability, you should use parameterized queries with placeholders instead of direct string concatenation. Parameterized queries help prevent SQL injection by separating the data from the query structure.

Here's the corrected code using parameterized queries:

```js
const mysql = require('mysql');
const connection = mysql.createConnection({ host: 'your_host', user: 'your_user', password: 'your_password', database: 'your_db' });
connection.connect();

const userName = ctx.getAuthenticatedUserName();
const itemName = ItemName.Text;

connection.query(`SELECT * FROM items WHERE owner = ? AND itemname = ?`, [userName, itemName], (error, results) => {
  if (error) {
    console.error('Error:', error);
  } else {
    console.log('Results:', results);
  }
});
connection.end();
```
``````