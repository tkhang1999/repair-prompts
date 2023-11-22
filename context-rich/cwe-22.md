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
```````
ChatGPT:
"""
To fix the bug and prevent directory traversal attacks, you should use a more secure method to ensure that the path stays within the expected directory. One way to achieve this is to use the path module in Node.js to resolve the absolute path and then check if it is still within the safe directory. Here's an updated version of the code:

```js
const path = getInputPath();
const safeDirectory = "/safe_dir/";

const fs = require('fs');
const pathModule = require('path');

// Resolve the absolute path
const absolutePath = pathModule.resolve(path);

// Check if the resolved path is still within the safe directory
if (absolutePath.startsWith(pathModule.resolve(safeDirectory))) {
  // Delete the file
  fs.unlink(absolutePath, (err) => {
    if (err) {
      console.error(`Error deleting file: ${err.message}`);
    } else {
      console.log("File deleted successfully.");
    }
  });
} else {
  console.error("Invalid path. Access to the specified path is not allowed.");
}
```
"""
```````