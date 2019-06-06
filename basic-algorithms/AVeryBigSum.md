# A Very Big Sum

This problem is actually super simple. We're just given an array of numbers and we need to add all of them together. 

Each number is a separate value in the array. We don't have to worry about dealing with an array that only has one value, and forcing that array to have multiple values.

In other words, the solution is fairly simple:
```
function aVeryBigSum(ar) {
  let sum = 0
for (let i = 0; i < ar.length; i++) {
  sum += ar[i]
}
return sum
}
```
If you're still lost, don't worry. Let's break it down.

\#1 --  We're given an empty function.
```
function aVeryBigSum(ar) { }
```
\#2 -- We create a sum varable and initialize it to 0.
```
function aVeryBigSum(ar) {
    let sum = 0;
}
```
\#3 -- We write a for loop. We initialize 'i' to 0, tell the for loop to continue running as long as 'i' is less than the length or our array, and each time we iterate (go through the loop) we add one to 'i'.
```
function aVeryBigSum(ar) {
    let sum = 0;
    for (let i = 0; i < ar.length; i++) {

    }
}
```
\#4 -- Now, we need to actually do something within our for loop. We want to add each value in our arr to our sum variable. We can do that using +=. We can access each individual array item using *ar[i]*.
```
function aVeryBigSum(ar) {
    let sum = 0;
    for (let i = 0; i < ar.length; i++) {
 sum+= ar[i] 
    }
}
```
\#5 -- Finally, we need to make sure we actually save all of the information that we're putting into our sum variable. Currently we're adding all of our array items to our sum, but we're not actually doing anything with that data.

We can actually save and do something with the information we've collected by returning our sum after our for loop has finished running, but before we exit our aVeryBigSum function.
```
function aVeryBigSum(ar) {
    let sum = 0
    for (let i = 0; i < ar.length; i++) {
        sum += ar[i]
    }
    return sum
}
```
I hope you found all of this useful! :D