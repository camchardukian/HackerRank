# Jumping on the Clouds HackerRank Algorithm Solution

You can view the [Jumping on the Clouds algorithm here](https://www.hackerrank.com/challenges/jumping-on-the-clouds/problem.).
___


21:17 -- We have a function *jumpingOnClouds* that has a single parameter *c* which takes in an array of integers that represent cloud types that are either safe (0) or must be avoided (1).

I've also initialized another variable *jumpCount* to 0.
```
function jumpingOnClouds(c) {
  let jumpCount = 0;
for (let i = 0; i <= c.length -2;) {
  if (c[i + 2] === 1) {
    i+=1
  }
  else {
    i+=2
  }
  jumpCount+=1
  console.log(i)
}
return jumpCount
}
```
21:21 -- Moving forward, I've created a for loop that starts at 0, and continues for as long as our variable *i* is less than or equal to the length of our *c* array minus two.

*Why (c.length - 2)?* Because we want our character to continue jumping all the way to the end of our array of clouds. We subtract 2 in this case, because the greatest length our character is capable of jumping is 2 clouds.

Also, notice that I didn't utilize the third optional expression in our for loop.

While normally we would increment *i* at this point, in this case, doing so is not necessary because we will increment *i* within the loop itself.

More on that later...
```
function jumpingOnClouds(c) {
  let jumpCount = 0;
for (let i = 0; i <= c.length -2;) {
    }
}
```
21:27 -- Are you still following along? Hopefully I haven't lost you yet ;) Anyway, within our for loop, we'll create an expression that states:
> If c[i+2] equals 1, we'll only increment *i* by one. This is because we know that if our character jumps two clouds forward (c[i+2]), that our character would jump onto a cloud that isn't safe to jump on. Thus, we only increment *i* by one because we only want our character to jump one cloud forward.

If on the other hand, c[i+2] **DID NOT** equal 1, we'd know that our character would be safe in jumping two clouds forward. Thus, we'd have no problem incrementing *i* by two.

Regardless of whether we increment *i* by one or two, we should increment *jumpCount* by one because we know our character just took another jump forward.

As long as our character has yet to reach the final cloud, we'll continue to loop through this process incrementing *i* by one or two.

Eventually, however, we'll reach the final cloud and break out of this loop. When that happens, we can return *jumpCount* as our solution to this algorithm!
```
function jumpingOnClouds(c) {
  let jumpCount = 0;
for (let i = 0; i <= c.length -2;) {
  if (c[i + 2] === 1) {
    i+=1
  }
  else {
    i+=2
  }
  jumpCount+=1
}
return jumpCount
}
```
Nice work!