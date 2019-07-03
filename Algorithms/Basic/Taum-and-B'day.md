# Taum and B'day HackerRank Algorithm Solution

You can view the [Taum and B'day algorithm here](https://www.hackerrank.com/challenges/taum-and-bday/problem).
___

9:14 -- For this problem, it looks like we have a boy named Taum who needs to buy presents for his friend Diksha's birthday.

To make Diksha happy Taum has to buy her a certain number of white gifts *w*, and a certain number of black gifts *b*.

Taum wants to spend the minimum amount of money necessary to do so. The cost for black gifts is *bc*, the cost of white gifts is *wc*, and the cost of converting the gifts from one color to another is *z*.

Our job is to determine the minimum amount of money Taum needs to buy Diksha the gifts she wants.

Here's our basic function setup:
```
function taumBday(b, w, bc, wc, z) {

}
```
9:20 -- I'll document my progress as I go, and explain my final solution to you once I reach one.

9:27 -- Here's my pseudocode brainstorm:
```

// If we need to buy black gifts, determine whether bc < wc + z. If so, multiply bc * b. If not, multiply (wc + z) * b and set equationOneResult equal to the result.

// If we need to buy white gifts, determine whether wc < bc + z. If so, multiply wc * w. If not, multiply (bc + z) * b, and set equationTwoResult equal to result.

// Add equationOneResult plus equationTwoResult to get our solution to this algorithm!
```
9:33 -- Working to implement my pseudocode. Halfway there...
```
function taumBday(b, w, bc, wc, z) {
let equationOneResult;
let equationTwoResult;

if (b > 0) {
  if (bc <= wc + z) {
    equationOneResult = bc * b
  }
  else if (bc > wc + z) {
    equationOneResult = (wc + z) * b
  }
 }
}
```
9:35 -- Taking a 20 minute break to handle something, be back soon.

9:58 -- I'm back. Let's finish solving this algorithm.

10:08 -- I've almost solved the algorithm. I've passed 13/15 test cases. It looks like the only issue is that I need to deal with the small value discrepancies that sometimes occur in JavaScript as a result of the manner in which the language uses binaries in dealing with numbers.

10:19 -- Quite honestly, I'm feeling lost. My use of the Math.round() method has only resulted in decreased performance it seems.

My function now only passed 10/15 test cases:
```
function taumBday(b, w, bc, wc, z) {
let equationOneResult;
let equationTwoResult;

if (b > 0) {
  if (bc <= wc + z) {
    equationOneResult = Math.round((bc * b)*100000)/100000
  }
  else if (bc > wc + z) {
    equationOneResult = Math.round(((wc + z) * b)*100000)/100000
  }
  else {
    return ("Error: incorrect input")
  }
 }
 if (w > 0) {
   if (wc <= bc + z) {
     equationTwoResult =  Math.round((wc * w)*100000)/100000
   }
   else if (wc > bc + z) {
     equationTwoResult = Math.round(((bc + z) * w)*100000)/100000
   }
   else {
     return ("Error: incorrect input")
   }
 }
 return (Math.round(equationOneResult + equationTwoResult)*100000)/100000
}
```
10:41 -- To make a long story short, it seems the numbers in this problem were too large for JavaScript to handle.

As such, getting a perfect score on this algorithm requires the use of the BigNumber library.

Whenever I try to use the bignumber library I seem to get a runtime error with my solution:
```
function taumBday(b, w, bc, wc, z) {
let equationOneResult;
let equationTwoResult;

if (b > 0) {
  if (bc <= wc + z) {
    equationOneResult = bc * BigNumber(b)
  }
  else if (bc > wc + z) {
    equationOneResult = (wc + z) * BigNumber(b)
  }
  else {
    return ("Error: incorrect input")
  }
 }
 if (w > 0) {
   if (wc <= bc + z) {
     equationTwoResult =  wc * BigNumber(w)
   }
   else if (wc > bc + z) {
     equationTwoResult = (bc + z) * BigNumber(w)
   }
   else {
     return ("Error: incorrect input")
   }
 }
 return (BigNumber(equationOneResult) + BigNumber(equationTwoResult))
}
```
Not to leave you hanging, however, here's an example from the [community](https://www.hackerrank.com/challenges/taum-and-bday/forum) of a user that successfully used the library to earn a full 25 points whereas my original solution (without bignumber) was only enough to earn 19 points (because of native JavaScript's limitations in dealing with very large numbers).

Here you go:
```
const BigNumber = require('bignumber.js')

function taumBday (b, w, bc, wc, z) {
    [b, w, bc, wc, z] = [...arguments].map(x => new BigNumber(x))
    let tbc = BigNumber.min( b.times(bc), b.times(wc).plus(b.times(z)) )
    let twc = BigNumber.min( w.times(wc), w.times(bc).plus(w.times(z)) )
    return tbc.plus(twc).toFixed()
}
// courtesy of HackerRank user 
adamxtokyo
```
10:50 -- While this problem had some complexities, I hope you were able to get some value out of our discussion!

While my understanding of the BigNumber library is pretty sketchy, you can [read more about it here](https://github.com/MikeMcl/bignumber.js/).