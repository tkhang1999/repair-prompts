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
```
TODO
```