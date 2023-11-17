CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')

Prompt:
```````
Fix the bug in the following code:

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
```
TODO
```