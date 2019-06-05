```
function simpleArraySum(ar) {
    let result = 0
    for (let i = 0; i < ar.length; i++) {
        result+=ar[i]
    }
    return result
}
simpleArraySum([2, 3, 4, 5, 6, 7])
```

In this function we initialize our result to a value of 0. Then, we write a for loop and iterate through the entire length of our array. Why do we iterate through the length of our array?

The answer is simple. Our goal is to add all of the numbers in our array together. To do that, we increment our result variable by the value of ar[i] and utilizing bracket notation in this way will add the first number in our array to result, then the second number and so on until we've added all of the numbers to out array. 

Could we have completed this exercise more efficiently? Perhaps. I think we could have just as easily used reduce() and added a callback function that returned a + b. In any case, I hope you found this explanation valuable!

Example solution using the reduce method:

```
function simpleArraySum(ar) {
  const result = ar.reduce((sum, acc) => {
      return sum + acc
    }, 0)
    return result
};

simpleArraySum([2, 3, 4, 5, 6, 7])
```