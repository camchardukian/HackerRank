# Birthday Chocolate HackerRank Algorithm Solution

You can find the [Birthday Chocolate algorithm here](https://www.hackerrank.com/challenges/the-birthday-bar/problem).

10:58 -- Let's explain this algorithm step-by-step. To start, we have a function *birthday* which has three parameters *s*, *d*, and *m*.

*s* is an array of integers representing the numbers printed on our squares of chocolate.

*d* is an integer representing Ron's birthday (which the sum of our chocolates must equal).

*m* is an integer representing Ron's birth month (which the length property of our result or "number of chocolates given" must match).
```
function birthday(s, d, m) {

}
```
11:01 -- Moving forward, I've also created a few variables. *approvedGroupCount* initialized to 0, *currentGroup* initialized to an empty array, and *counter* initialized to 0.
```
function birthday(s, d, m) {
let approvedGroupCount = 0;
let currentGroup = [];
let counter = 0;
}
```
11:05 -- Next, we use a for loop to loop through all of the values in our *s* array as long as (s.length - i ) is greater than or equal to m.

This piece of logic is important because it prevents unnecessary looping after we no longer have enough chocolate squares left to satisfy Lily's desire of giving Ron a number of chocolate squares equal to his birth month.

We also reset our current group to an empty array, push the value of *s[i]* to *currentGroup* and set *counter* equal to *s[i]*.

Some of these steps may seem unnecessary now, however, that's simply because we haven't yet implemented our nested for loop.
```
function birthday(s, d, m) {
let approvedGroupCount = 0;
let currentGroup = [];
let counter = 0;

for (let i = 0; i < s.length && (s.length - i) >= m ; i++) {
  currentGroup = [];
  currentGroup.push(s[i])
  counter = s[i];
```
11:10 -- Now, time for the nested for loop. Our nested for loop will start at the chocolate bar after the current bar (let ii = i + 1), and will continue to run as long as we still have chocolate bars (ii < s.length) AND the number of chocolate bars we currently have (the ones we're considering giving to Ron) is less than Ron's birth month ((currentGroup.length < m)), with *ii* being incremented by one each time through the loop.

With each iteration of the loop, we'll increment counter by *s[ii]* and push *s[ii]* to our *currentGroup* array.
```
function birthday(s, d, m) {
let approvedGroupCount = 0;
let currentGroup = [];
let counter = 0;

for (let i = 0; i < s.length && (s.length - i) >= m ; i++) {
  currentGroup = [];
  currentGroup.push(s[i])
  counter = s[i];
 for (let ii = i + 1; ii < s.length && currentGroup.length < m; ii++) {
   counter+=s[ii];
   currentGroup.push(s[ii])
 }
}
```
11:18 -- Finally, after we break out of our nested for loop, we'll evaluate whether *counter* is equal to *d*, and *currentGroup.length* is equal to m.

If so, we know that the given combination of chocolate bars is valid, and we increment *approvedGroupCount* by one.

After that, we'll go back to our previous loops and repeat the process. After all of our looping has eventually finished, we'll return *approvedGroupCount* as our solution to this algorithm.
```
function birthday(s, d, m) {
let approvedGroupCount = 0;
let currentGroup = [];
let counter = 0;

for (let i = 0; i < s.length && (s.length - i) >= m ; i++) {
  currentGroup = [];
  currentGroup.push(s[i])
  counter = s[i];
 for (let ii = i + 1; ii < s.length && currentGroup.length < m; ii++) {
   counter+=s[ii];
   currentGroup.push(s[ii])
 }
 if (counter === d && currentGroup.length === m) {
   approvedGroupCount+=1
 }
}
return approvedGroupCount
}
```
Wow, that was a dense explanation! Well done for following along! :D