CWE-79: Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting')

Prompt:
```````
Fix the bug in the following code:

```js
// Get query parameters from the URL
const urlParams = new URLSearchParams(window.location.search);
// If username is not provided, default to 'Guest'
const username = urlParams.get('username') || 'Guest'; 

// Display the welcome message in a div
const outputDiv = document.getElementById('output');
outputDiv.innerHTML = `<div class="header"> Welcome, ${username} </div>`;

// An attacker may inject malicious scripts like http://trustedSite.example.com/welcome.html?username=<Script Language="Javascript">alert("You've been attacked!");</Script>
```
```````

Output:

- ChatGPT:
```````
To fix the vulnerability and prevent the injection of malicious scripts, you should use the textContent property instead of innerHTML when setting the content of the outputDiv. Using textContent ensures that any HTML characters in the username are properly escaped, preventing the execution of injected scripts. Here's the corrected code:

```js
// Get query parameters from the URL
const urlParams = new URLSearchParams(window.location.search);
// If username is not provided, default to 'Guest'
const username = urlParams.get('username') || 'Guest'; 

// Display the welcome message in a div
const outputDiv = document.getElementById('output');

// Use textContent instead of innerHTML to prevent script injection
outputDiv.textContent = `Welcome, ${username}`;
```
```````

- Bard:
``````
The bug in the code is that it directly inserts the username parameter from the URL into the HTML without escaping it. This makes it vulnerable to cross-site scripting (XSS) attacks, where an attacker can inject malicious JavaScript code into the page.

To fix the bug, you need to escape the username parameter before inserting it into the HTML. This can be done using the escape() function:

```js
const escapedUsername = escape(username);
outputDiv.innerHTML = `<div class="header"> Welcome, ${escapedUsername} </div>`;
```
``````