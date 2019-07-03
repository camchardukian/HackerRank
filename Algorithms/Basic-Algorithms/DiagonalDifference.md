# Diagonal Difference HackerRank Algorithm Solution

You can view the [Diagonal Difference algorithm here](https://www.hackerrank.com/challenges/diagonal-difference/problem).
___


15:58 -- We have a function *diagonalDifference* that has a parameter *arr*. LISTEN UP. Though the problem orientation page states that *arr* is an array of integers, it's important to note that *arr* is actually a 2-d array of integers.

I wasted several hours trying to solve this problem, having my solution work perfectly on repl.it, but having it fail on HackerRank countless times.

Eventually after playing around with the user tests on HackerRank, I realized that they gave us a 2-d array, and not a standard array of integers.

With that being said, here's our basic function setup:
```
function diagonalDifference(arr) {

}
```
16:01 -- Next, I've also defined a few additional variables: *primary* and *secondary* initialized to **0**, and a variable *result* declared but not given any initial value.
```
function diagonalDifference(arr) {
let primary = 0;
let secondary = 0;
let result;
}
```
16:04 -- Now that we've got our function setup and declared all of our variables, we're going to create a for loop. Our first for loop will be used to increment *primary* by the values that make up a line drawn through the primary diagonal of any square of integers.

Our second for loop increments *secondary* by the values that make up a line drawn through the secondary diagonal of any square of integers.
```
function diagonalDifference(arr) {
let primary = 0;
let secondary = 0;
let result;
for (let i = 0; i < arr.length; i++) {
  primary+=arr[i][i]
}
for (let i = 0; i < arr.length; i++) {
  secondary+= arr[i][arr.length-i-1]
}
```
16:08 -- Now that the sum of all of our values in the two diagonal lines drawn through a square are stored in either *primary* or *secondary*, we can then return the absolute value of *primary* minus *secondary* as our solution to this algorithm!
```
function diagonalDifference(arr) {
let primary = 0;
let secondary = 0;
let result;
for (let i = 0; i < arr.length; i++) {
  primary+=arr[i][i]
}
for (let i = 0; i < arr.length; i++) {
  secondary+= arr[i][arr.length-i-1]
}
return Math.abs(primary-secondary)
}
```
16:10 -- If you found this algorithm frustrating or confusing, you're not alone.

This may be my first month solving algorithms on HackerRank (June 2019), but of the 30+ algorithms I've solved thus far, this is the only algorithm that made me so frustrated I had to store it away for a couple weeks before coming back to it.

In retrospect, this algorithm wouldn't have been so frustrating if the instructions were written more clearly, or... taking personal responsibility -- I could have maintained my composure and solved this algorithm more quickly by ensuring I'd understood what the author was looking for, even if their explanation was unclear to me and my only real way of understanding the problem was playing with the console and various user tests.

At the very least, I've learned a lesson and if in the future my code isn't working the way I expect, I'll go straight to the user tests and play with the console to see if the inputs my function is receiving are in a different format than I expected.