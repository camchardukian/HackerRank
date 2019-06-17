# Divisible Sum Pairs Hackerrank Algorithm Solution

You can find the [Divisible Sum Pairs algorithm here](https://www.hackerrank.com/challenges/divisible-sum-pairs/problem).

Here's my final solution to said problem:
```
function divisibleSumPairs(n, k, ar) {
  let results = [];

for (let i = 0; i < n - 1; i++) {
  for (let ii = i + 1; ii < n; ii++) {
    if ((ar[i]+ar[ii]) % k === 0) {
      results.push(`${i},${ii}`)
    } 
  }
}
return results.length
}
```
10:06 -- While the code I wrote to get to this point may have been a bit messy, the solution itself is pretty simple. Here's what we're doing.

10:07 -- First, we have a function *divisbleSumPairs* that has parameters of *n*, *k*, and *ar*.

*n* takes in an argument that represents the integer length of the array, the value passed to *k* is what we will use as a divisor, and the value passed to *ar* will be our array of integers.

I've also initialized a results variable to an empty array, which we will later use when we need to return our output for the algorithm.
```
function divisibleSumPairs(n, k, ar) {
  let results = [];
}
```
10:13 -- The next thing we need to do is loop through and add the items in our array. If our array was [1, 3, 5, 10] for example, we'd need to first see what do 1 + 3 equal, then 1 + 5, then 1+ 10. Then... we'd go to the next number and see 3 + 5, 3 + 10, etc.

We can do this by using a nested array.
```
function divisibleSumPairs(n, k, ar) {
  let results = [];

for (let i = 0; i < n - 1; i++) {
  for (let ii = i + 1; ii < n; ii++) {
    if ((ar[i]+ar[ii]) % k === 0) {
      results.push(`${i},${ii}`)
    } 
  }
  return results.length
}
```
Notice that in the code above, besides simply adding every possible combination of integer pairs from the array, we also used the modulus operator (%).

The reason we used the modulus operator is because through using it we can see if numbers are evenly divisble by something.

In this case, we used the modulus operator to evaluate whether a pair of integers (ar[i] + ar[ii]) divided by *k* would have a remainder of **0**.

If so, we pushed that pair of integers to our result array.

Finally, we returned the length of our results array as our output and final solution to this algorithm.

While we could've used a simple counter variable and just incremented it each time we found an integer pair evenly divisible by *k*, I thought saving the integer pairs may be useful for some other unspecified future operation (if this were a real-world example).

Of course, you could also argue that having to return the length of the *results* array rather than simply displaying the number assigned to a counter variable results in some extra processing time.

That may be true. Alas, the ideal solution depends on the intended real-world use case, and is beyond the scope of this algorithm.

Regardless, I hope you found my explanation of this algorithm useful!