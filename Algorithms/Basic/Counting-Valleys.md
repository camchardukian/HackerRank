# Counting Valleys HackerRank Algorithm Solution

You can find the [Counting Valleys
 algorithm here](https://www.hackerrank.com/challenges/counting-valleys/problem).

21:48 -- Let's understand what's going on here.

21:49 -- First we define a function *countingValleys()* that has two parameters *n* and *s*. *n* is an integer that represents how many steps Gary takes throughout his hike. *s* is a string of characters that describes  Gary's path and when he took steps upward or downwards.
```
function countingValleys(n, s) {

}
```
21:53 -- Moving forward, we can opt to set our string *s* equal to the results of s.toUpperCase(). This enables us to not have to worry about whether a user incorrectly passed lowercase characters to *s*.

We also need to initialize a few variables to 0. *valleyCount* which represents how many valleys Gary walked through, and *currentPosition* which represents Gary's current position in regards to whether he is at, below, or above sea level.

Finally, we're going to add a for loop to loop through each of Gary's steps (we'll build upon this in the next step.)
```
function countingValleys(n, s) {
s = s.toUpperCase();
let valleyCount = 0;
let currentPosition = 0;
for (let i = 0; i < n; i++) {
}
}
```
21:57 -- The only thing we need to do now is add some conditional logic. If Gary's current position is one unit below sealevel (-1) and he walks upwards ('U'), we'll increment *currentPosition* and *valleyCount* by one.

If Gary walks upwards but he is not currently one unit below sealevel, we'll merely increment his *currentPosition* by one.

Likewise, is Gary walks downward we'll decrement his *currentPosition* by one.

Else, we ran into some kind of error along the way and we'll log error to the console.

Finally, after we eventually break out of our for loop we'll return *valleyCount* as our solution to this algorithm.

```
function countingValleys(n, s) {
s = s.toUpperCase();
let valleyCount = 0;
let currentPosition = 0;
for (let i = 0; i < n; i++) {
  if (currentPosition === -1 && s[i] === 'U') {
    currentPosition+=1
    valleyCount+=1
  }
 else if (s[i] === 'U') {
    currentPosition+=1
  }
  else if (s[i] === 'D') {
    currentPosition-=1
  }
  else {
    console.log("error")
  }
}
return valleyCount
}
```

Hope you found this guide useful. Cheers!