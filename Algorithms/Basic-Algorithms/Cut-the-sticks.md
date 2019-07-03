# Cut the sticks HackerRank Algorithm Solution

You can view the [Cut the sticks algorithm here](https://www.hackerrank.com/challenges/cut-the-sticks/problem).
___

18:53 -- We have a function *cutTheSticks* which has a single parameter *arr* which takes in an array of integers representing the lengths of our various sticks.

I've also defined a few additional variables *numberOfSticks*: initialized to the length of *arr*, *smallestStick*: initialized to **Infinity**, and *remainingSticks*: initialized to an empty array.
```
function cutTheSticks(arr) {
  let numberOfSticks = [arr.length];
  let smallestStick = Infinity;
  let remainingSticks = [];
}
```
18:58 -- Next, we use a for loop to iterate through all of the items in our array.

Within our first for loop we're going to update the value of *smallestStick* to **Infinity**.

While this may seem somewhat redundant at this point (*smallestStick* was already set to the value of **Infinity** after all), you'll see later on why this step was necessary.
```
function cutTheSticks(arr) {
  let numberOfSticks = [arr.length];
  let smallestStick = Infinity;
  let remainingSticks = [];
  for (let i = 0; i < arr.length; i++) {
    smallestStick = Infinity;
  }
}
```
19:04 -- We've still got quite a ways to go. Now, we're going to create a second for loop.

This nested for loop will be used for determining the smallest stick in our array that *DOES NOT* have a value of 0.

Once we find a value of *arr[ii]* that is smaller than *smallestStick*, which if there are any positive integer values left in our array, they will be larger than *smallestStick* because *smallestStick* was just set to **Infinity** in the previous step, we'll then update *smallestStick* to the value of *arr[ii]*.

That was a loooong sentence, maybe it'll be more simple to just show you the code:
```
function cutTheSticks(arr) {
  let numberOfSticks = [arr.length];
  let smallestStick = Infinity;
  let remainingSticks = [];
  for (let i = 0; i < arr.length; i++) {
    smallestStick = Infinity;

    for (let ii = 0; ii < arr.length; ii++) {
      if (arr[ii] < smallestStick && arr[ii] > 0) {
        smallestStick = arr[ii]
      }
    }
  }
}
```
19:11 -- Now, we're going to need a third loop. Our final loop will iterate through our array, subtracting the value of *smallestStick* from each of our array items.

Then, if a given array item's value is larger than 0, we'll push that array item to *remainingSticks*.

After breaking out of our final loop, we have a conditional statement that says,
> if the length of our *remainingSticks* array is greater than 0, we'll push the length of *remainingSticks* to *numberofSticks*, update the value of *remainingSticks* to an empty array (and then continue through our various loops once again).

Otherwise, we'll return *numberOfSticks* as our solution to this algorithm!

```
function cutTheSticks(arr) {
  let numberOfSticks = [arr.length];
  let smallestStick = Infinity;
  let remainingSticks = [];
  for (let i = 0; i < arr.length; i++) {
    smallestStick = Infinity;

    for (let ii = 0; ii < arr.length; ii++) {
      if (arr[ii] < smallestStick && arr[ii] > 0) {
        smallestStick = arr[ii]
      }
    }
  for (let j = 0; j < arr.length; j++) {
    arr[j]-= smallestStick
    if (arr[j] > 0) {
      remainingSticks.push(arr[j])
    } 
  }
    if (remainingSticks.length > 0) {
    numberOfSticks.push(remainingSticks.length)
    }
    else {
      return (numberOfSticks)
    }
        remainingSticks = []
  }
}
```
I was quite surprised this algorithm's difficulty level was rated as 'easy' and not 'medium'.

In any case, way to stick with it. Now that you've read my solution, try to solve this algorithm on your own. You can do it! :D