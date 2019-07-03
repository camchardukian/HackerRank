# Beautiful Days at the Movies HackerRank Algorithm Solution

You can find the [Beautiful Days at the Movies algorithm here](https://www.hackerrank.com/challenges/beautiful-days-at-the-movies/problem).


22:58 --  We have a function *beautifulDays* which has three parameters -- *i*, an integer which represents the start date, *j*, an integer which represents the end date, and *k*, an integer which represents the "magical divisor" which will help us evaluate whether a day is beautiful or not.

```
function beautifulDays(i, j, k) {

}
```
23:04 -- I've also defined three additional variables *beautifulDays*, *reversedDays*, and *days*, all of which are initialized to empty arrays.
```
function beautifulDays(i, j, k) {
  let beautifulDays = [];
  let reversedDays = [];
  let days = [];
}
```
23:05 -- Next, with our first for loop we're going to loop through all of the integers between and including *i* and *j*, pushing each integer to our *days* array in the process. 

We'll also take each integer's inverse (21 --> 12 for example), and push said inverse to the *reversedDays* array.
```
function beautifulDays(i, j, k) {
  let beautifulDays = [];
  let reversedDays = [];
  let days = [];
for (let inc = i; inc <= j; inc++) {
days.push(inc);
  reversedDays.push(String(inc).split("").reverse().join(""))
}
```
23:08 -- Now that we have completed *days* and *reversedDays* arrays, we can loop through them and subtract the value of each item in the *reversedDays* array from its corresponding value in the *days*.

Note: During this process, we need to use the *parseInt* method because the items in our *reversedDays* array are actually strings and not integers. Thus, we need to convert said strings into integers.

If
>(days[inc] - parseInt(reversedDays[inc])) is divisible by *k* without having any remainder, we'll push the value of days[inc] to our *beautifulDays* array.

Finally, after we break out of our for loop, we'll return beautifulDays.length as the solution to our algorithm!
```
function beautifulDays(i, j, k) {
  let beautifulDays = [];
  let reversedDays = [];
  let days = [];
for (let inc = i; inc <= j; inc++) {
days.push(inc);
  reversedDays.push(String(inc).split("").reverse().join(""))
}

for (let inc = 0; inc < days.length; inc++) {
  if ((days[inc] - parseInt(reversedDays[inc])) % k === 0) {
    beautifulDays.push(days[inc])
  }
}
return beautifulDays.length
}
```
Way to go on making it through our entire walkthrough of this algorithm!