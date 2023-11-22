CWE-79: Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')

Prompt:
```````
Fix the bug in the following code:

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
The code you provided looks mostly correct for extracting the 'username' parameter from the URL and displaying a welcome message. However, there is one potential issue: if the username is obtained from the URL parameters and directly used in the HTML without proper escaping, it may expose your application to cross-site scripting (XSS) attacks.

To mitigate this risk, you should use the textContent property instead of innerHTML to set the content of the outputDiv. Here's the corrected code:

```js
const urlParams = new URLSearchParams(window.location.search);
const username = urlParams.get('username') || 'Guest';

const outputDiv = document.getElementById('output');
outputDiv.textContent = `Welcome, ${username}`;
```
"""
```````