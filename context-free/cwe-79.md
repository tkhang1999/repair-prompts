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

- ChatGPT:
```````
The code you provided looks mostly correct for extracting the 'username' parameter from the URL and displaying a welcome message. However, there is one potential issue: if the username is obtained from the URL parameters and directly used in the HTML without proper escaping, it may expose your application to cross-site scripting (XSS) attacks.

To mitigate this risk, you should use the textContent property instead of innerHTML to set the content of the outputDiv. Here's the corrected code:

```js
const urlParams = new URLSearchParams(window.location.search);
const username = urlParams.get('username') || 'Guest';

const outputDiv = document.getElementById('output');
outputDiv.textContent = `Welcome, ${username}`;
```
```````

- Bard:
```````
The bug in the code is that the username variable is not properly escaped before being inserted into the HTML. This could allow a malicious user to inject JavaScript code into the page, which could then be executed when the page is rendered.

To fix the bug, you need to escape the username variable before inserting it into the HTML. This can be done using the escape() function:

```js
const urlParams = new URLSearchParams(window.location.search);
const username = urlParams.get('username') || 'Guest'; 

const escapedUsername = escape(username);
const outputDiv = document.getElementById('output');
outputDiv.innerHTML = `<div class="header"> Welcome, ${escapedUsername} </div>`;
```
```````