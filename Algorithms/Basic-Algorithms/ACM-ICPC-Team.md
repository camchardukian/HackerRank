# ACM ICPC Team HackerRank Algorithm Solution

You can view the [ACM ICPC Team algorithm on HackerRank here](https://www.hackerrank.com/challenges/acm-icpc-team/problem).
___


19:21 -- It looks like we have some people attending the ACM-ICPC World Finals (a programming contest).

Given a list of topics known by each attendee (zeros represent not known while ones represent known), determine the maximum numbers of topics a 2-person team can know.

We also need to determine how many different ways a team could be formed that would know the maximum number of topics we just calculated.

We have a function *acmTeam* that has a single parameter *topic*, which takes in a string of binary digits.

Here's our basic setup:
```
function acmTeam(topic) {

}
```
19:22 -- Now that we talked about what we're trying to do in this problem and we've gotten our function's skeleton all written out, let's talk about variables.

Our solution is going to utilize a few variables:
* *highestTopicsKnown*: An integer representing the maximum number of topics any of our teams know.
* *numberOfTopTeams*: An integer representing how many teams know the maximum numbers of topics (*highestTopicsKnown*).
* *currentTopicsKnown*: An integer representing how many topics our current team knows.

All of the above variables can be initialized to 0.
```
function acmTeam(topic) {
let highestTopicsKnown = 0;
let numberOfTopTeams = 0;
let currentTopicsKnown = 0;
}
```
19:28 --  Next, we need several loops. Our first loop will loop through all of the people in our array *topic*.

Our 2nd layer for loop will also iterate through the people in our array, but this for loop will start with its position being the person after whoever the outer for loop currently has selected (i + 1).

These two for loops will work together to compare every possible combination of teams (of 2 individuals) possible.

For example if we have 4 individuals our for loops will run like this.
```
i = 0
ii = 1
ii = 2
ii = 3
i = 1
ii = 2
ii = 3
i = 2
ii = 3
```

Each time we run through our 2nd layer for loop, we're also going to update the value of *currentTopicsKnown* to 0.

We're doing this because it doesn't matter how many topics previous potential teams had, we're only concerned with how many topics our current combination of individuals (will) know.

Hopefully, you're following along alright thus far. Here's a view of our code as things currently stand :)
```
function acmTeam(topic) {
let highestTopicsKnown = 0;
let numberOfTopTeams = 0;
let currentTopicsKnown = 0;
for (let i = 0; i < topic.length; i++) {
  for (let ii = i + 1; ii < topic.length; ii++) {
  }
 }
}
```
19:35 -- Now, we're going to need one more for loop. This 3rd layer for loop will iterate through each possible topic.

We'll then check to see where either person 'a' (topic[i][j]) or person 'b' (topic[i][j]) knows topic 'j' (topic[i][j] === '1' || topic[ii][j] === '1').

If so, we'll increment *currentTopicsKnown* by 1. If not, we'll continue repeating this 3rd layer for loop until we've run out of topics.
```
function acmTeam(topic) {
let highestTopicsKnown = 0;
let numberOfTopTeams = 0;
let currentTopicsKnown = 0;
for (let i = 0; i < topic.length; i++) {
  for (let ii = i + 1; ii < topic.length; ii++) {
      currentTopicsKnown = 0
    for (let j = 0; j < topic[i].length; j++) {
    if (topic[i][j] === '1' || topic[ii][j] === '1') {
      currentTopicsKnown+=1
    }
   }
  }
 }
}
```
19:38 -- After we've run through all of our topics, we'll break out of our 3rd layer for loop and reach an if statement.

This if statement uses the logic that if *currentTopicsKnown* is greater than the amount of topics any previous team had known *highestTopicsKnown*, we'll update the value of *highestTopicsKnown* to *currentTopicsKnown*.

Of course, if this was the case, we'd also have to update the value of *numberOfTopTeams* to 1. This is because at this time, only 1 team would have the record for greatest number of topics known.
```
function acmTeam(topic) {
let highestTopicsKnown = 0;
let numberOfTopTeams = 0;
let currentTopicsKnown = 0;
for (let i = 0; i < topic.length; i++) {
  for (let ii = i + 1; ii < topic.length; ii++) {
      currentTopicsKnown = 0
    for (let j = 0; j < topic[i].length; j++) {
    if (topic[i][j] === '1' || topic[ii][j] === '1') {
      currentTopicsKnown+=1
    }
   }
   if (currentTopicsKnown > highestTopicsKnown) {
     highestTopicsKnown = currentTopicsKnown
     numberOfTopTeams = 1
   }
  }
 }
}
```
19:44 -- Finally, if the value of *currentTopicsKnown* was equal to *highestTopicsknown* after breaking out of our 3rd layer for loop, we'd know that 2 or more teams shared the record for *highestTopicsKnown*.

Thus, we'd increment *numberOfTopTeams* by 1.

We'd then go through all of our 3 for loops again and again until we eventually broke out of all of them.

When that happens, we can return an array containing *highestTopicsKnown* and *numberOfTopTeams* as our solution to this algorithm!
```
function acmTeam(topic) {
let highestTopicsKnown = 0;
let numberOfTopTeams = 0;
let currentTopicsKnown = 0;
for (let i = 0; i < topic.length; i++) {
  for (let ii = i + 1; ii < topic.length; ii++) {
      currentTopicsKnown = 0
    for (let j = 0; j < topic[i].length; j++) {
    if (topic[i][j] === '1' || topic[ii][j] === '1') {
      currentTopicsKnown+=1
    }
   }
   if (currentTopicsKnown > highestTopicsKnown) {
     highestTopicsKnown = currentTopicsKnown
     numberOfTopTeams = 1
   }
   else if (currentTopicsKnown === highestTopicsKnown) {
     numberOfTopTeams +=1
   }
  }
 }
 return [highestTopicsKnown, numberOfTopTeams]
}
```
19:47 -- Way to stick with it. We're done!