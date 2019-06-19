# Find Digits HackerRank Algorithm Solution

You can view the [Find Digits algorithm here](https://www.hackerrank.com/challenges/find-digits/problem).
___

14:44 -- We have a function *findDigits* that has a single parameter *n* which takes in an integer that represents the number we will perform division operations on.

I've also declared a few other variables: *divisorCount*: initialized to 0, *dividend* initialized to the value passed to *n*, and *divisors* initialized to the value of String(n).split("").

In other words, divisors will be set to the value of an array in which each item is an individual character taken from the integer passed to *n*.
```
function findDigits(n) {
let divisorCount = 0;
let dividend = n;
let divisors = String(n).split("");
}
```
14:56 -- Next, we'll use a for loop to go through each value in our *divisors* array. Then we have the logic that if our dividend is divisible by our divisor (*divisors[i]) without a remainder, we'll increment divisorCount by 1.

After we finishing iterating through our array we'll break out of our loop and return our variable *divisorCount* as our solution to this algorithm!
```
function findDigits(n) {
let divisorCount = 0;
let dividend = n;
let divisors = String(n).split("");
for (let i = 0; i < divisors.length; i++) {
  if (dividend % Number(divisors[i]) === 0) {
    divisorCount+=1
  }
}
return divisorCount
}
```
Nice job!