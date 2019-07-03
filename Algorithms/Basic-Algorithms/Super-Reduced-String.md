# Super Reduced String HackerRank Algorithm Solution

You can view the [Super Reduced String algorithm on HackerRank here](https://www.hackerrank.com/challenges/reduced-string/problem).
___


17:51 -- It looks like we have a guy named Steve who has a string of lowercase characters ranging from a-z.

Anytime Steve sees two adjacent of the same letters touching each other ('aa') he deletes both letters.

Our job is to go through the string in the same manner as Steve, deleting pairs of the same letters that are touching each other.

In the end, we should return what our string looks like after all of the deletions. Or, if the final string we have is empty, we'll return 'Empty String'.

Here's our basic setup:
```
function superReducedString(s) {

}
```
17:54 -- Next, I'm going to declare a variable *array*. We'll initialize *array* to the value of *s*.split("").

The reason we're doing this is because later on we'll want to use the splice() method. Doing so requires an array, and thus we need to manipulate our data types ahead of time.
```
function superReducedString(s) {
  let array = s.split("");
}
```
17:57 -- Moving forward, the next thing we need is a loop. This loop will have a variable *i* initialized to 0, and will run for as long as *i* is less than the length of our array.

Each time we go through our loop we'll increment *i* by one.

Also, if *array[i]* (some item in our array) is ever equal to *array[i+1]* (the item immediately following the previous item we just mentioned), we're going to do something.

We'll talk about that in the next step.
```
function superReducedString(s) {
  let array = s.split("");
for (let i = 0; i < array.length; i++) {
  if (array[i] === array[i + 1]) {
  } 
 }
}
```
18:01 -- So, what's the something we're doing to do if *array[i]* is equal to *array[i+1]*? It's simple.

We're going to take our array, and splice it starting at *i*, and splicing for a duration of two items.

This enables us to remove items from our array, without having "empty" items in our array as would be the case if we used the delete keyword.

After using the splice() method, we'll set the value of *i* equal to -1. This ensures that when our loop runs again, after *i* is incremented it will have a value of 0 (-1 + 1 === 0).

The reason we want *i* to have a value of 0 is that after using the splice() method, we may have new combinations of letters touching each other.

Thus, we need to go and loop through all of *array* again to see if there are any new or remaining adjacent letters that are equal to each other.
```
function superReducedString(s) {
  let array = s.split("");
for (let i = 0; i < array.length; i++) {
  if (array[i] === array[i + 1]) {
 array.splice(i, 2)
 i = -1;
  } 
 }
}
```
18:08 -- Eventually, we'll no longer have any adjacent letters that are equal to each other and we'll be able to finish looping through our variable *array*.

When this happens, we'll break out of our loop.

At this point we'll then return the result of our ternary operator as our solution to this algorithm!

If the length of *array* is greater than 0,it means we have some letters that we weren't able to "remove" from our array.

If this is the case, we'll use the .join() method on our array (because the algorithm wants our solution to be of the string data type rather than an array) and return that as our solution to this algorithm.

Otherwise, if the length of our array is 0, we'll return 'Empty String' as our solution to this algorithm.
```
function superReducedString(s) {
  let array = s.split("");
for (let i = 0; i < array.length; i++) {
  if (array[i] === array[i + 1]) {
 array.splice(i, 2)
 i = -1;
  } 
 }
return (array.length > 0? array.join(""): 'Empty String')
}
```
18:14 -- I found this algorithm to be a little bit challenging, but hopefully my algorithm solution and explanation helped clear some things up for you.

Keep working hard everyday and you and your developer skills are sure to improve! :D