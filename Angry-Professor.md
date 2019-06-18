# Angry Professor HackerRank Algorithm Solution

You can find the [Angry Professor algorithm here](https://www.hackerrank.com/challenges/angry-professor/problem).


18:19 -- Let's talk about how one may approach this algorithm. First of all, we have a function *angryProfessor* which has two parameters *k* (an integer representing the threshold number of students required to hold class), and *a* (an array representing the times students arrived to class).
```
function angryProfessor(k, a) {

}
```
18:21 -- Before going any further, we should note negative integers in our *a* array represent students that arrived before class, **0** represents students that arrived "exactly on-time" and thus count towards the professor's count for present students, and positive integers represent students that arrived a certain number of minutes (or any unit of time really) after class started, and thus do not count towards the professor's tally of timely students.

That explanation aside, you'll see I also defined an additional two variables: initialized to 0 is *timelyStudents* an integer representing the number of students that arrived to class at or before its intended start time, and initialized to an empty string is *professorDecision* which represents whether the professor is choosing to cancel class or not:
```
function angryProfessor(k, a) {
let timelyStudents = 0;
let professorDecision = "";
for (let i = 0; i < a.length; i++) {
  if (a[i] <= 0) {
    timelyStudents++
  }
}
timelyStudents < k ? professorDecision = "YES" : professorDecision = "NO";
return professorDecision;
}
```
18:26 -- Moving on, we can use a for loop to cycle through all of the students in the professor's class. If they arrived before class or on-time (an integer equal to or less than 0), we increment the number of *timelyStudent* by one.

Otherwise, we do nothing. After looping through all of the students, we can use a ternary operator to set the value of *professorDecision*.

If *timelyStudents* is less than the threshold number of students needed to hold class *k* we set the value of *professorDecision* to "YES" because class is canceled. Otherwise, we'd set its value to "NO".

Then, we return *professorDecision* as our solution to this algorithm!

```
function angryProfessor(k, a) {
let timelyStudents = 0;
let professorDecision = "";
for (let i = 0; i < a.length; i++) {
  if (a[i] <= 0) {
    timelyStudents++
  }
}
timelyStudents < k ? professorDecision = "YES" : professorDecision = "NO";
return professorDecision;
}
```
That wasn't too bad was it? :D