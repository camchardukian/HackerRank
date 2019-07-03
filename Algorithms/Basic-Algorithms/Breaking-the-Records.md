# Breaking the Records Hackerrank Algorithm Solution

7:42 -- The first thing I did was create a function *breakingRecords* that has a parameter *scores* which takes in an array of numbers as its argument.
```
function breakingRecords(scores) {

}
```

7:44 -- Next, we need to define several variables. *maxMinRecord* will be an array whose first value represents how many times Maria broke her record for highest points in a game, and the second value represents how many times she broke her record for lowest points in a game.

Our *maximum* and *minimum* variables are intialized to the first value in the array passed in as an argument to our breakingRecords function.

The reason we use the first value in the array to initialize our variables is because Maria's first game of the reason operates as the baseline through which all further comparisons are made.
```
function breakingRecords(scores) {
  let maxMinRecord = [0, 0];
  let maximum = scores[0];
  let minimum = scores[0];
}
```
7:49 -- Next, we write a for loop that'll cycle through all the values in our *scores* array. Nested in our scores array is an *if statement* with logic that basically states, if Maria's points in her current game is greater than her previous maximum, we'll update her record to the current game's number of points and increment Maria's number of times she has broken her maximum scoring record.

We use similar logic to state that if in Maria's current game she has scored less than her minimum number of points for a single game this season, we'll update her minimum (obviously decreasing it in the process), and increment the number of times she's broken her minimum record by one.
```
function breakingRecords(scores) {
  let maxMinRecord = [0, 0];
  let maximum = scores[0];
  let minimum = scores[0];
for (let i = 0; i < scores.length; i++) {
  if (scores[i] > maximum) {
        maximum = scores[i]
        maxMinRecord[0]+=1
  }
  else if (scores[i] < minimum) {
    minimum = scores[i]
    maxMinRecord[1]+=1
  }
}
}
```
7:56 -- The only thing left to do now is join our maxMinRecord array, separating our two values by a space in the process, and then return *maxMinRecord* as our solution to the algorithm!
```
function breakingRecords(scores) {
  let maxMinRecord = [0, 0];
  let maximum = scores[0];
  let minimum = scores[0];
for (let i = 0; i < scores.length; i++) {
  if (scores[i] > maximum) {
        maximum = scores[i]
        maxMinRecord[0]+=1
  }
  else if (scores[i] < minimum) {
    minimum = scores[i]
    maxMinRecord[1]+=1
  }
}
return (maxMinRecord.join(" "))
}
```
7:58 -- I hope my explanation of this problem has helped you understand it!