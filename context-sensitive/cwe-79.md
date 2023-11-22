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
```````
ChatGPT:
"""
To fix the "Cross-site Scripting" (XSS) vulnerability in the given code, you should ensure that user input is properly sanitized before being inserted into the HTML. One way to achieve this is by using the textContent property instead of innerHTML to set the content of the outputDiv. Here's an updated version of the code:

```js
const urlParams = new URLSearchParams(window.location.search);
const username = urlParams.get('username') || 'Guest'; 

const outputDiv = document.getElementById('output');

// Use textContent to set the content, which automatically escapes HTML entities
outputDiv.textContent = `Welcome, ${username}`;
```
"""
```````