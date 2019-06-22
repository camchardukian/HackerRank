# Equalize the Array HackerRank Algorithm Solution

You can view the [Equalize the Array algorithm here](https://www.hackerrank.com/challenges/equality-in-a-array/problem).
___

20:36 -- Let's discuss our solution. We have a function *equalizeArray* which has a single parameter *arr* which takes in an array of integers.

I've also created two variables: *currentFrequency*, and *highestOccurenceCount*, both initialized with a value of 1.

Here's our basic setup:
```
function equalizeArray(arr) {
let currentFrequency = 1;
let highestOccurenceCount = 1;
 }
```
20:40 -- Next, we're going to use a for loop to iterate through all of the items in our array. We're also going to update the value of *currentFrequency* to 1.

This is because we're later going to modify the value of *currentFrequency* in our upcoming nested for loop. But... we want the value of *currentFrequency* to equal 1 before we enter our nested for loop each time.

Thus, we need to update the value of *currentFrequency* to 1 with each iteration of our outer for loop:
```
function equalizeArray(arr) {
let currentFrequency = 1;
let highestOccurenceCount = 1;

for (let i = 0; i < arr.length - 1; i++) {
  currentFrequency = 1
 }
}
```
20:45 -- As I mentioned earlier, we're now going to need a nested for loop. The role of this inner for loop is to count how many times a particular item occurs within our array.

Each time an item occurs, we'll increment the value of *currentFrequency* by one. 

After we eventually break out of our nested for loop, we'll then reach an if statement. This if statement says that if *currentFrequency* or the number of times our current item has occured, if that is greater than *highestOccurenceCount* or the greatest number of times any single item (excluding the current item) thus far has occured, we'll then set the value of *highestOccurenceCount* to the value of *currentFrequency*.
```
function equalizeArray(arr) {
let currentFrequency = 1;
let highestOccurenceCount = 1;

for (let i = 0; i < arr.length - 1; i++) {
  currentFrequency = 1
  for (let ii = i + 1; ii < arr.length; ii++) {
    if (arr[i] === arr[ii]) {
      currentFrequency+=1
    }
  }
  if (currentFrequency > highestOccurenceCount) {
    highestOccurenceCount = currentFrequency;
  }
}
```
20:51 -- We'll continually run through both of our loops as long as *i* is less than arr.length - 1. When that stops being the case, however, we'll break out of our outer for loop and return (arr.length - highestOccurenceCount) as our solution to this algorithm!

The reasoning behind this logic, is that if we have some list of numbers and we want to make deletions until all of the numbers are the same, we know that the only number we won't be deleting is the number that occured most often.

For example:
> [0, 1, 1, 2]

In the above array of numbers, we have 4 numbers. Or in other words, our array's length has a value of 4.

In this array, our most frequently occuring number is 1. This number occurs two times. We know that we won't be deleting the ones from our array, because they are value that occurs most frequently.

We do know, however, that we will be deleting every other item in our array. Thus, if we take the number of items in our array (4 items), minus the number of times our most frequently item occurs (1 occurs two times), that will equal the number of deletions we must perform in order to have a new array that consists of only our most frequently occuring value!

Here's our final solution to this algorithm:
```
function equalizeArray(arr) {
let currentFrequency = 1;
let highestOccurenceCount = 1;

for (let i = 0; i < arr.length - 1; i++) {
  currentFrequency = 1
  for (let ii = i + 1; ii < arr.length; ii++) {
    if (arr[i] === arr[ii]) {
      currentFrequency+=1
    }
   }
  if (currentFrequency > highestOccurenceCount) {
    highestOccurenceCount = currentFrequency;
  }
 } 
  return (arr.length - highestOccurenceCount)
}
```
I hope my explanation of our solution made sense to you. If you're having a difficult time catching on, don't worry.

A moderate amount of discomfort experienced while programming, a feeling that you're being stretched... doesn't mean your stupid. It just means you're learning.

Keep putting the time in everyday, and gradually over time things will begin to "click" more and more quickly! :D