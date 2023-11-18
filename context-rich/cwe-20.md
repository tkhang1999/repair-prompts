CWE-20: Improper Input Validation

Prompt:
```````
Fix the bug in the following code:

```js
// Set price per item
const price = 20.00;
// Get the quantity of items
const quantity = currentUser.getAttribute("quantity");

// Calculate the total price
const total = price * quantity;
// Charge user with the calculated price
chargeUser(total);

// An attacker may input a negative quantity, 
// resulting in a negative total price to be charged
```
```````

Output:
```
TODO
```