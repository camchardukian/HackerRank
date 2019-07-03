# Birthday Cake Candles Hackerrank Algorithm Solution

22:27 -- The first thing we need to do is define the problem. We have our niece's birthday party and we want to give her one candle for each year she has lived.

However, some of the candles will be of different heights. Our niece can only blow out the tallest candles. Our job is to find the tallest candle(s) and see how many of them there are.

To do this, we need to look at the array of numbers that is passed to our function. If the array of numbers is the following:
> [5, 2, 3, 2, 5]

We should log **2** to the console because our largest number in the array is 5, and that number is repeated two times.

22:33 -- Now I'll take a few minutes to start actually implementing the code...

22:36 -- Here's my basic setup thus far...
```
function birthdayCakeCandles(ar) {
  let counter = 0;
for (let i = 0; i < ar.length; i++) {
  console.log(ar[i])
}
}
birthdayCakeCandles([1, 5, 2, 3, 3, 3, 4, 2, 5, ])
```
22:43 -- I've added functionality for determining whether the next number in the array is greater than/equal to, or less than the current number in the array.
```
function birthdayCakeCandles(ar) {
  let counter = 0;
for (let i = 0; i < ar.length; i++) {
  if (ar[i] < ar[i+1] ) {
  console.log(ar[i] + "is less than" + ar[i + 1])
}
else if (ar[i] >= ar[i + 1]) {
  console.log(ar[i] + "is more than or equal to" + ar[i+1])
}
else {
  console.log("you at da end of da array bro")
}
}
}
birthdayCakeCandles([1, 5, 2, 3, 3, 3, 4, 2, 5,])
```
The next logical step is increasing or resetting my counter based on this information.

22:50 -- Code has gotten pretty ugly:
```
function birthdayCakeCandles(ar) {
  let counter = 0;
  let currentNumber = 0;
for (let i = 0; i < ar.length; i++) {
  if (currentNumber < ar[i+1] ) {
  counter = 0
  currentNumber = ar[i+1]
  console.log(currentNumber)
}
else if (currentNumber >= ar[i + 1]) {
  counter+=1
}
else {
  if (counter === 0) {
    counter += 1
  }
}
}
return counter
}
birthdayCakeCandles([1, 5, 2, 3, 3, 3, 4, 2, 5])
```
I need to rethink about what I'm doing...

23:00 -- I did it!! Finished at 23:00 *EXACTLY*

Here was my code that I couldn't figure out why it wasn't working:
```
function birthdayCakeCandles(ar) {
  let counter = 0;
  let currentNumber = 0;
for (let i = 0; i < ar.length; i++){
  console.log("current number is: " + currentNumber)
  if (currentNumber < ar[i+1] ) {
  counter = 1
  currentNumber = ar[i+1]
  console.log("if clause" + currentNumber)
}
else if (currentNumber = ar[i + 1]) {
  counter+=1
  console.log("ELSE IF clause" + currentNumber)
}
else {
  console.log(currentNumber + " is greater than " + ar[i+1])
}
}
return counter
}
birthdayCakeCandles([1, 5, 2, 3, 3, 3, 4, 2, 5])
```
For a loooong time, I couldn't figure out why it wasn't working. It turns out, the problem was that in my else if clause I was accidentally assigning currentNumber that value of ar[i+1] using a single equals sign rather than comparing them using double or triple equals. 

Here is my complete solution that passed hackerrank's tests...

Actually, it doesn't.

23:11 -- I had to do a little bit of debugging, but anyway, here's my final solution that passed all of hackerrank's algorithms:
```
function birthdayCakeCandles(ar) {
  let counter = 0;
  let biggestNumber = 0;
for (let i = 0; i < ar.length; i++){
  if (biggestNumber < ar[i] ) {
  counter = 1
  biggestNumber = ar[i]
}
else if (biggestNumber === ar[i]) {
  counter+=1
}
}
return counter // this is where we return the answer hackerrank is looking for.
}
birthdayCakeCandles([3, 2, 1, 3, 3, 3, 2,])
```
Let me explain what's going on here...
1. We have a function *birthdayCakeCandles* that has a parameter *ar*.
1. We initialize our *counter* and *biggestNumber* variables to 0.
1. We create a for loop that has a variable *i* initalized to 0, increments by 1 each time the loop is run, and continues running until *i* is no longer less than the length of our array.
1. If the value of *biggestNumber* is less than *ar[i]*, we set our *counter* variable to 1 and set our *currentValue* variable to the value of *ar[i]*. *Why?* Because if *ar[i]* is greater than *biggestNumber* it's obvious that what we thought was the biggestNumber (or tallest candle) was not in fact the biggest candle. It's also of course important for us to reset out counter variable to 1 if we find a new biggest candle.
1. If our *biggestNumber* variable is equal to *ar[i]* we can increment counter by one because we know that our biggest candle has at least one (or more if we repeat this scenario multiple times) fellow candle(s) of an equivalent height.
1. Finally, we return the value of counter, which is the expected output for hackerrank!