# Lonely Integer HackerRank Algorithm Solution

You can view the [Lonely Integer algorithm here](https://www.hackerrank.com/challenges/lonely-integer/problem).
___

23:17 -- In this algorithm we have a function *lonelyinteger* which has a single parameter *a* which takes in an array of integers.

Our job is to look at all of the integers in the array, and identify which single integer is 'lonely' or in other words, which integer has a value that is not matched by any other integer in the array.

Here's our basic setup:
```
function lonelyinteger(a) {
}
```
23:21 -- Next, I'd like to take the opportunity to declare a couple variables variables:

* *lonelyChecker* -- A boolean which we'll use to hold the value of whether an investigated integer is lonely or not.
* *shiftedArray* -- An array of integers that we shift values to from our array *a*

Of the above variables *lonelyChecker* is initialized to **true**, and *shiftedArray* is initialized to an empty array.
```
function lonelyinteger(a) {
  let lonelyChecker = true;
  let shiftedArray = [];
}
```
23:26 -- Now, we're going to use a while loop to iterate through our array as long as it's length is less than 0.

Once our loop begins running, we'll check to see if *shiftedArray* has any instances of our current value (a[0]). We do this of course, using the indexOf() method.

If *shiftedArray.indexOf(a[0])* does NOT equal negative, we'll know that somewhere in our array *shiftedArray*, we found an item that has a value equal to a[0]. Thus, we'd know the current item was NOT lonely.
```
function lonelyinteger(a) {
  let lonelyChecker = true;
  let shiftedArray = [];
while (a.length > 0) {
  
  if (shiftedArray.indexOf(a[0]) !== -1) {
  }
 }
}
```
23:32 -- Of course, there are sure to be many instances in which *shiftedArray* doesn't contain any items equivalent to a[0]. In this case, we'll then proceed to our else statement.

Our else statement begins with us updating the value of *lonelyChecker* to true. We have to update this value to true as just because one of our previous integers may have had a matching pair and thus *lonelyChecker* may have been set to false at some point... We need to evaluate each integer as its own case.

In other words, we're looking at the current item in our *a* array as if it is "guilty" of being lonely, and it's up to the item itself to prove it's not guilty.

However, as long as we have array items and *lonelyChecker* is set to true, we'll evaluate whether our current item a[0] is equal to the next value in the array a[i+1]. If so, we'll set the value of *lonelyChecker* to false.

Then if our array still has more items remaining, we'll increment our variable *i* by one. If *lonelyChecker* is set to false, we'll do nothing.

If *lonelyChecker* is true, however, we'll then see if our current item a[0] is equal to the item that is positioned two spots behind our current item a[i+1] (with *i* now having a value of 1 making it equivalent to a[i+2]).

If the two are equal, we'll set *lonelyChecker* to false. Otherwise, we'll continue looping through this array until we've gone through all of the items.
```
function lonelyinteger(a) {
  let lonelyChecker = true;
  let shiftedArray = [];
while (a.length > 0) {
  if (shiftedArray.indexOf(a[0]) !== -1) {
  }
  else {
    lonelyChecker = true
    for (let i = 0; i < a.length; i++) {
      if (lonelyChecker === true) {
      if (a[0] === a[i+1]) {
        lonelyChecker = false
      }
  
      }
    }
  }
 }
}
```
23:49 -- If *lonelyChecker* is set to true after we've gone broken out of our for loop, it means we were unable to find any item that matched the value of our current item.

If this is the case, we'll return a[0] as our solution to the algorithm!

If this is not the case, however, we'll shift the first value off of our *a* array and onto our *shiftedArray* and go back to the beginning of our while loop.

The reason we're using the shift() method in this algorithm solution is that doing so reduces the amount of loops we need to write.

This allows us to write cleaner code and in theory, any looping the indexOf() method may do theoretically should offer better performance than the loops we write because it is a native method of JavaScript.

Let's cut all this blibber blabber though and show you the final solution!
```
function lonelyinteger(a) {
  let lonelyChecker = true;
  let shiftedArray = [];
while (a.length > 0) {
  if (shiftedArray.indexOf(a[0]) !== -1) {
  }
  else {
    lonelyChecker = true
    for (let i = 0; i < a.length; i++) {
      if (lonelyChecker === true) {
      if (a[0] === a[i+1]) {
        lonelyChecker = false
      }
  
      }
    }
    if (lonelyChecker === true) {
      return a[0]
    }
  }
    shiftedArray.push(a.shift());
 }
}
```