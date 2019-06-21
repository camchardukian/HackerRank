# CamelCase HackerRank Algorithm Solution

You can view the [CamelCase algorithm here](https://www.hackerrank.com/challenges/camelcase/problem).
___

13:56 -- This algorithm is pretty simple. We have a function *camelcase* which has a single parameter *s*, which takes in a string of multiple words "mashed" together in CamelCase fashion.

Our job is given *s*, to determine how many words are in our string *s*.

Here's our basic function setup:
```
function camelcase(s) {

}
```
13:58 -- My logic in solving this problem was pretty simple. While the initial word begins with a lowercase letter, all of the succeeding words in our string *s* will begin with capital letters.

For that reason, my thinking was that we should create a variable *counter* and initialize said variable to 1.

*Why 1?* Because any given string passed to *s* will always have its first word begin with a lower case letter. By initializing *counter* to 1, we are accounting for this fact.

Moving forward, we're going to create a loop that iterates through every character in our string *s*. Any time we encounter a capital letter, we know that a new word has begun, and thus we should increment *counter* by 1.

In other words:
```
if (s[i].toUpperCase() === s[i]) {
    counter+=1
  }
```
After we've finished iterating through every character in our string *s*, we can return our variable *counter* as our solution to this algorithm!

Here's my finished solution I submitted successfully to HackerRank:
```
function camelcase(s) {
  let counter = 1;
for (let i = 0; i < s.length; i++) {
  if (s[i].toUpperCase() === s[i]) {
    counter+=1
  }
}
return counter
}
```
Thanks for following along. I hope you found my instructions useful! :D