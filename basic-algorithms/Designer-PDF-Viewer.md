# Designer PDF Viewer HackerRank Algorithm Solution

You can find the [Designer PDF Viewer
 algorithm here](https://www.hackerrank.com/challenges/designer-pdf-viewer/problem).


The first thing we have is a function *designerPdfViewer* which has two parameters *h*, and *word*.

*h* is an array whose items represent the height of each individual letter in the alphabet.

*word* represents a string of characters (letters in the intended use case).
```
function designerPdfViewer(h, word) {
    
}
```
9:00 -- Now, we need a couple variables. One is *tallestLetter* which we'll initialize to **0** and later use for storing the height of the tallest letter from the string passed to *word*.

We also need a variable *alphaArr* which is initialized to a 2-d array with each letter of the alphabet given its own sub-array.
```
function designerPdfViewer(h, word) {

  let tallestLetter = 0;
  let alphaArr = [
 ['a'], ['b'], ['c'], ['d'], ['e'],['f'], ['g'],
 ['h'], ['i'], ['j'], ['k'], ['l'], ['m'], ['n'], ['o'], ['p'], ['q'], ['r'], ['s'], ['t'], ['u'],
 ['v'], ['w'], ['x'], ['y'], ['z']
 ];
}
```
9:03 -- Of course, we're not finished yet. We need to loop through the array passed to *h* in order for us to assign said integers to the letters in our *alphaArr* (this will give each letter an appropriate height).
```
function designerPdfViewer(h, word) {

  let tallestLetter = 0;
  let alphaArr = [
 ['a'], ['b'], ['c'], ['d'], ['e'],['f'], ['g'],
 ['h'], ['i'], ['j'], ['k'], ['l'], ['m'], ['n'], ['o'], ['p'], ['q'], ['r'], ['s'], ['t'], ['u'],
 ['v'], ['w'], ['x'], ['y'], ['z']
 ];

 for (let i = 0; i < h.length; i++) {
   alphaArr[i].push(h[i])
 }
}
 ```
 9:06 -- Now that each letter in our *alphaArr* has been assigned a height, we now need to loop through each character in the string passed to *word*.

 We'll also nest another for loop inside our first for loop. The second for loop is for looping through each item in our *alphaArr*.

When our letter from *word* is equivalent to the letter from our *alphaArr*, we'll then evaluate if said letter is taller than the previous letter (value) assigned to *tallestLetter*.

If so, we'll assign *tallestLetter* the value of *h[ii]* (the current index and thus current height of a letter from our *h* array).

Otherwise, we'll simply continue looping through the rest of the characters in our *word* string.

Once we've finished looping through everything, we'll return the value assigned to *tallestLetter* times the length of the string passed to *word* for our solution to the algorithm.

*Why do we need to use multiplication?* Because our selection rectangle, like all rectangles has both a height (*tallestLetter*) and a width (*word.length*).

```
function designerPdfViewer(h, word) {

  let tallestLetter = 0;
  let alphaArr = [
 ['a'], ['b'], ['c'], ['d'], ['e'],['f'], ['g'],
 ['h'], ['i'], ['j'], ['k'], ['l'], ['m'], ['n'], ['o'], ['p'], ['q'], ['r'], ['s'], ['t'], ['u'],
 ['v'], ['w'], ['x'], ['y'], ['z']
 ];

 for (let i = 0; i < h.length; i++) {
   alphaArr[i].push(h[i])
 }

 for (let i = 0; i < word.length; i++) {
   for (let ii = 0; ii < alphaArr.length; ii++) {

if (word[i] === alphaArr[ii][0]) {
     if (h[ii] > tallestLetter) {
       tallestLetter = h[ii]
     }
      }
   }
   
 }
return (tallestLetter*word.length)
}
```
Aaaaaand we're done!