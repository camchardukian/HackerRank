# Migratory Birds HackerRank Algorithm Solution

You can view the [Migratory Birds algorithm on HackerRank here](https://www.hackerrank.com/challenges/migratory-birds/problem).
___


12:13 -- We have been asked to study the population of various birds migrating across the continent. Each type of bird will be identified by an integer value.

When we see a certain type of bird, it will be added to our array of "spotted birds".

Our goal is to use our function *migratoryBirds*, and its parameter *arr* (which is an array of integers representing the types of birds sighted), to output the most commonly sighted bird.

In the scenario that two or more types of birds are equally common, we'll choose the type of bird with the smallest ID number.

Here's our initial setup:
```
function migratoryBirds(arr) {

}
```
12:19 -- We need a few variables:

*mostSightedCount* is initialized to 1 because we'd need to see a bird type at least once in order for it to be the most commonly sighted bird.

*currentCount* is initialized to 0 because until we see the bird, we can't assume that it exists.

*mostSightedBirdType* is declared but not initialized to any value.
```
function migratoryBirds(arr) {
let mostSightedCount = 1;
let currentCount = 0;
let mostSightedBirdType;
}
```
12:23 -- Now, we need a for loop that'll iterate through all of the possible bird types. This algorithm explicitly stated that there are only 5 bird types being studied.

Thus, our first for loop will simply continue running with *i* starting at 1, all the way until *i* is finished with 5.

At the beginning of our for loop, we'll also want to update the value of *currentCount* to 0.

We do this each time we start counting the number of times a bird type has occured, we want to start counting from 0.
```
function migratoryBirds(arr) {
let mostSightedCount = 1;
let currentCount = 0;
let mostSightedBirdType;

for (let i = 1; i <= 5; i++) {
  currentCount = 0
  }
}
```
12:27 -- Unfortunately, a single for loop isn't enough. We also need another for loop. This nested for loop will iterate through all of the numbers passed to *arr*.

In interating through *arr*, we'll see if the particular bird seen is equal to the type of bird we're looking for *i*.

If so, we'll increment *currentCount* by 1. We'll loop all the way through and at the end, *currentCount* will be equal to the number of times we saw a particular type of bird.
```
function migratoryBirds(arr) {
let mostSightedCount = 1;
let currentCount = 0;
let mostSightedBirdType;

for (let i = 1; i <= 5; i++) {
  currentCount = 0
  for (let ii = 0; ii < arr.length; ii++) {
    if (arr[ii] === i) {
      currentCount+=1
    }
  }
 }
}
```
12:30 -- It's important that we do something with the value inside of *currentCount*. If we don't, we'll lose it because the value of *currentCount* is reset to 0 with each iteration of our outer for loop.

Thus, after we break out of our nested for loop, we'll evaluate whether the value of *currentCount* is greater than the value of *mostSightedCount*.

If so, we'll know that the current bird type we're evaluating is the most common (at least thus far).

Thus, we can set the value of *mostSightedBirdType* to *i*.

We'll also set the value of *mostSightedCount* equal to *currentCount*.

If we saw bird type 2 eleven times for example, this step would help us ensure that we'd only classify future bird types as the **SOLE** most commonly sighted type if we saw them more than 11 times.
```
function migratoryBirds(arr) {
let mostSightedCount = 1;
let currentCount = 0;
let mostSightedBirdType;

for (let i = 1; i <= 5; i++) {
  currentCount = 0
  for (let ii = 0; ii < arr.length; ii++) {
    if (arr[ii] === i) {
      currentCount+=1
    }
  }
  if (currentCount > mostSightedCount) {
    mostSightedBirdType = i
    mostSightedCount = currentCount
  }
 }
}
```
12:34 -- Notice how we bolded the word 'SOLE'. This is because continuing with the previous example, we may see more than one bird type 11 times.

If we see bird type 2 eleven times, but also see bird type 4 eleven times, we should set the value of *mostSightedBirdType* equal to the bird type of a lower integer value (the algorithm instructions specified this).

If the value of *i* is less than *mostSightedBirdType*, we'll update the value of *mostSightedBirdType* to equal *i*.

Otherwise, we'll keep everything as is.

Eventually, we'll break out of all of our loops and be able to return *mostSightedBirdType* as our solution to this algorithm!
```
function migratoryBirds(arr) {
let mostSightedCount = 1;
let currentCount = 0;
let mostSightedBirdType;

for (let i = 1; i <= 5; i++) {
  currentCount = 0
  for (let ii = 0; ii < arr.length; ii++) {
    if (arr[ii] === i) {
      currentCount+=1
    }
  }
  if (currentCount > mostSightedCount) {
    mostSightedBirdType = i
    mostSightedCount = currentCount
  }
  else if (currentCount === mostSightedCount) {
    if (i < mostSightedBirdType) {
      mostSightedBirdType = i
    }
  }
 }
 return mostSightedBirdType
}
```
12:52 -- This explanation was a bit long, but good for you for reading everything all the way to the end! :D