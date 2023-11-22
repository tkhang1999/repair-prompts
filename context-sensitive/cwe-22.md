CWE-22: Improper Limitation of a Pathname to a Restricted Directory ('Path Traversal')

Prompt:
```````
Fix the "Path Traversal" vulnerability in the following code:

```js
const path = getInputPath();

if (path.startsWith("/safe_dir/")) {
  const fs = require('fs');
  fs.unlink(path, (err) => {
    if (err) {
      console.error(`Error deleting file: ${err.message}`);
    } else {
      console.log("File deleted successfully.");
    }
  });
}
```
```````

Output:
```
TODO
```