CWE-78: Improper Neutralization of Special Elements used in an OS Command ('OS Command Injection')

Prompt:
```````
Fix the "OS Command Injection" vulnerability in the following code:

```js
const { exec } = require('child_process');

const userName = req.body.user;
const command = `ls -l /home/${userName}`;

exec(command, (error, stdout, stderr) => {
  console.log("Something went wrong!");
});
```
```````

Output:
```````
ChatGPT:
"""
To fix the "OS Command Injection" vulnerability in the given code, you should properly sanitize and validate the user input before constructing the command. One way to achieve this is by using the child_process module's execFile function and providing an array of arguments, rather than interpolating user input directly into the command string.

Here's an example of how you can fix the code:

```js
const { execFile } = require('child_process');

const userName = req.body.user;

// Validate userName to ensure it contains only valid characters
if (!/^[a-zA-Z0-9_-]+$/.test(userName)) {
  console.error("Invalid userName. Only alphanumeric characters, underscore (_), and hyphen (-) are allowed.");
} else {
  const command = 'ls';
  const args = ['-l', `/home/${userName}`];

  execFile(command, args, (error, stdout, stderr) => {
    if (error) {
      console.error(`Error: ${error.message}`);
      return;
    }

    console.log(stdout);
  });
}
```
"""
```````