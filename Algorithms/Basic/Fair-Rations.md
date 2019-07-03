# Fair Rations HackerRank Algorithm Solution

You can view the [Fair Rations algorithm here](https://www.hackerrank.com/challenges/fair-rations/problem).
___


19:28 -- Our goal is make sure each subject has an even number of loaves of bread (Note: When we say even number of loaves we don't mean equivalent number of loaves, we're simply referring to even numbers, AKA not odd numbers.)

For a full explanation of this problem, [click here](https://www.hackerrank.com/challenges/fair-rations/problem).

We have a function *fairRations* that has a parameter *B* which takes in an array of integers representing the number of loaves of bread each of our subjects currently has.

I've also declared a variable *loavesDistributed* which is initialized to 0 and is used for the purpose of counting how many total loaves of bread we've given to our kingdom's citizens.

```
function fairRations(B) {
  let loavesDistributed = 0;
}
```
19:31 -- Next, we have a for loop that iterates over all but the last item in our array. With each iteration of our loop, we see whether the current subject (B[i]) has an off number of loaves of bread. 

If so, we give a loaf of bread to the current subject (B[i]+=1). We also give a loaf of bread to the next citizen in line (B[i]+=1). Then, we note that we've just given two loaves of bread (loavesDistributed+=2).
```
function fairRations(B) {
  let loavesDistributed = 0;
for (let i = 0; i < B.length - 1; i++) {
  if (B[i] % 2 === 1) {
    B[i]+=1;
    B[i+1]+=1;
  loavesDistributed+=2
  }
 }
}
```
19:38 -- If we reach the last subject (B[B.length -1]), and they have an even number of loaves of bread ((B[B.length-1]) % 2 === 0), we return *loavesDistributed* as our solution to this algorithm because all of our citizens have an even number of loaves of bread!

Otherwise, we'll return the string "NO" as our solution because we were unable to meet the constraints set by the algorithm (we can't give the last person a loaf of bread, because if we did we'd also have to give then 2nd to last person a loaf of bread and then we'd still have one citizen with an odd number of loaves of bread).
```
function fairRations(B) {
  let loavesDistributed = 0;
for (let i = 0; i < B.length - 1; i++) {
  if (B[i] % 2 === 1) {
    B[i]+=1;
    B[i+1]+=1;
  loavesDistributed+=2
  }
 }
if ((B[B.length-1]) % 2 === 0) {
 return (loavesDistributed)
 }
else {
  return "NO"
 }
}
```
19:42 -- Way to follow through all the way to the end! If you feel you've gotten your head around this problem, try closing this file and solving the algorithm again for yourself!