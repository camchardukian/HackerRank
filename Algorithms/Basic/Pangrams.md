# Pangrams Characters HackerRank Algorithm Solution

You can view the [Pangrams algorithm on HackerRank here](https://www.hackerrank.com/challenges/pangrams/problem).
___


23:29 -- It seems we have a boy named Roy who wants to improve his typing speed. For that reason, he wants to practice typing pangrams (a single sentence which contains every letter of the alphabet).

We have a function *pangrams* that has a single parameter *s*, which will take in a string.

We need to evaluate whether the string *s* is a pangram -- ignoring cases (whether the letters are lower or uppercase).

Here's our basic setup:
```
function pangrams(s) {

}
```
23:30 -- We need to declare and initalize a few variables. The most simple of which is a variable we can name *result*. We'll initialize *result* to the string 'pangram'.

You'll probably find understanding this variable pretty straightforward. *result* is simple a variable that will hold the value 'panagram' or 'not panagram'. 

We'll later return our variable *result* as our solution to this algorith.

We also need to get rid of the spaces in our string *s*, ensure all of the characters in *s* are lowercase, and then we'll also want to turn *s* into an array.

More on that coming up shortly...
```
function pangrams(s) {
  let result = 'pangram';
s = s.replace(/\s/g, "").toLowerCase().split("");
}
```
23:35 -- Now, the next thing we need to do is declare another variable *testArray*. 

The purpose behind creating *testArray* is we want an array that contains [ASCII numbers/codes](https://en.wikipedia.org/wiki/ASCII) (in practical terms each item in our array will be an integer), that correspond with each character in our string.

We can do this by mapping the character code from each character in our string over to our new array.
```
function pangrams(s) {
let result = 'pangram';
s = s.replace(/\s/g, "").toLowerCase().split("");

let testArray = s.map(s => s.charCodeAt(0))
```
23:43 -- Next, we need a for loop. This loop will iterate through all of the ASCII codes from lowercase 'a' (97) all the way to 'z' (122).

Each time through our array, we'll use the indexOf() method on *testArray* to see if *testArray* contains the ASCII code we're looking for.

For example, if testArray.indexOf(97) returns any value greater than -1, we'll know that ASCII code occured somewhere in our array, and thus... somewhere in our string we have the letter that corresponds to that ASCII code ('a').

If testArray.indexOf(i) is NOT greater than -1, however, we'll know *testArray* does not contain the ASCII code we're looking for.

Moreover, we'll know our string is not a pangram because it is missing some letter between 'a' and 'z'. At this point you probably also understand why we had to convert our entire string to lowercase at the beginning of our function:

> We needed to ensure all of the ASCII codes we were looking for would appear in consecutive orders, and that we would not miss some code because we were for example searching for ASCII code 65 ('A'), when the reality is that *testArray* only contained ASCII code 97 ('a').

To make a long story short, if our string contains all the ASCII codes we need, we'll return *result* in its current form as the solution to our algorithm ('pangram').

If at any point along the way, however, *testArray* doesn't contain the ASCII code we're looking for... we'll set the value of *result* to the string 'not pangram' and then return *result* as our solution to this algorithm.
```
function pangrams(s) {
let result = 'pangram';
s = s.replace(/\s/g, "").toLowerCase().split("");

let testArray = s.map(s => s.charCodeAt(0))

  for (let i = 97; i <= 122; i++) {
    if (testArray.indexOf(i) > -1) {

    }
    else {
      result = "not pangram"
      return result
    }
  }
return result
}
```
23:54 -- That was a LONG explanation for less than 20 lines of code hahahaa. In any case, I hope you got some value out of this explanation.

Keep up the great coding! :D