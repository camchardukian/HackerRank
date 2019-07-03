# Apple and Orange Hackerrank Algorithm Solution

21:28 -- Oh man, this problem has a lot of stuff going on. First, we've got an apple tree and an orange tree sitting on a single x-axis.

Our job is to build a function with a bunch of parameters that'll identify how many apples and oranges fall on farmer Sam's house.

21:31 -- Here's some of the information they give us on parameters for our function:
```
s: integer, starting point of Sam's house location.
t: integer, ending location of Sam's house location.
a: integer, location of the Apple tree.
b: integer, location of the Orange tree.
apples: integer array, distances at which each apple falls from the tree.
oranges: integer array, distances at which each orange falls from the tree.
```
and some additional information:
```
The first line contains two space-separated integers denoting the respective values of  and. 
The second line contains two space-separated integers denoting the respective values of  and. 
The third line contains two space-separated integers denoting the respective values of  and. 
The fourth line contains  space-separated integers denoting the respective distances that each apple falls from point. 
The fifth line contains  space-separated integers denoting the respective distances that each orange falls from point.
```
Anyway, this is a lot of information to process at one time. Let's try to add one parameter at a time and go from there.

21:38 -- One step at a time. Get a working function and start to see what each variable represents:
```
function countApplesAndOranges(s, t, a, b, apples, oranges) {
console.log(`Sam's house extends from ${s} to ${t}`)
}
countApplesAndOranges(7, 10);
```
___
21:47 -- Just got back from a 5-8 minute break. Let's keep going!

21:51 -- I've gotten my basic function and passed arguments to all of my variables:
```
function countApplesAndOranges(s, t, a, b, apples, oranges) {
console.log(`Sam's house extends from ${s} to ${t}`)
console.log(`The apple tree is at ${a}`)
console.log(`The orange tree is at ${b}`)
console.log(`The apples fell at ${apples}`)
console.log(`The oranges fell at ${oranges}`)
}
countApplesAndOranges(7, 10, 4, 12, [2, 3, -4], [3,-2, -4]);
```
Now I just need to add some basic logic to figure out where everything fell...

21:58 -- Making progress:
```
function countApplesAndOranges(s, t, a, b, apples, oranges) {
console.log(`Sam's house extends from ${s} to ${t}`)
console.log(`The apple tree is at ${a}`)
console.log(`The orange tree is at ${b}`)
console.log(`The apples fell at ${apples}`)
console.log(`The oranges fell at ${oranges}`)
  let counter = 0;
for (let i = 0; i < apples.length; i++) {
  if (a + apples[i] >= s && a + apples[i] <= t) {
    counter+=1
  }
}
  console.log(counter)
}
countApplesAndOranges(7, 10, 4, 12, [2, 3, -4], [3,-2, -4]);
```
I feel like this algorithm is simple enough for me to work through despite my extreme fatigue. But actually explaining everything, don't get me thinking about that now lol.

Anyway, let me give it a shot. Let Tony Robbins says, you can choose to change your state.

Whoaa. I reread that last sentence like 4 times before I realized I made a spelling error hahaha.

So... in the previous step, we initialized a counter variable to 0. We then wrote a basic for loop that runs for as long as *i* is less than the length of our apples array. 

We then used the logic that if we take the position of our apple tree 'a' and add it to how far the apple fell from the tree, we can then calculate where the apple landed.

If the apple landed between the beginning of Sam's house 's' and the end of Sam's house 't' we can then conclude that the apple landed on Sam's house and the result is that we increment our counter variable.

Finally, after exiting our for loop we log to the console how many apples fell on Sam's house.

The cool thing, is we can apply almost the same logic for oranges. We just have to switch out the apple tree for the orange tree and the apples array for the orange array.

And here we go, the final solution!
```
function countApplesAndOranges(s, t, a, b, apples, oranges) {
  let counter = 0;
for (let i = 0; i < apples.length; i++) {
  if (a + apples[i] >= s && a + apples[i] <= t) {
    counter+=1
  }
}
  console.log(counter)
  counter = 0;
  for (let i = 0; i < oranges.length; i++) {
    if (b + oranges[i] >= s && b + oranges[i] <= t) {
      counter+=1}
  }
  console.log(counter)
}