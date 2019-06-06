**NOTE: I could not get any of my solutions to work on hackerrank (on repl.it all 3-4 of my solutions worked fine). Either I misinterpreted something during the challenge or the quality assurance tests for JavaScript were misfunctioning.**

**So, my answers listed throughout this entry may not get you points or pass their tests. But, perhaps my process of thinking will be beneficial to you in understanding how a developer may approach this problem.**

# Diagonal Difference


16:09 -- I'm now working on the Diagonal Difference algorithm on hackerrank.

16:11 -- This problem is strange. It gives me a square of numbers, and I'm supposed to sum up all of the numbers going one way diagonally, and then sum up all of the numbers going the other way diagonally. Then, find the absolute difference of the two sums using
> secondary diagonal sum - primary diagonal sum = absolute difference

16:16 -- The first thing I'm trying to figure out is whether the square is always going to be 3 x 3 or if it could be of varying dimensions (4 x 4), (5 x 5), etc.

16:20 -- I was trying to figure out what the pattern would be between our values in our diagonal line. I knew that we needed to find some kind of scaleable formula if we were going to be able to solve this problem. With the primary diagonal the pattern seems to be...
1. the first value in the array
1. take the dimension of the array, for example 3 x 3, and take the first digit and add +1. In this example 3 + 1 = 4. Then we would add 4 to our current accumulator (starting at 1) and we would then select 5, and then go through the process again to select 9.
1. The same would apply for 4x4. We would select 1 then (4+1) + 1 = 6... then 6 + (4+1) = 11 then 11 + (4 + 1) = 16
1. During this process of course, we would also be adding each of the numbers together. For example, 1 + 6 + 11 + 16 = 34

16:29 -- Of course, it's also important for us to find a scaleable formula for finding the secondary diagonal. This formula is also simple.
1. The first value we select is the number that is equivalent to the dimensions of our array. For example, if our array is 5 x 5, we would first select 5.
1. Going forward we take the dimension (5 in this case), and subtract one from the dimension. 5 - 1 = 4. Then we take this number and advance this many values in the array (we'd advance to number 9 in this example).
1. Repeat the process and we get 5 + 9 + 13 + 17 + 21 = 65

16:35 -- Once we've gotten the sum of both diagonals we take the primary diagonal sum and subtract it from the secondary diagonal sum to give us our absolute difference. In other words:
>secondary sum - diagonal sum = absolute difference

We'd then take whatever we got as the absolute difference and return it to get our answer and finish the challenge. So I hope lol.

16:37 -- I have some tightness in my forearms so I'm going to take a quick break to stretch and then I'll resume coding again in another 10 minutes or so.
___
16:55 -- I'm back. Let's actually code the solution now.

16:58 -- I think this challenge is poorly explained. I still don't know if I'm going to be told the dimensions of the array, or if I just have to infer the dimensions based on the length of the array. \**sigh*\*

17:03 -- Here's what my for loop implementation looks like for my primary diagonal:
```
for (let i = 0; i < arr.length; i+= Math.sqrt(arr.length) + 1) {
 primarySum += arr[i]
}
```

17:18 -- Things are looking good so far at least according to my console ;). Now I just have to do algebraic operations between the primary sum and secondary sum:
```
function diagonalDifference(arr) {
let primarySum = 0;
let secondarySum = 0;
let squareRoot = Math.sqrt(arr.length);

for (let i = 0; i < arr.length; i+= squareRoot + 1) {
 primarySum += arr[i]
}
for (let ii = squareRoot -1; ii <= arr.length - (squareRoot - 1);ii += squareRoot - 1) {
  secondarySum += arr[ii]
}
console.log(`primary sum is ${primarySum} and secondary sum is ${secondarySum}`)
}
diagonalDifference([1, 2, 7, 4, 5, 6, 7, 8, 9])
```

17:23 -- Here's my final solution, or so I think:
```
function diagonalDifference(arr) {
let primarySum = 0;
let secondarySum = 0;
let squareRoot = Math.sqrt(arr.length);
let absoluteValueDifference;

for (let i = 0; i < arr.length; i+= squareRoot + 1) {
 primarySum += arr[i]
}
for (let ii = squareRoot -1; ii <= arr.length - (squareRoot - 1);ii += squareRoot - 1) {
  secondarySum += arr[ii]
}

absoluteValueDifference = primarySum - secondarySum;
if (absoluteValueDifference < 0) {
  return absoluteValueDifference * -1
}
return absoluteValueDifference;
}

diagonalDifference([1, 2, 7, 4, 5, 6, 7, 8, 9])
```

17:25 -- Unfortunately, it seems I've misinterpreted the problem and made things more difficult for myself... again.

I do wish that the people that wrote these challenges were better communicators. In any case, it seems that I'm receiving 2 pieces in this array. The first is a lone number that tells about the dimensions of the array, and the 2nd is an array nested inside of our array that contains all of the numbers we need.

17:37 -- I'm starting to feel annoyed with hackerrank now. Not only are the authors of the problem sets questionable communicators, but also the tests themselves seem to be faulty:

```
function diagonalDifference(arr) {
let primarySum = 0;
let secondarySum = 0;
let squareRoot = arr[0];
let absoluteValueDifference;

for (let i = 0; i < arr[1].length; i+= squareRoot + 1) {
 primarySum += arr[1][i]
}
for (let ii = squareRoot -1; ii <= arr[1].length - (squareRoot - 1);ii += squareRoot - 1) {
  secondarySum += arr[1][ii]
}
console.log(`primary sum is ${primarySum} and secondary sum is ${secondarySum}`)

absoluteValueDifference = primarySum - secondarySum;
if (absoluteValueDifference < 0) {
  return absoluteValueDifference * -1
}
return absoluteValueDifference;
}

diagonalDifference([3,[11, 2, 4, 4, 5,6, 10, 8, -12]])
```
On repl.it my answer is functional, but it's continually rejected by hackerrank.

17:43 -- Perhaps the function is not being called as such:
> diagonalDifference([3,[11, 2, 4, 4, 5,6, 10, 8, -12]])

nor as such 
>diagonalDifference([1, 2, 7, 4, 5, 6, 7, 8, 9])

But the dimensions are actually included in a one dimensional array and the first value in the array is actually the base of our grid. For example a 3 x 3 grid could potentially be:
> diagonalDifference([3, 1, 2, 3, 4, 5, 6, 7, 8, 9])

17:54 -- I've now crafted a third answer that works based on the above input:
```
function diagonalDifference(arr) {
let primarySum = 0;
let secondarySum = 0;
let squareRoot = arr[0];
let absoluteValueDifference;

for (let i = 1; i < arr.length; i+= squareRoot + 1) {
 primarySum += arr[i]
 console.log(arr[i])
}
for (let ii = squareRoot; ii <= arr.length - (squareRoot);ii += squareRoot - 1) {
  secondarySum += arr[ii]
}
console.log(`primary sum is ${primarySum} and secondary sum is ${secondarySum}`)

absoluteValueDifference = primarySum - secondarySum;
if (absoluteValueDifference < 0) {
  return absoluteValueDifference * -1
}
return absoluteValueDifference;
}

diagonalDifference([3, 11, 2, 4,
4, 5, 6,
10, 8, -12])
```
Unfortunately, it seems either I am completely misinterpreting something about the problem (seems unlikely as I produced the expected answers in repl.it using three distinct functions based on different possible inputs), OR... there is something lacking in hackerrank's tests.

18:02 -- I looked at the discussion based around this algorithm and got the idea that perhaps the problem was that I manually found the absolute value of our difference rather than using the Math.abs() method.

18:08 -- Absolutely ridiculous. Even directly copying answers others have posted won't solve this problem.

18:10 -- I cannot even get the "editorial answers" to work. This algorithm has seriously soured my experience with hackerrank. I hope this is a one-off issue with their algorithms.

If their instructions continue to be poorly communicated and I continue to have problems with their tests I'll have to switch over to codesignal or Dylan Israel's 100 algorith challenge course.