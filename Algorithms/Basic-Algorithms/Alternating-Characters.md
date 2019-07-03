# Alternating Characters HackerRank Algorithm Solution

You can view the [Alternating Characters algorithm on HackerRank here](https://www.hackerrank.com/challenges/alternating-characters/problem).
___


17:13 -- It looks like we have a function *alternatingCharacters* that has a single parameter *s* which takes in a string.

Our string will be a series of  consecutive 'A' and 'B' characters.

We will then "delete" characters from our string such that we no longer have any 'A' characters that are "touching" any other 'A' characters nor any 'B' characters that are touching any other 'B' characters.

Our goal is to determine the minimum number of deletions required to achieve the above.

Here's our basic function setup:
```
function alternatingCharacters(s) {

}
```
17:15 -- My logic for solving this algorithm was pretty simple. The first thing I did was declare a variable *counter*.

I initialized this variable to **0**. The purpose of *counter* is to act as a location where we can store the value of how many deletions we need to make.

Anytime we see that a deletion needs to occur, we can increment the value of *counter* by 1.
```
function alternatingCharacters(s) {
  let counter = 0;
    counter+=1
}
```
17:16 -- Of course, we're not finished yet. Right now our code is somewhat nonsensical. We initialize *counter* to 0, and increment it for seemingly no reason.

We need to define some kind of criteria so that we know when a deletion needs to occur.

My thinking was that a deletion will need to occur anytime our first character is equal to the character immediately after it.

For example, let's say we're given this string:

> ABBABAA

We would look at the 1st character 'A', and then look at the character following it (the 2nd character in our string) 'B'. Since they are not the same, we'd simply proceed to the next pair of characters.

Is the 2nd character in our string 'B' equal to the 3rd character in our string 'B'? YES! Because this is true, we know we'd need to make a deletion.

Thus, we'd increment *counter* by 1, and we can imagine the string as now being:

> AB(the 2nd B is deleted)ABAA ------ Or if it's easier for you to see: ABABAA

We'd then repeat our process until we reaching the 2nd to last character with the final character in our string.

It isn't necessary of course to compare the final character in our string with the character that follows it because no such character exists. Thus, we'd simply be comparing the final character with undefined with is simply a waste of resources.

Thus, we go through all of our looping incrementing *counter* as necessary. When we eventually break out of our loop, we can return *counter* as our solution to this algorithm!
```
function alternatingCharacters(s) {
  let counter = 0;
for (let i = 0; i < s.length - 1; i++) {
  if (s[i] === s[i+1]) {
    counter +=1
  }
 }
return counter
}
```
17:26 -- Hopefully my explanation of my solution for this algorithm was clear to you. Good for you on reading through the entire explanation! :D