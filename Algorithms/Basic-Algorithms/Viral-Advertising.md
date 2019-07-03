# Viral Advertising HackerRank Algorithm Solution

You can find the [Viral Advertising algorithm here](https://www.hackerrank.com/challenges/strange-advertising/problem).

20:55 -- Here we go. We have a function *viralAdvertising* with a single parameter *n* which will be passed an integer that represents how many days have passed since our advertising campaign begun.
```
function viralAdvertising(n) {

}
```
20:58 -- I've also defined several variables. Initialized to 5 is our *viewers* variable, because that's how many people we shared our ad with on the first day. *currentLikers* and *cummulativeLikes* on the other hand are initialized to 0 because we will calculate these values based upon the number of viewers we have each day.
```
function viralAdvertising(n) {
  let viewers = 5;
  let currentLikers = 0;
  let cummulativeLikes = 0;
}
```
21:00 -- Now that we've gotten all of our variables initialized, we need to create a for loop that'll perform our calculations a given number of times based upon the value of *n*, or how many days have passed since our advertising campaign began.

As for the calculations themselves, they are pretty straightforward. We set our *currentLikers* equal to the result of Math.floor(viewers/2). We then increment our *cummulativeLikes* by *currentLikers*.

Finally, to determine the number of people that will view our ad on the next day, we set *viewers* equal to the result of *currentLikers* times 3 (because each of the people that liked our post will share it with three of their friends).

Then we repeat the process. After we eventually break out of this loop, we'll return the value of *cummulativeLikes* as the solution to this algorithm.
```
function viralAdvertising(n) {
  let viewers = 5;
  let currentLikers = 0;
  let cummulativeLikes = 0;
for (let i = 0; i < n; i++) {
  currentLikers = Math.floor(viewers/2)
  cummulativeLikes+= currentLikers;
  viewers = currentLikers * 3
}
return cummulativeLikes
}
```
That's it! You're finished!