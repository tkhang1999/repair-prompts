CWE-79: Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')

Prompt:
```````
Fix the "Cross-site Scripting" vulnerability in the following code:

```js
const urlParams = new URLSearchParams(window.location.search);
const username = urlParams.get('username') || 'Guest'; 

const outputDiv = document.getElementById('output');
outputDiv.innerHTML = `<div class="header"> Welcome, ${username} </div>`;
```
```````

Output:
```
TODO
```