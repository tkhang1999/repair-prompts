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
```
TODO
```