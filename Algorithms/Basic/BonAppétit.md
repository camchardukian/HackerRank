# Bon Appétit Hackerrank Algorithm Solution

You can find the [Bon Appétit HackerRank algorithm here](https://www.hackerrank.com/challenges/bon-appetit/problem).

11:46 -- Let's break this problem down. The first thing we need to do is write a function *bonAppetit* that has three parameters: *bill*, *k*, and *b*.

The value passed to *bill* will be an array of integers representing the cost of each item ordered.

*k* is an integer that represents which item in the *bill* array Anna doesn't eat.

*b* is how much money Anna originally contributed to the bill.

Here's our basic function, and function call:
```
function bonAppetit(bill, k, b) {

}
bonAppetit([2, 1, 8, 10], 1, 10.5)
```
Also, a quick note: I'm showing this function call to help you visualize what we're working with. You shouldn't actually include it when submitting your algorithm (doing so will result in your solution failing the test cases).

11:53 -- Next, we need to total the cost of all of the items ordered to figure out how much their dinner actually costs.

We can do this by intializing a variable *total* to 0, and then using a for loop and adding (incrementing by the value of) each item in our bill array:
```
function bonAppetit(bill, k, b) {
  let total = 0;
for (let i = 0; i < bill.length; i++) {
total+= bill[i]
}
}
```
The final thing we need to add is our conditional logic. If we take our *total* which represents how much the meal costs, and minus the value of the item Anna was allergic to *bill[k]*, we can divide it by two to see how much money Anna should pay.

If the result of the previous operation is equal to what Anna actually paid *b*, we log 'Bon Appetit' to the console. 

If Anna paid too much, we can calculate her change by subtracting how much she should have paid by what she actually paid.

For humor purposes, I also added a scenario in which Anna runs away with extra money, and an all encompassing error message (if for example the user passed a string instead of an integer to our *b* variable).

Final solution:
```
function bonAppetit(bill, k, b) {
  let total = 0;
for (let i = 0; i < bill.length; i++) {
total+= bill[i]
}
if ((total - bill[k])/ 2 === b) {
  console.log('Bon Appetit')
}
else if ((total - bill[k])/ 2 < b) {
console.log(b - (total - bill[k])/ 2)
}
else if ((total - bill[k])/ 2 > b)  {
  console.log("Anna is running away with the extra $$$")
}
else {
  console.log("Please double check the inputs and try again.")
  }
}
```