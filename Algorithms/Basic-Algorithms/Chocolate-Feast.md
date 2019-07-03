# Chocolate Feast HackerRank Algorithm Solution

You can view the [Chocolate Feast algorithm here](https://www.hackerrank.com/challenges/chocolate-feast/problem).
___

21:31 -- Let's go over everything. First, we have a function *chocolateFeast* that has three parameters: *n*: an integer representing the amount of money Bobby is starting with, *c*: an integer representing the cost of a chocolate bar, and *m*: an integer representing the number of wrappers Bobby can turn in for a free chocolate bar.

Our job is to figure out how many chocolate bars Bobby can get.

Note that we're making a few assumptions. The first assumption is that Bobby will use all of his money. The second assumption is that Bobby will immediately turn in his wrappers for a free bar of chocolate if he has enough wrappers.

With that being the case, let's look at our problem's basic setup:
```
function chocolateFeast(n, c, m) {

}
```
21:34 -- I've also defined a few additional variables: *chocolateBars* and *wrappers*, both of which are initialized to the result of Math.floor(n/c).

In other words, we're initializing those two variables to the value of our money divided by the cost of a chocolate bar, and we're taking that result and rounding it down to the nearest integer.
```
function chocolateFeast(n, c, m) {
  let chocolateBars = Math.floor(n/c);
  let wrappers = Math.floor(n/c);
```
21:41 -- Next, we're going to use a for loop. Our for loop has a variable *i* which is initialized to the value of *wrappers*.

Our for loop will continue running for as long as *wrappers* is greater than or equal to *m* (the number of wrappers Bobby need to exchange for a free chocolate.) Finally, we're decrementing *i* by *m*.

Now that we've finished talking about the three expressions governing this for loop, let's talk about the contents within the loop. Everytime our loop runs, we increment *chocolateBars* by one, and decrement *wrappers* by *m*.

This is because our wrappers should decrease everytime we successfully exchange them for a chocolate bar, and our number of chocolate bars should increase by one everytime we make a successful exchange.

After we finish decrementing *wrappers*, we'll then increment *wrappers* by one because after getting a free chocolate bar we can eat the chocolate bar and have an additional wrapper to trade in.

Finally, after we eventually break out of this loop, we'll return *chocolateBars* as our solution to this algorithm!
```
function chocolateFeast(n, c, m) {
    let chocolateBars = Math.floor(n / c);
    let wrappers = Math.floor(n / c);

    for (let i = wrappers; wrappers >= m; i -= m) {
        chocolateBars += 1
        wrappers -= m;
        wrappers += 1
    }
    return (chocolateBars)
}
```
We did it!