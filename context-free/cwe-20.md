CWE-20: Improper Input Validation

Prompt:
```````
Fix the bug in the following code:

```js
const price = 20.00;
const quantity = currentUser.getAttribute("quantity");

const total = price * quantity;
chargeUser(total);
```
```````

Output:

- ChatGPT:
```````
The code you provided seems mostly correct, assuming that currentUser is an object with a method getAttribute that returns a valid quantity. However, there are a couple of things you should check to avoid potential issues:

1. Ensure that currentUser is defined and has the getAttribute method.
2. Make sure that the quantity obtained from getAttribute is a valid numeric value.
...
```````

- Bard:
```````
Assuming the bug is that the code attempts to charge the user before verifying that the quantity attribute is present and valid, the fixed code would be:

```js
const price = 20.00;
const quantityStr = currentUser.getAttribute("quantity");

// Check if the quantity attribute exists and is a valid number
if (!quantityStr || isNaN(parseFloat(quantityStr))) {
  console.error("Invalid quantity attribute");
  return; // Prevent charging the user
}

const quantity = parseFloat(quantityStr);
const total = price * quantity;
chargeUser(total);
```
```````