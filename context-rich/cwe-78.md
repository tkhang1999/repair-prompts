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
```````
ChatGPT:
"""
The code you provided is vulnerable to command injection, as it directly uses user input (req.body.user) to construct a shell command. To fix this vulnerability, you should validate and sanitize the input before using it in a shell command. One way to do this is by using a regular expression to ensure that the username consists only of valid characters. Here's an example:

```js
const { exec } = require('child_process');

// Extract the 'user' property from the request body
const userName = req.body.user;

// Validate the username using a regular expression
const validUserNameRegex = /^[a-zA-Z0-9_-]+$/;
if (!validUserNameRegex.test(userName)) {
  console.error("Invalid username. Please provide a valid username.");
  return;
}

// Construct a shell command to list files in the specified user's home directory
const command = `ls -l /home/${userName}`;

// Execute the shell command
exec(command, (error, stdout, stderr) => {
  // Log an error message if there is an issue with the command execution
  if (error) {
    console.error(`Error executing command: ${error.message}`);
  } else {
    console.log(stdout);
  }
});
```
"""
```````