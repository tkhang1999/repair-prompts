CWE-77: Improper Neutralization of Special Elements used in a Command ('Command Injection')

Prompt:
```````
Fix the bug in the following code:

```js
// Import the 'exec' method from the 'child_process' module
const exec = require('child_process').exec;

// Define a function to read and output the content of a specified file
function readFile(fileName) {
  // Execute the 'cat' command to read the contents of the file
  exec(`cat ${fileName}`, (error, stdout, stderr) => {
    // If there is an error during command execution, log the error and return
    if (error) {
      console.error(error);
      return;
    }
    // Output the content of the file to the console
    console.log(stdout);
  });
}

// Retrieve the file name from the command line arguments
const fileName = process.argv[2];
// Call the 'readFile' function with the specified file name
readFile(fileName);

// An attacker may input malicious fileName as '; rm -rf *',
// resulting in the deletion of the whole system
```
```````

Output:
```
TODO
```