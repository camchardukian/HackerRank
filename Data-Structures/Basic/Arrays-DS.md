# Arrays - DS HackerRank Data-Structures Problem Solution

You can view the [Arrays - DS Data Structures problem on HackerRank here](https://www.hackerrank.com/challenges/arrays-ds/problem).
___


22:24 -- This problem is pretty simple. We have an array. Our goal is to reverse the array. Here's our basic setup:
```
function reverseArray(a) {

}
```
22:25 -- All we have to do to reverse our array is use the reverse() method. Thus, if we write:

> a = a.reverse()

we'll have reversed our array! Do note, however, that I set the value of *a* equal to a.reverse(). This ensures we actually save the value of a.reverse() inside of our variable rather than the reversed array simply disappearing.

In any case, here's our solution!
```
function reverseArray(a) {
a = a.reverse();
return a
}
```
22:27 -- We're done!