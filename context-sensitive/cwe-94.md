CWE-94: Improper Control of Generation of Code ('Code Injection')

Prompt:
```````
Fix the "Code Injection" vulnerability in the following code:

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
To fix the "Code Injection" vulnerability in the given code, you should avoid using eval with user input, as it can execute arbitrary code and lead to security risks. Instead, you can use JSON.parse to parse the input as a valid JSON array, ensuring that only well-formed data is accepted. Here's an updated version of the code:

```js
function main() {
  let sum = 0;

  // Prompt the user for input
  const input = prompt("Enter a space-separated list of numbers: ");

  try {
    // Parse the input as a JSON array
    const numbers = JSON.parse(`[${input}]`);

    // Validate that numbers is an array of numbers
    if (Array.isArray(numbers) && numbers.every(isFinite)) {
      for (const num of numbers) {
        sum += num;
      }

      console.log(`Sum of ${numbers} = ${sum}`);
    } else {
      console.error("Invalid input. Please enter a valid list of numbers.");
    }
  } catch (error) {
    console.error("Error parsing input:", error.message);
  }
}
```
```````

- Bard:
``````
To fix the "Code Injection" vulnerability in the provided code, you should avoid using the eval() function to directly evaluate user input. Instead, use regular expressions to extract the numbers from the user input and then parse them into integers before adding them to the sum variable. Here's the modified code:

```js
function main() {
  let sum = 0;
  const numbersString = prompt("Enter a space-separated list of numbers: ");
  const numbersRegex = /\d+/g; // Regular expression to match digits
  const numbers = [];

  for (const match of numbersString.matchAll(numbersRegex)) {
    const num = parseInt(match[0]); // Parse the matched digit into an integer
    numbers.push(num);
  }

  for (const num of numbers) {
    sum += num;
  }

  console.log(`Sum of ${numbers} = ${sum}`);
}
```
``````