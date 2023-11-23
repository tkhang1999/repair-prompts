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

- ChatGPT:
```````
To fix the vulnerability related to the use of eval, you should avoid using eval as it can lead to security risks, especially when dealing with user input. Instead, you can use split to separate the input string into an array of numbers. Here's an updated version of your code:

```js
// Function 'main' to calculate the sum of a list of numbers entered by the user.
function main() {
  // Initialize a variable to store the sum of numbers
  let sum = 0;
  // Prompt the user to enter a space-separated list of numbers
  const input = prompt("Enter a space-separated list of numbers: ");

  // Split the input string into an array of numbers
  const numbers = input.split(' ').map(Number);

  // Check if the input is valid
  if (numbers.some(isNaN)) {
    console.error("Invalid input. Please enter a valid list of numbers.");
    return;
  }

  // Iterate through each number in the list and add it to the sum
  for (const num of numbers) {
    sum += num;
  }

  // Print the final sum value
  console.log(`Sum of ${numbers} = ${sum}`);
}

// Call the main function
main();
```
```````

- Bard:
``````
The primary issue with the provided code is the use of the eval function, which allows arbitrary code execution based on user input. This poses a significant security vulnerability as malicious users can inject harmful code into the prompt input, potentially compromising the system or executing unwanted actions.

To address this vulnerability and prevent arbitrary code execution, replace the eval function with a safer approach that explicitly parses the user input and converts it into a valid JavaScript array of numbers. Here's the revised code:

```js
// Function 'main' to calculate the sum of a list of numbers entered by the user.
function main() {
  // Initialize a variable to store the sum of numbers
  let sum = 0;

  // Prompt the user to enter a space-separated list of numbers
  const inputNumbers = prompt("Enter a space-separated list of numbers: ");

  // Split the input string into an array of numbers
  const numbers = inputNumbers.split(" ").map(Number);

  // Validate each input to ensure it is a valid number
  for (const num of numbers) {
    if (isNaN(num)) {
      alert("Invalid input: Please enter only numbers separated by spaces.");
      return; // Exit the function if invalid input is found
    }
  }

  // Iterate through each number in the array and add it to the sum
  for (const num of numbers) {
    sum += num;
  }

  // Print the final sum value
  console.log(`Sum of ${numbers} = ${sum}`);
}
```
``````