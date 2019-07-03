# Cats and a Mouse Hackerrank Algorithm Solution

You can find the [Cats and a Mouse algorithm here](https://www.hackerrank.com/challenges/cats-and-a-mouse/problem).

8:52 -- To start with, we define a function *catAndMouse* that has three parameters *x*, *y*, and *z*. Our variables represent the starting points of our different animals. *x* represents 'Cat A', *y* represents 'Cat B', and *z* represents 'Mouse C'.
```
function catAndMouse(x, y, z) {

}
```
Now, we need to see which cat is further away from the mouse. It's important to remember that we're thinking about distance here, and not money for example.

For that reason, it doesn't really matter if our cat is on a negative position on the number line or a positive position.

All that matters is how many "steps"
on the number line our cat is away from the mouse.

Let's look at an example:

> CatA(3) - Mouse(1) = 2

Whereas:
>CatB(-100) - Mouse(1) = -101

Obviously CatA is closer to the mouse and will catch it far before CatB. CatA is only 2 "steps" in the positive direction away from the mouse while CatB is 101 "steps" away in the negative direction.

However, let's change the numbers a bit:
>CatA[50] - mouse(-100) = 150

versus
>CatB(-99) - mouse(-100) = 1

In this scenario CatA is 150 "steps" away from the mouse while CatB is only 1 "step" away from the mouse.

As you can see, it doesn't matter whether our cats are sitting a given number of steps away in the "positive" direction or the "negative" direction.

Far more vital is the absolute number of steps away from the mouse that they are.

For that reason, and because we do not know if either or both of our cats will be starting at a negative position, we need to find the absolute value of the distance between *x-z* and *y-z*. We can do that using the Math.abs() method.

And here's our final solution!
```
function catAndMouse(x, y, z) {
if (Math.abs(x-z) > Math.abs(y-z)) {
  return ("Cat B")
}
else if (Math.abs(x-z) < Math.abs(y-z)) {
  return ("Cat A")
}
else if (Math.abs(x-z) === Math.abs(y-z)) {
  return ('Mouse C')
}
else {
  return ("error: unexpected input")
}
}
```
If the distance between CatA and the mouse is greater than CatB and the mouse, we return "Cat B".

If the distance between CatA and the mouse is less than the distance between CatB and the mouse, we return "Cat A".

If the distances are the same, we return "Mouse C".

And in any other situation, we return "error: unexpected input".

There we go, a comprehensive explanation of this algorithm. Hopefully breaking things down helped you understand! :D