19:50 -- I'm now working on the *Compare the Triplets* algorithm. Basically, this algorithm gives you two arrays.

Each array represents a person's score in some event or category. If person A scores higher, we should give them a point.

Otherwise, if person B scores higher we should give person B a point.

So, for this problem we're going to need a function that takes in two parameters:

```
function compareScoreArrays (a, b) {

}
```

The two arguments passed to this array should be arrays.

19:55 -- Now, I'm trying to figure out what should be next. I don't know if it's the most optimal way, but I think we can create a doable solution using a plain old for loop.

19:59 -- Even before adding the for loop, I just thought that it would be important to note if our two passed arrays were of different length.

Obviously, it wouldn't be a valid comparison if one person competed in 10 events and another only competed in 2.

In other words, my version of the solution will only compare two people (or two arrays) of an equal length. Here's my example code below:
```
function compareTriplets(a, b) {
if (a.length === b.length) {
  console.log("arrays are same")
}
else {
  console.log("Your arrays are of different lengths.")
}
}

compareTriplets([1, 2, 3, 4], [3, 2, 1])
```

20:03 -- The next thing I have to focus on is adding some functionality. In the above code I only log to the console.

20:07 -- Added some variables, and a for loop:
```
function compareTriplets(a, b) {
if (a.length === b.length) {
  let aScore = 0;
  let bScore = 0;
  for (let i = 0; i < a.length; i++) {
    console.log(i)
  }
}
else {
  console.log("Your arrays are of different lengths.")
}
}

compareTriplets([1, 2, 3,], [3, 2, 1])
```

20:11 -- I've completed the challenge it seems. Here's what I've created thus far:

```
function compareTriplets(a, b) {
if (a.length === b.length) {
  let aScore = 0;
  let bScore = 0;
  for (let i = 0; i < a.length; i++) {
    if (a[i] > b[i]) {
      aScore++
    }
    else if (a[i] < b[i]) {
       bScore++
    }
  }
      return [aScore, bScore]
}
else {
  console.log("Your arrays are of different lengths.")
}
}

compareTriplets([1, 2, 3,], [3, 1, 5])
```
Let's just test it in hackerrank before we go over it...

It was successful! Now let's discuss what we did.

First we have a function that takes two parameters:
>function compareTriplets(a, b) { }

The two arguments passed to this function should both be arrays.

Then we create an *if statement* to see if our two passed arrays are of equal length.
> if (a.length === b.length)

Obviously we cannot do a proper direct comparison on our arrays (or people) if the arrays are of different lengths (or the people competed in a different number of events/categories.)

For that reason our else statement simply logs an error message to the console:
```
else {
  console.log("Your arrays are of different lengths.")
}
```
Now, if our arrays are of the same length, we'll process to the if clause rather than the else clause of our if statement.

While you could have done this step using a single variable by initializing a variable to an array as such:
> let scoreArr = [0, 0]

I opted to use multiple variables as I thought having multiple variables would require less bracket notation and be easier for new developers to understand:
>   let aScore = 0; let bScore = 0;

From there, I created a for loop that would iterate just enough times to go through the entire array:
```
for (let i = 0; i < a.length; i++) {
}
```
On each iteration of the array, we checked to see if a[i] was less than or greater than b[i]. In other words we first checked it a[0] was greater than b[0], then a[1] and b[1] and so on until we'd iterated through the entire length of the array.

Each time a was greater than b, we incremented our aScore variable by one:
```
if (a[i] > b[i]) {
      aScore++
    }
```
We also did the same for our bScore when b was greater than a:
```
else if (a[i] < b[i]) {
       bScore++
    }
```
After we finished iterating through everything we returned an array that included our aScore variable and our bScore variable:
> return [aScore, bScore]

And that folks is your answer for how I solved this algorithm!

How could we have made it better? For one, I think it could have been beneficial to specify what happens if a user's array contained objects, booleans, strings, or other non-number values.

We also could have used a single variable for our player's scores instead of having two variables.

Overall, however, I think this solution is very decent.