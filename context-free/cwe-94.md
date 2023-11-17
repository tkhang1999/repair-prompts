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

main();
```
```````

Output:
```
TODO
```