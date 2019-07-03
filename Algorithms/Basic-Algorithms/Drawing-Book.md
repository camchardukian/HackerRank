# Drawing Book HackerRank Algorithm Solution

You can view the [Drawing Book algorithm here](https://www.hackerrank.com/challenges/drawing-book/problem).
___

12:09 -- Let's talk about how to solve this algorithm. First, we have a function *pageCount* that has two parameters *n*: an integer representing the total numbers of pages in the book, and *p*: an integer representing the page number the teacher wants Brie to open her book to.

I've also defined a few additional variables: *frontToBack*: initialized to 0, *backToFront*: initialized to 0, and *result*: declared, but not given any initial value.
```
function pageCount(n, p) {
let frontToBack = 0;
let backToFront = 0;
let result;
}
```
12:13 -- Now that we've got the skeleton of our function setup, the next thing we need is a for loop. We're going to use a for loop to count how many pages it would take Brie to reach *p* if she starts at page 1.

Each time we go through our loop, we'll increment *i* by two (because turning the page from 1 doesn't just give us 2, but it gives us 2-3, and then 4-5, then 6-7, and so on).

With that being said we will NOT increment *frontToBack* by two because this variable's intent isn't to count how many total pages we've read or moved past.

This variable's intent is to simply count how many times we touched the bottom right corner of the book to turn the page. For that reason, we're only going to increment *frontToBack* by 1 each time through the loop.
```
function pageCount(n, p) {
let frontToBack = 0;
let backToFront = 0;
let result;
for (let i = 1; i < p; i+=2) {
  frontToBack+=1
 }
}
```
12:18 -- Next, we also need to evaluate how many page turns we would need to reach the desired page if we were starting from the end of the book.

For that reason, we'll create another for loop. This for loop will have have a variable *i* that's initialized to *n* because we want our initial page or starting point to be the end of the book.

We'll continue turning the page as long as *i* is greater than *p*, decrementing i by 2 with each iteration. However, if our *i* is an odd number, and *i* - 1 equals *p*, we'll know that we have arrived to the proper page and no longer need to increment *backToFront*.

Unless the above holds true, we'll increment *backToFront* each time we go through our loop.
```
function pageCount(n, p) {
let frontToBack = 0;
let backToFront = 0;
let result;
for (let i = 1; i < p; i+=2) {
  frontToBack+=1
}
for (let i = n; i > p; i-=2 ) {
  if (i % 2 === 1 && i - 1 === p) {
  }
  else {
    backToFront+=1
  }
 }
}
```
12:26 -- Finally, we will use a ternary operator to set the value of our variable *result*. If *frontToBack* is greater than *backToFront*, we'll set *result* equal to *backToFront* as that would be the method of arriving at page *p* with the fewest number of page turns.

Otherwise, we'll set *result* equal to *frontToBack*.

Regardless of how our ternary operator evaluates, when it is finished evaluating we'll return *result* as our solution to this algorithm!
```
function pageCount(n, p) {
let frontToBack = 0;
let backToFront = 0;
let result;
for (let i = 1; i < p; i+=2) {
  frontToBack+=1
}
for (let i = n; i > p; i-=2 ) {
  if (i % 2 === 1 && i - 1 === p) {
  }
  else {
    backToFront+=1
  }
}

frontToBack > backToFront? result = backToFront : result = frontToBack;

return result
}
```
I can't believe this algorithm was only worth 10 points. It was a bit of a handful :p. But, if you made it to the end, excellent job on your part!