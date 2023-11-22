CWE-77: Improper Neutralization of Special Elements used in a Command ('Command Injection')

Prompt:
```````
Fix the bug in the following code:

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
The code you provided looks generally fine, but there are potential security issues with using exec to execute shell commands, especially when user input is involved. It opens up the possibility of command injection attacks. It's recommended to use safer alternatives, such as fs.readFile, for reading files.

Here's an updated version of your code using fs.readFile:

```js
const fs = require('fs');

function readFile(fileName) {
  fs.readFile(fileName, 'utf8', (err, data) => {
    if (err) {
      console.error(err);
      return;
    }
    console.log(data);
  });
}

const fileName = process.argv[2];

if (fileName) {
  readFile(fileName);
} else {
  console.error("Please provide a file name as a command-line argument.");
}
```
"""
```````