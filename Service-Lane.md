# Service Lane HackerRank Algorithm Solution

You can view the [Service Lane algorithm here](https://www.hackerrank.com/challenges/service-lane/problem).
___


17:51 -- Note: the user tests for this algorithm are a bit problematic. For that reason, around line 43 you need to change the *main* function to the following in order for your tests to pass and your solution to be accepted:
```
function main() {
    const ws = fs.createWriteStream(process.env.OUTPUT_PATH)

    const [n, t] = [...readLine().split(' ')].map(x => parseInt(x, 10))
    const width = readLine().split(' ').map(x => parseInt(x, 10))
    const cases = Array(t).fill(0).map(x => readLine().split(' ').map(y => parseInt(y, 10)))
    let result = serviceLane(width, cases)

    ws.write(result.join("\n") + "\n")
    ws.end()
}
```
17:52 -- That small disclaimer aside, let's explain our solution. We have a function *serviceLane* with two parameters *n*: an array of integers representing the various widths within the service lane, and *cases*, a 2-d array of integers representing the various test cases where we're trying to pull into the service lane, and we need to see how wide the service lane is thoughout to see the maximum width a vehicle could possibly be for it to be capable of driving through the service lane.
```
function serviceLane(n, cases) {

}
```
17:57 -- I've also defined a few additional variables: *maxWidth* which is initialized to 0, and represents the maximum possible width a vehicle could be and still drive through all assigned parts of the service lane, and *resultsArray* which is initialized to an empty array and will later be used to hold the results produced from our various test cases.
```
function serviceLane(n, cases) {
  let maxWidth = Infinity;
  let resultsArray = [];
}
```
18:01 -- Next, we're going to use a for loop to iterate through each item in *cases*. Also note, that each time through our array we're going to update the value of *maxWidth* to Infinity.

We're doing this because each time we evaluate a new test case, we want to have a "fresh start" so to speak.

For example, it doesn't matter if a smart car was capable of driving through the previous test case if we're now evaluating a wider portion of the service lane and a school bus could now pass the user tests.
```
function serviceLane(n, cases) {
  let maxWidth = Infinity;
  let resultsArray = [];
for (let i = 0; i < cases.length; i++) {
  maxWidth = Infinity;
 }
}
```
18:05 -- Next, we need a nested for loop. Our nested for loop will iterate between all of the array items in *n* starting at the value of *cases[i][0]* (the first point in a given ordered pair from the *cases* array), and ending at *cases[i][1]* (the second point in a given ordered pair from the *cases* array).

Within this loop, we've added an if statement that says if at any point *n[ii]* is less than *maxWidth*, we'll update the value of *maxWidth* to equal *n[ii]*.

After each iteration of our nested for loop, we'll take the value of *maxWidth* and push it to *resultsArray*.

After we finish pushing, we'll then enter the next cycle of our outer for loop beginning with updating the value of *maxWidth* to **Infinity** and repeating all of the previous steps.

Eventually, after we finish cycling through both of our for loops the necessary amount of times, we'll return *resultsArray* as our solution to this algorithm!
```
function serviceLane(n, cases) {
  let maxWidth = Infinity;
  let resultsArray = [];
for (let i = 0; i < cases.length; i++) {
  maxWidth = Infinity;
  for (let ii = cases[i][0]; ii <= cases[i][1]; ii++) {
    if (n[ii] < maxWidth) {
      maxWidth = n[ii]
    }
  }
 resultsArray.push(maxWidth)
}
return resultsArray
}
```
18:12 -- Remember to view my disclaimer at the top of this file and change your *main* function on HackerRank if your test cases are not passing. Of course, if you're just playing around on repl.it, you won't have to worry about doing anything with *main*.

You're finished. Way to go!