# Kangaroo HackerRank Algorithm Solution

You can view the [Kangaroo algorithm here](https://www.hackerrank.com/challenges/kangaroo/problem).
___

20:43 -- We have two kangaroos. Our job is to figure out if these two kangaroos will ever land in the same place after the same number of jumps.

If so, our function should return "YES". Otherwise, our function should return "NO".

To accomplish this task, we have a function *kangaroo* that has four parameters:
* *x1* -- The starting position for kangaroo 1.
* *v1* -- The jump distance for kangaroo 1.
* *x2* -- The starting position for kangaroo 2.
* *v2* -- The jump distance for kangaroo 2.

Here's our basic function setup:
```
function kangaroo(x1, v1, x2, v2) {
} 
```
20:49 -- Our logic for solving this problem is pretty simple. If our first kangaroo has a larger jump distance than our second kangaroo (*v1* > *v2*), we'll run a for loop for as long as the second kangaroo is farther along than the first kangaroo (x1 < x2).

Once this stops being the case, we would of course break out of our loop because if the fastest kangaroo ever gets ahead, any further looping becomes unnecessary because the slower kangaroo will never be able to catch up.

Moving forward, for each iteration of our loop, we'll advance our kangaroo's positions (*x1* and *x2*) by the value of the distance they can make with each jump (*v1* and *v2* respectively).

Each time through our loop, we'll also check to see if our kangaroos are in the same position (x1 === x2). If so, we'll return "YES" as our solution to this algorithm.

```
function kangaroo(x1, v1, x2, v2) {
if (v1 > v2) {
  while (x1 < x2) {
    x1+= v1;
    x2+= v2;
    if (x1 === x2) {
    return "YES"
    }
  }
 }
}
```
20:57 -- Of course, it's important to note that sometimes our first kangaroo will be faster and sometimes our second kangaroo will be faster. If the first kangaroo is faster we'll utilize our if statement above.

Otherwise, we can simply reverse the logic to create an if else statement to govern a scenario in which the second kangaroo is faster.

Finally, regardless of whether our passed arguments lead to us using the logic in our if statement or the logic in our if else statement, one thing is certain.

Our two kangaroos will either be in the same spot after the same numbers of jumps at some point (in this scenario we'd return "YES"), OR neither our if nor or if else statement returned anything, and thus we'd return "NO" as our solution to this algorithm.
```
function kangaroo(x1, v1, x2, v2) {
if (v1 > v2) {
  while (x1 < x2) {
    x1+= v1;
    x2+= v2;
    if (x1 === x2) {
    return "YES"
    }
  }
 }
  else if (v1 < v2) {
    while (x1 > x2) {
      x1+= v1;
      x2+= v2;
      if (x1 === x2) {
        return "YES"
      }
    }
  }
  return "NO"
}
```
21:03 -- Hopefully you were able to follow along. For more algorithm challenges, you can go to [HackerRank's algorithm challenges page](https://www.hackerrank.com/domains/algorithms), and for more solutions check out my [HackerRank algorithm solutions GitHub repo](https://github.com/camchardukian/hackerrank-algorithms).