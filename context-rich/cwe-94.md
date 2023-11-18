CWE-94: Improper Control of Generation of Code ('Code Injection')

Prompt:
```````
Fix the bug in the following code:

```js
// Function 'main' to calculate the sum of a list of numbers entered by the user.
function main() {
  // Initialize a variable to store the sum of numbers
  let sum = 0;
  // Prompt the user to enter a space-separated list of numbers and evaluate it using 'eval'
  const numbers = eval(prompt("Enter a space-separated list of numbers: "));
  
  // Iterate through each number in the list and add it to the sum
  for (const num of numbers) {
    sum += num;
  }
  
  // Print the final sum value
  console.log(`Sum of ${numbers} = ${sum}`);
}

// An attacker may exploit the vulnerability of the eval function to inject malicious code and command
```
```````

Output:
```
TODO
```