# The Electronics Shop HackerRank Algorithm Solution

You can find the [Electronics Shop
 algorithm here](https://www.hackerrank.com/challenges/electronics-shop/problem).

15:34 -- Let's break things down. First, we define a function *getMoneySpent* which has three parameters *keyboards*, *drives*, and *b*.

*keyboards* and *drives* have arrays passed to them that represent respectively the costs of the stores' various keyboards and USB drives.

*b* represents Monica's budget.

I've also defined a new variable *mostExpensiveCombo* which is an integer representing the costliest combination of keyboards and USB drives Monica could purchase.
```
function getMoneySpent(keyboards, drives, b) {
let mostExpensiveCombo = 0;
}
```
15:40 -- Now, the first thing we need to do is loop through all of the different keyboards. As we go through each item in the *keyboards* array, we'll use a nested for loop to also go through all of the items in the *drives* array.

The reason we're doing this is to evaluate every possible combination of keyboards and USB drives.
```
function getMoneySpent(keyboards, drives, b) {
let mostExpensiveCombo = 0;

for (let i = 0; i < keyboards.length; i++) {

for (let ii = 0; ii < drives.length; ii++) {
}
}
}
```
15:43 -- Of course, we also need to add some logic. Our logic is as follows... If the cost of the given keyboard and USB drive is greater than the current value of *mostExpensiveCombo*, AND less than or equal to Monica's budget *b*, we will set the value of *mostExpensiveCombo* equal to the sum cost of the keyboard and USB drive we are currently looking at.

After going through every possible combination, we will then break out of our loops and utilize a return statement.

That return statement utilizes a ternary operator with the following logic:
> If the value of *mostExpensiveCombo* is greater than 0, it means Monica is capable of buying both a keyboard and a USB drive and we can return the value of *mostExpensiveCombo*. If not, it means Monica's budget wasn't large enough to purchase both a keyboard and a USB drive and we will instead return -1 as requested in this algorithm's explanation.

```
function getMoneySpent(keyboards, drives, b) {
let mostExpensiveCombo = 0;

for (let i = 0; i < keyboards.length; i++) {

for (let ii = 0; ii < drives.length; ii++) {
  if(keyboards[i] + drives[ii] > mostExpensiveCombo && keyboards[i] + drives[ii] <= b) {
    mostExpensiveCombo = keyboards[i] + drives[ii]
  } 
}
}
return (mostExpensiveCombo > 0 ? mostExpensiveCombo : -1)
}
```
We're finished!