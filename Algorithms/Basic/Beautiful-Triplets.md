# Beautiful Triplets HackerRank Algorithm Solution

You can view the [Beautiful Triplets algorithm here](https://www.hackerrank.com/challenges/find-digits/problem).
___

23:32 -- We have a function *beautifulTriplets* that has two parameters *d* and *arr*. *d* is an integer that represents what we would define as a beautiful number. *arr* is an array of integers sorted in ascending order.

Our job is to look at *arr* and find all of the possible combinations of beautiful triplet numbers ([Click here](https://www.hackerrank.com/challenges/beautiful-triplets/problem), to go to this algorithm's page and read a more articulate and detailed problem definition).

Anyway, I've also defined an additional variable *beautifulTriplets* which is initialized to 0 and will be used to count the possible combinations of beautiful triplets.

Here's what our basic problem setup looks like:
```
function beautifulTriplets(d, arr) {
let beautifulTriplets = 0
```
23:37 -- Next, we have a for loop that we'll use to iterate through almost of the items in our array in reverse order.

The reason we don't want to loop over the first two items in our array *arr[0]* and *arr[1]*, is because we need at least three numbers to have a group of beautiful triplets.

Thus, iterating over these array items in our outer array would be redundant and a waste of resources.
```
function beautifulTriplets(d, arr) {
let beautifulTriplets = 0

for (let i = arr.length - 1; i >= 2; i--) {
 }
}
```
23:42 -- Next we have a second for loop. This for loop will also loop backwards through our array from largest numbers to smallest numbers. If at any point we find a number that is smaller than arr[i] and when said smaller number is subtracted from arr[i] also equals *d* or in other words:
> if (arr[i] - arr[ii] === d)

It means we're on the brink of possibly having a group of beautiful triplets, and that we also need a 3rd layer for loop (nested within our already nested 2nd layer for loop).

This 3rd layer for loop will also iterate through our array in reverse to see if we can find a number that is smaller than arr[ii] but when said smaller number is used to subtract from arr[ii] and gives us the result of *d*, or in other words:
> if (arr[ii] - arr[j] === d)

we'll know we have a group of beautiful triplets and thus can increment *beautifulTriplets* by one.

```
function beautifulTriplets(d, arr) {
let beautifulTriplets = 0

for (let i = arr.length - 1; i >= 2; i--) {
  for (let ii = i -1; ii >= 0;ii--) {
    if (arr[i] - arr[ii] === d) {
      for (let j = arr[ii]; j >= 0; j--) {
        if (arr[ii] - arr[j] === d) {
          beautifulTriplets+=1
        }
      }
    }
  }
 }
}
```
23:48 -- Eventually, after all of our loops terminate and we break out of them, we'll then return *beautifulTriplets* as our solution to this algorithm!
```
function beautifulTriplets(d, arr) {
let beautifulTriplets = 0

for (let i = arr.length - 1; i >= 2; i--) {
  for (let ii = i -1; ii >= 0;ii--) {
    if (arr[i] - arr[ii] === d) {
      for (let j = arr[ii]; j >= 0; j--) {
        if (arr[ii] - arr[j] === d) {
          beautifulTriplets+=1
        }
      }
    }
  }
 }
 return beautifulTriplets
}
```
Wow, this problem was a bit of a handful. Read over the original problem explanation a few times, try to understand my solution, and try to come up with your own solution.

If you stick with it, eventually you'll understand this algorithm and be able to produce a solution! :D