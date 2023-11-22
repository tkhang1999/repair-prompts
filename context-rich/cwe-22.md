CWE-22: Improper Limitation of a Pathname to a Restricted Directory ('Path Traversal')

Prompt:
```````
Fix the bug in the following code:

```js
// Read the input path from user
const path = getInputPath();

// Verify the input path is within the safe directory
if (path.startsWith("/safe_dir/")) {
  const fs = require('fs');
  // Delete the file
  fs.unlink(path, (err) => {
    if (err) {
      console.error(`Error deleting file: ${err.message}`);
    } else {
      console.log("File deleted successfully.");
    }
  });
}

// An attacker may input a path like "/safe_dir/../important.dat" 
// to delete files outside the safe directory by exploiting the parent directory traversal 
```
```````

Output:
```
TODO
```