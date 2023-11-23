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

- ChatGPT:
```````
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
```````

- Bard:
``````
The provided code is vulnerable to parent directory traversal attacks, which allow an attacker to delete files outside of the intended safe directory. To fix this bug, you can use the path.resolve() function to normalize the input path and ensure that it remains within the safe directory. Here's the corrected code:

```js
// Read the input path from user
const inputPath = getInputPath();

// Normalize the input path to prevent parent directory traversal
const safePath = path.resolve("/safe_dir/", inputPath);

// Verify that the normalized path is still within the safe directory
if (safePath.startsWith("/safe_dir/")) {
  const fs = require('fs');
  // Delete the file
  fs.unlink(safePath, (err) => {
    if (err) {
      console.error(`Error deleting file: ${err.message}`);
    } else {
      console.log("File deleted successfully.");
    }
  });
} else {
  console.error("Invalid input path: Path is outside the safe directory.");
}
```
``````