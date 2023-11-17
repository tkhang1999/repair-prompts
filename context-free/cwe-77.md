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
```
TODO
```