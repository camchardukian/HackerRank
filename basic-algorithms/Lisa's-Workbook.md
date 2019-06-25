# Lisa's Workbook HackerRank Algorithm Solution

You can view the [Lisa's Workbook algorithm here](https://www.hackerrank.com/challenges/lisa-workbook/problem).
___

12:28 -- Let's go over how this solution works. We have a function *workbook* that takes in 3 parameters: *n*: an integer representing the number of chapters in Lisa's workbook, *k*: an integer representing the maximum number of problems each individual page in the workbook can hold, and *arr*: an array of integers representing the number of problems for each chapter in the workbook.

Here's our basic setup for this algorithm:
```
function workbook(n, k, arr) {

}
```
12:32 -- Next, we're going to need several variables. These variables include:
* *pageNumber* -- The current page of the book we're on.
* *problemsOnCurrentPage* -- The number of problems we have on our current page.
* *problemNumberThisChapter* -- The number of problems in the current chapter we've already gone through.
* *specialProblems* -- The number of special problems we've had thus far. We'll eventually return this variable as our solution to the algorithm.

Apart from simply declaring the above variables, we're also going to initialize all of them to 0.
```
function workbook(n, k, arr) {
  let pageNumber = 0;
  let problemsOnCurrentPage = 0;
  let problemNumberThisChapter = 0
  let specialProblems = 0;
}
```
12:38 -- Now, we're going to add our first for loop. This for loop will run a number of times that's equivalent to the integer passed to *n* (the number of chapters in Lisa's book).

The role of this for loop is to move us along through all of the chapters in Lisa's book while also updating some values each time we start a new chapter.

Whenever we start a new chapter, that chapter is going to begin on a new page. Thus, with each iteration of our for loop, we're going to increment *pageNumber* by one.

We'll also update the values of *problemsOnCurrentPage* and *problemNumberThisChapter* to 0 each time we start a new chapter.
```
function workbook(n, k, arr) {
  let pageNumber = 0;
  let problemsOnCurrentPage = 0;
  let problemNumberThisChapter = 0
  let specialProblems = 0;
for (let i = 1; i <= n; i++) {
  problemsOnCurrentPage = 0;
  pageNumber+=1;
  problemNumberThisChapter = 0;
 }
}
```
12:44 -- Stay with me. We're on the home stretch. At this point, we need to do something while we're going through the problems in each chapter, before moving on to the next chapter.

Otherwise, we'd just be flipping from chapter to chapter with no regards for the actual contents of each chapter.

In other words, we're going to need a nested for loop. This nested for loop will run for as long as our variable *ii* is less than *arr[i-1]* -- the current position in *arr* (the number of problems in the chapter we're currently on).

With each iteration of our loop, we're going to increment *problemsOnCurrentPage* and *problemNumberThisChapter* by one.

Then, we'll evaluate if *problemsOnCurrentPage* is greater than *k*. If so, we'll increment *pageNumber* by 1, and update the value of *problemsOnCurrentPage* to equal 1, because we're going to a new page, and that new page currently houses 1 problem (the most recent problem we added).
```
function workbook(n, k, arr) {
  let pageNumber = 0;
  let problemsOnCurrentPage = 0;
  let problemNumberThisChapter = 0
  let specialProblems = 0;
for (let i = 1; i <= n; i++) {
  problemsOnCurrentPage = 0;
  pageNumber+=1;
  problemNumberThisChapter = 0;
  
  for (let ii = 0; ii < arr[i-1]; ii++) {
    problemsOnCurrentPage+=1
   problemNumberThisChapter+=1
    if (problemsOnCurrentPage > k) {
      problemsOnCurrentPage = 1
      pageNumber+=1
    }
  }
 }
}
```
12:52 -- If at any point the value of *problemNumberThisChapter* is equal to *pageNumber*, we'll know that we have a special problem and thus we increment our variable *specialProblems* by one.

Eventually, after we break out of our function's two loops, we'll return *specialProblems* as our solution to this algorithm!
```
function workbook(n, k, arr) {
  let pageNumber = 0;
  let problemsOnCurrentPage = 0;
  let problemNumberThisChapter = 0
  let specialProblems = 0;
for (let i = 1; i <= n; i++) {
  problemsOnCurrentPage = 0;
  pageNumber+=1;
  problemNumberThisChapter = 0;
  
  for (let ii = 0; ii < arr[i-1]; ii++) {
    problemsOnCurrentPage+=1
   problemNumberThisChapter+=1
    if (problemsOnCurrentPage > k) {
      problemsOnCurrentPage = 1
      pageNumber+=1
    }
    if (problemNumberThisChapter === pageNumber) {
      specialProblems+=1
    }
  }
 }
return (specialProblems)
}
```
12:54 -- Hopefully you were able to get some value out of this tutorial. Together you and I, let's keep practicing and improving our skills each day! :D
