# Utopian Tree HackerRank Algorithm Solution

You can find the [Utopian Tree algorithm here](https://www.hackerrank.com/challenges/utopian-tree/problem).

17:15 -- We have a function *utopianTree* which has a parameter *n* which takes in an integer representing the number of growth cycles we will go through. I've also defined a variable *treeHeight* which represents the height of our Utopian Tree.
```
function utopianTree(n) {
    let treeHeight = 0
}
```
17:17 -- Moving forward, we use a for loop. Our number of iterations is equal to the number of growth cycles *n* passed to our function.

On iterations which feature **0** or an even number (defined as an integer having a remainder of 0 after dividing by 2 with the modulus operator) we increment our tree height by one.

```
function utopianTree(n) {
    let treeHeight = 0
    for (let i = 0; i <= n; i++) {

        if (i % 2 === 0) {
            treeHeight += 1
        }
    }
}
```
If the iteration features an odd number, however (defined as an integer having a remainder of 0 after dividing by 2 with the modulus operator) we set the value of *treeHeight* to double its current value.

Finally, after we've finished running through our loop the specified number of times, we then return our *treeHeight* variable as the solution to our algorithm.
```
function utopianTree(n) {
    let treeHeight = 0
    for (let i = 0; i <= n; i++) {

        if (i % 2 === 0) {
            treeHeight += 1
        }
        else {
            treeHeight *= 2
        }
    }
    return treeHeight
}
```
We're done!