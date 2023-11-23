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

- ChatGPT:
```````
To fix the bug and prevent the possibility of a negative total price, you can add a check to ensure that the quantity is a positive number before calculating the total price. Here's an updated version of the code:

```js
// Set price per item
const price = 20.00;
// Get the quantity of items
const quantity = currentUser.getAttribute("quantity");

// Check if quantity is a positive number
if (quantity >= 0) {
  // Calculate the total price
  const total = price * quantity;
  // Charge user with the calculated price
  chargeUser(total);
} else {
  // Handle the case where the quantity is negative
  console.error("Invalid quantity. Please enter a positive number.");
}
```
```````

- Bard:
``````
To prevent the issue of a negative total price, modify the code to validate the quantity input before calculating the total price:

```js
// Set price per item
const price = 20.00;

// Get and validate the quantity
let quantity = parseInt(currentUser.getAttribute("quantity"));
if (isNaN(quantity) || quantity < 0) {
  // Invalid quantity input, handle accordingly
  alert("Invalid quantity input. Please enter a positive number.");
  return; // Exit the function to prevent further processing
}

// Calculate the total price with the validated quantity
const total = price * quantity;

// Charge user with the calculated price
chargeUser(total);
```
``````