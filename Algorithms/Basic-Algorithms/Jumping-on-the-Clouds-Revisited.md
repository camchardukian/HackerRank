# Jumping on the Clouds: Revisited HackerRank Algorithm Solution

You can find the [Jumping on the Clouds: Revisited algorithm here](https://www.hackerrank.com/challenges/jumping-on-the-clouds-revisited/problem).
___

12:40 -- First, we have a function *jumpingOnClouds* that has two parameters: *c*: an array of integers representing the different cloud types, and *k*: an integer representing the length of one jump.

I've also initialized a variable *energy* to 100, because our character energy starts at 100 per the algorithm instructions.
```
function jumpingOnClouds(c, k) {
  let energy = 100;
}
```
12:44 -- Next, we use a for loop to iterate through our array of clouds *c*. We continue as long as our incrementor *i* is less than the length of our clouds array, also keeping in mind that we're incrementing *i* by the value of *k* or how far our character is capable of jumping.

For each iteration of our array, we identify whether our character landed on a thundercloud (1) or a safe cloud (0). We do this by seeing whether the current array item c[i] is equal to 1.

If so, we know our character landed on a thundercloud and we decrement *energy* by three. Otherwise, we only decrement *energy* by one because we know we're simply dealing with a standard jump onto a normal or safe cloud.

After we've iterated through the entire array and break out of our loop, we return *energy* as our solution to this algorithm!
```
function jumpingOnClouds(c, k) {
  let energy = 100;
for (let i = 0; i < c.length; i+=k) {
  if (c[i] === 1) {
    energy-=3
  }
  else {
    energy -=1
  }
}
return energy
}
```
Way to go!