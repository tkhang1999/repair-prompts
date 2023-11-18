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
```
TODO
```