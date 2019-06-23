# Repeated String HackerRank Algorithm Solution

You can view the [Repeated String algorithm here](https://www.hackerrank.com/challenges/repeated-string/problem).
___

17:41 -- We have a function *repeatedString* that has two parameters: *s*: a string of lowercase English letters that a girl named Lilah has repeated an infinite amount of times, and *n*: an integer representing the first *n* number of characters in Lilah's string that are to be evaluated.

Our job is to figure out how many times the letter 'a' occurs in the first *n* characters of Lilah's string.

Here's our basic setup:
```
function repeatedString(s, n) {

}
```
17:46 -- The next thing we'll need to do is define a few variables. Those variables are *initialLowerCaseACount* initialized to 0, *remainderACount* initialized to 0, and *numberOfFullReps* initialized to the value of:
> Math.floor(n / s.length) 

To quickly go over the variables, *initialLowerCaseACount* is where we'll eventually store the value of how many times 'a' occured in the original string *s*.

This variable is NOT where we'll be storing our final result for this algorithm. If Lilah's infinitely repeated string was 'anapple', it wouldn't matter how many characters we were evaluating AKA what value was passed to *n*.

The value of *initialLowerCaseACount* in this example would be 2, because in the basic string 'anapple', the letter 'a' occurs two times.

*numberOfFullReps* counts how many times we're going to evaluate the entire basic string passed to *s*. If our string passed to *s* was apple and our number passed to *n* was 11, the entire string we would be repeating would be:
>'appleapplea'

In this example, our original string *s* is repeated in full 2 times, and it has one extra letter we're evaluating. Thus, *numberOfFullReps* would have a value of 2 in this scenario because the basic string *s* is repeated in full two times.

*remainderACount* in this scenario would have its value set to 1, because the letter 'a' occurs 1 time in the sub-section of the string not repeated in full and thus not evaluated by *numberOfFullReps*.
```
function repeatedString(s, n) {
let numberOfFullReps = Math.floor(n / s.length);
let initialLowerCaseACount = 0;
let remainderACount = 0;
}
```
Now that we've spent half a century explaining our variables, let's get to the rest of the function ;).

After our initial variable declaration and assignment phase, the next thing we're going to do is run a for loop. This for loop will iterate over all of the characters in *s*.

With each iteration of the loop, we will check to see if the current character *s[i]* is equivalent to 'a'. If so, we'll increment our variable *initialLowerCaseACount* by one.

After this loop finishes running, the value of *initialLowerCaseACount* will be equal to the number of times 'a' occurs in the basic string *s*.
```
function repeatedString(s, n) {
let numberOfFullReps = Math.floor(n / s.length);
let initialLowerCaseACount = 0;
let remainderACount = 0;
for (let i = 0; i < s.length; i++) {
  if (s[i] === 'a') {
initialLowerCaseACount+=1
  }
 }
} 
```
18:06 -- Moving forward, after we break out of our first for loop, we'll then come across an if statement. This if statement states that if *n* divided by *s.length* has a remainder of 0, we'll return *numberOfFullReps* times *initialLowerCaseACount* as our solution to this algorithm!
```
function repeatedString(s, n) {
let numberOfFullReps = Math.floor(n / s.length);
let initialLowerCaseACount = 0;
let remainderACount = 0;
for (let i = 0; i < s.length; i++) {
  if (s[i] === 'a') {
initialLowerCaseACount+=1
  }
 }

if (n % s.length === 0) {
  return (numberOfFullReps*initialLowerCaseACount)
 }
}
```
18:08 -- Of course, if *n* divided by *s.length* did have some remainder, the above would NOT be our solution to our algoritm and we'd then proceed to our else clause of our if statement.

Our else clause initializes a variable *i* to 0. It then has a while loop that will continue running for as long as *i* is less than the remainder produced by dividing *n* by *s.length*.

In simpler terms, our loop will continue running for as long as necessary to check any partial part of our *s* string that was not repeated in full, and thus could not be evaluated under *numberOfFullReps*.

With each iteration of our loop we'll increment our variable *i* after seeing whether our current character *s[i]* is equal to the string 'a'. If so, we'll increment *remainderACount* by 1, and run our for loop again if our while condition still holds true.

When we eventually break out of our for loop, we'll return (numberOfFullReps*initialLowerCaseACount) + remainderACount) as our solution to this algorithm!
```
function repeatedString(s, n) {
let numberOfFullReps = Math.floor(n / s.length);
let initialLowerCaseACount = 0;
let remainderACount = 0;
for (let i = 0; i < s.length; i++) {
  if (s[i] === 'a') {
initialLowerCaseACount+=1
  }
 }

if (n % s.length === 0) {
  return (numberOfFullReps*initialLowerCaseACount)
 }
else {
  let i = 0
  while (i < n % s.length) {
    if (s[i] === 'a') {
      remainderACount+=1
    }
    i++
  }
return ((numberOfFullReps*initialLowerCaseACount) + remainderACount)
 }
}
```
18:17 -- The explanation for this problem was a bit dense. I hope you're still with me. If so, excellent job at persisting despite this problem's level of complexity! :D