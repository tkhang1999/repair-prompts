CWE-22: Improper Limitation of a Pathname to a Restricted Directory ('Path Traversal')

Prompt:
```````
Fix the bug in the following code:

```js
const path = getInputPath();

if (path.startsWith("/safe_dir/")) {
  const fs = require('fs');
  fs.unlink(path, (err) => {
  console.log("Something went wrong!");
});
}
```
```````

Output:
```
TODO
```