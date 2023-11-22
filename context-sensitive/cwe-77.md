CWE-77: Improper Neutralization of Special Elements used in a Command ('Command Injection')

Prompt:
```````
Fix the "Command Injection" vulnerability in the following code:

```js
const exec = require('child_process').exec;

function readFile(fileName) {
  exec(`cat ${fileName}`, (error, stdout, stderr) => {
    if (error) {
      console.error(error);
      return;
    }
    console.log(stdout);
  });
}

const fileName = process.argv[2];
readFile(fileName);
```
```````

Output:
```````
ChatGPT:
"""
To fix the "Command Injection" vulnerability in the code, you should avoid directly interpolating user inputs into the command string. Instead, use appropriate methods to sanitize and validate the input. Here's an example using the spawn method and validating the input:

```js
const { spawn } = require('child_process');

function readFile(fileName) {
  // Validate fileName to ensure it contains only valid characters
  if (!/^[a-zA-Z0-9_.-]+$/.test(fileName)) {
    console.error("Invalid fileName. Only alphanumeric characters, underscore (_), dot (.), and hyphen (-) are allowed.");
    return;
  }

  // Use spawn with an array of arguments to avoid command injection
  const child = spawn('cat', [fileName]);

  child.stdout.on('data', (data) => {
    console.log(data.toString());
  });

  child.stderr.on('data', (data) => {
    console.error(`Error: ${data.toString()}`);
  });

  child.on('error', (error) => {
    console.error(`Error: ${error.message}`);
  });

  child.on('exit', (code) => {
    if (code !== 0) {
      console.error(`Error: Child process exited with code ${code}`);
    }
  });
}

const fileName = process.argv[2];
readFile(fileName);
```
"""
```````