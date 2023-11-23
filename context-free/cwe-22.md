CWE-22: Improper Limitation of a Pathname to a Restricted Directory ('Path Traversal')

Prompt:
```````
Fix the bug in the following code:

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

- ChatGPT:
```````
The code you provided looks correct for the most part. However, there's one potential issue to consider. If the file deletion is asynchronous, there might be a race condition where the program terminates before the deletion completes. To handle this, you can add a callback or use the fs.promises.unlink method (available in newer versions of Node.js) to ensure that the deletion is complete before the program exits.
...
```````

- Bard:
```````
The bug in the code is that it uses the fs.unlink() function to delete a file, but it does not check if the file exists before attempting to delete it. If the file does not exist, then fs.unlink() will throw an error.

To fix the bug, you can add a check to make sure that the file exists before attempting to delete it. Here is the updated code:

```js
const path = getInputPath();

if (path.startsWith("/safe_dir/")) {
  const fs = require('fs');

  if (fs.existsSync(path)) {
    fs.unlink(path, (err) => {
      if (err) {
        console.error(`Error deleting file: ${err.message}`);
      } else {
        console.log("File deleted successfully.");
      }
    });
  } else {
    console.error(`File does not exist: ${path}`);
  }
}
```
```````