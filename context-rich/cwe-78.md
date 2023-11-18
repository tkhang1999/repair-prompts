CWE-78: Improper Neutralization of Special Elements used in an OS Command ('OS Command Injection')

Prompt:
```````
Fix the bug in the following code:

```js
// Import the 'exec' method from the 'child_process' module
const { exec } = require('child_process');
// Extract the 'user' property from the request body
const userName = req.body.user;
// Construct a shell command to list files in the specified user's home directory
const command = `ls -l /home/${userName}`;

// Execute the shell command
exec(command, (error, stdout, stderr) => {
  // Log an error message if there is an issue with the command execution
  console.log("Something went wrong!");
});
```
```````

Output:
```
TODO
```