# Library Fine HackerRank Algorithm Solution

You can view the [Library Fine algorithm here](https://www.hackerrank.com/challenges/library-fine/problem).
___

21:18 -- It looks like we have a local library that wants us to build an application that calculates the fee (if any is applicable) to books that are returned after their expected return date.

We have a function *libraryFine* that has several parameters:
* *d1*, *m1*, *y1*: Integers representing the day, month, and year on which the book was returned.
* *d2*, *m2*, *y2*: Integers representing the day, month, and year on which the book was *supposed* to be returned by.

To see full details on how this algorithm wants us to calculate fines, please [see its page on HackerRank](https://www.hackerrank.com/challenges/library-fine/problem).

Otherwise, here are the basic elements to keep in mind:

1. If the book is returned on or before the expected return date, no fine will be charged (fine = 0)

1. If the book is returned after the expected return day but still within the same calendar month and year as the expected return date (fine = 15 Hackos x number of days late)

1. If the book is returned after the expected return month but still within the same calendar year as the expected return date, (fine = 500 Hackos x number of months late)

1. If the book is returned after the calendar year in which it was expected, there is a fixed fine of
(fine = 10000 Hackos)

21:19 -- Here's our basic problem setup:
```
function libraryFine(d1, m1, y1, d2, m2, y2) {

}
```
21:20 -- Next I'll declare an optional variable *fine*. I'll explain my algorithm solution using our variable *fine*, but you could also easily do away with using an additional variable.

It just depends on what you think is easily readable by both yourself and other developers.
```
function libraryFine(d1, m1, y1, d2, m2, y2) {
let fine;
}
```
21:23 -- Moving forward, we know that if the book is returned in a year after the year it was "supposed" to be returned, the library should give out a flat fine of 10000. 

Thus, if the year the book was received (y1) is greater than the year in which the book was supposed to be returned (y2), we can set *fine* equal to 10000 and return it as our solution to this algorithm!
```
function libraryFine(d1, m1, y1, d2, m2, y2) {
let fine;

if (y1 > y2) {
  fine = 10000;
  return fine;
  }
}
```
21:26 -- If our book is returned in the correct year (y1 === y2), we'll check to see if the book was returned some number of months after it was supposed (m1 > m2). If so, we'll assess a fine that is equal to the number of months the book was late (m1-m2) times 500 (the late fee per month prescribed by the library's instructions).
```
function libraryFine(d1, m1, y1, d2, m2, y2) {
let fine;

if (y1 > y2) {
  fine = 10000;
  return fine;
}
if (y1 === y2) {
if (m1 > m2) {
  fine = (m1-m2)*500
  return fine
  }
 }
}
```
21:29 -- We're getting close to the finish. If the year the book was returned AND the month the book was returned match when it was supposed to be returned, we'll then evaluate if the book was returned some number of days after it was supposed to be returned (d1 > d2).

If so, we'll assess a fine that is equal to the number of days late the book was returned (d1 - d2) times 15 (the late fee per day prescribed by the library).
```
function libraryFine(d1, m1, y1, d2, m2, y2) {
let fine;

if (y1 > y2) {
  fine = 10000;
  return fine;
  }
if (y1 === y2) {
if (m1 > m2) {
  fine = (m1-m2)*500
  return fine
  }
 else if (m1 === m2) {
  if (d1 > d2) {
    fine = (d1-d2)*15
    return fine
   }
  }
 }
}
```
If we go through all of the previous steps, however, without having to assess any fines (the book was either returned on time or before it was due), we'll then set the fine to 0 and return that as our solution to this algorithm!
```
function libraryFine(d1, m1, y1, d2, m2, y2) {
let fine;

if (y1 > y2) {
  fine = 10000;
  return fine;
   }
if (y1 === y2) {
if (m1 > m2) {
  fine = (m1-m2)*500
  return fine
    }
 else if (m1 === m2) {
  if (d1 > d2) {
    fine = (d1-d2)*15
    return fine
    }
  }
 }
fine = 0
return fine
}
```
21:35 -- Way to go! We're all done here! If you'd like more practice with algorithms, check out my other [HackerRank algorithm explanations on GitHub](https://github.com/camchardukian/hackerrank-algorithms).