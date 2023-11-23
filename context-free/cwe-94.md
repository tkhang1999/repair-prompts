CWE-94: Improper Control of Generation of Code ('Code Injection')

Prompt:
```````
Fix the bug in the following code:

```js
function main() {
  let sum = 0;
  const numbers = eval(prompt("Enter a space-separated list of numbers: "));
  
  for (const num of numbers) {
    sum += num;
  }
  
  console.log(`Sum of ${numbers} = ${sum}`);
}
```
```````

Output:

- ChatGPT:
```````
The use of eval in this code is generally discouraged due to security and maintainability concerns. Instead, you can use prompt to get a string input, split it into an array of numbers, and then perform the sum. Here's an updated version of your code:

```js
function main() {
  const input = prompt("Enter a space-separated list of numbers: ");
  
  // Split the input string into an array of numbers
  const numbers = input.split(' ').map(Number);

  // Check if all elements in the array are valid numbers
  if (numbers.some(isNaN)) {
    console.error("Invalid input. Please enter a space-separated list of numbers.");
    return;
  }

  // Calculate the sum
  const sum = numbers.reduce((acc, num) => acc + num, 0);

  console.log(`Sum of ${numbers.join(', ')} = ${sum}`);
}

// Call the main function
main();
```
```````

- Bard:
```````
The provided code contains a potential security vulnerability due to the usage of eval(). The eval() function evaluates a string as JavaScript code, which means that an attacker could craft malicious input that would execute arbitrary code in your program. To fix this bug, replace the usage of eval() with a safer approach. Here's the corrected code:

```js
function main() {
  let sum = 0;
  const numbersString = prompt("Enter a space-separated list of numbers: ");
  const numbersArray = numbersString.split(" ");
  
  for (const numString of numbersArray) {
    const num = parseInt(numString);
    if (isNaN(num)) {
      continue; // Ignore non-numeric values
    }
    sum += num;
  }
  
  console.log(`Sum of ${numbersString} = ${sum}`);
}
```
```````