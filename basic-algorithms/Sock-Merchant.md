# Sock Merchant Hackerrank Algorithm Solution

You can find the [Sock Merchant HackerRank algorithm here](https://www.hackerrank.com/challenges/sock-merchant/problem).


16:38 -- The first thing we need to do is define a function *sockMerchant* that has the parameters *n* and *ar*.

*n* represents how many total socks we have in our sock pile (or in programming terms, the length of our array).

*ar* represents the color (such as a rgb value or hexcode) of each individual sock.
```
function sockMerchant(n, ar) {

}
```
16:40 -- I also think it's important that we define three variables before we go any further. The first of those three variables is *alreadyEvaluated*, which is initialized to an empty array, and will be used for checking whether we've already gathered all of the color socks of that color value.

For example, if we already gathered all of the blue socks, counted them, and performed our calculation; it isn't necessary for us to loop through everything and repeat said calculations if we encounter another blue sock.

The second variable is *numberOfSocks* which is initialized to 1 (because if we're evaluating a given color of socks from our array we know that there will be at least one of that color.). Whenever we find a color of sock that hasn't yet been evaluated, we'll loop through our array and total all of that color.

The third and final variable is *numberOfPairs*. Our *numberOfPairs* variable is initalized to 0, but may be incremented... we'll get to that later.

Now that we understand all of the variables, I'll show you the final solution and explain more in-depth about how all of the variables interact.
```
function sockMerchant(n, ar) {
let alreadyEvaluated = [];
let numberOfSocks = 1;
let numberOfPairs = 0;
for (let i = 0; i < n; i++){
  if (alreadyEvaluated.indexOf(ar[i])!= -1) {
  }
  else {
        alreadyEvaluated.push(ar[i])
         numberOfSocks = 1;
        for (let ii = i + 1; ii < n; ii++) {
          if (ar[i] === ar[ii]) {
numberOfSocks+=1
          }
        }
        numberOfPairs+=Math.floor(numberOfSocks/2)
  }
}
return numberOfPairs
}
```
16:48 -- From top to bottom, here we go.
 1. First we define our function, its parameters, and the variables we just finished discussing.

 1. Next, we write a for loop that'll loop through all of the socks in our pile.

 1. Within the for loop, we utilize the indexOf() method to evaluate whether the current sock color (value of ar[i]) has already been evaluated. If so, we do nothing and will move on to the next sock (item in the array *ar*). If not, we'll continue to the next step.

 1. If we haven't yet evaluated a given sock color, the first thing we need to do is push that sock color to our *alreadyEvaluated* array. This will prevent us from "double dipping" and wasting unnecessary resources evaluating it again later.

 1. After pushing the sock color to *alreadyEvaluated*, we then will loop through our *ar* array and compare our current sock with all of the remaining socks in the pile (one by one). Anytime the color of our current sock is the same as one of the socks in the pil, we increment numberOfSocks by one.

 1. After we go through all of the socks in the pile, we need to add the number of pairs to our *numberofPairs* variable. We do this by incrementing *numberOfPairs* by the result of Math.floor(numberOfSocks/2).

 1. If we haven't finished going through all of the possible color combination, we'll go back to our initial for loop from step #1 and repeat the process.

 1. After completing all of the previous steps, we return our *numberOfPairs* variable as our solution to the algorithm!