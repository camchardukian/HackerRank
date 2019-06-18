# The Hurdle Race HackerRank Algorithm Solution

You can find the [The Hurdle Race
 algorithm here](https://www.hackerrank.com/challenges/the-hurdle-race/problem).

13:22 -- Let's walk through it. First, we have a function *hurdleRace* which has two parameters *k* (an integer representing how high Dan's character can jump), and *height* (an array of integers representing the height of each individual hurdle Dan must jump over).

I've also defined a couple additional variables. *tallestHurdle* and *potionsNeeded*, both of which are initialized to 0.
```
function hurdleRace(k, height) {
  let tallestHurdle = 0;
  let potionsNeeded = 0;
}
```
The next thing we need to do is figure out which hurdle is tallest. We can do that by looping through our *height* array and seeing if each item's value is larger than the value which *tallestHurdle* is currently set to.
```
function hurdleRace(k, height) {
  let tallestHurdle = 0;
  let potionsNeeded = 0;
for (let i = 0; i < height.length; i++) {
  if (tallestHurdle < height[i]) {
    tallestHurdle = height[i]
  }
}
}
```
Finally, we can compare the values of *tallestHurdle* and *k* (which is the maximum height Dan can jump without potions).

If *tallestHurdle* is greater than *k* the height Dan can jump, we subtract *k* the height Dan can jump from our *tallestHurdle* variable and set our *potionsNeeded* variable equal to this integer.

Finally, we return our *potionsNeeded* variable as our solution to this algorithm.

Of course, if *tallestHurdle* was not greater than *k*, we would've simply broken out of our if statement, and returned potionsNeeded as the value it was initialized to (**0**).
```
function hurdleRace(k, height) {
  let tallestHurdle = 0;
  let potionsNeeded = 0;
for (let i = 0; i < height.length; i++) {
  if (tallestHurdle < height[i]) {
    tallestHurdle = height[i]
  }
}
if (tallestHurdle > k) {
  potionsNeeded = tallestHurdle - k
}
return potionsNeeded
}
```
We're finished!