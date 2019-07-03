# Mars Exploration HackerRank Algorithm Solution

You can view the [Mars Exploration algorithm on HackerRank here](https://www.hackerrank.com/challenges/mars-exploration/problem).
___

10:59 -- Sami's spaceship has crashed on Mars. She's trying to send 'SOS' messages to Earth.

Unfortunately, some of the 'SOS' messages have gotten altered from cosmic radiation. We have a function *marsExploration*.

Given the string *s*, our job is to evaluate how many characters got altered during the message transmission process.

Here's our basic setup:
```
function marsExploration(s) {

}
```
11:00 -- The first thing we need to do is create a few variables. I've created a variable *counter* initialized to **0**, and another variable *unalteredString* initialized to an empty string.

We'll use *unalteredString* to repeat 'SOS', however many times is necessary to produce Sami's original message.

We can do this with a while loop using the logic that as long as the length of *unalteredString* is less than the length of *s*, we'll update the value of *unalteredString* to equal *unalteredString* and the string 'SOS' mashed together using concatenation(concatenating is kind of like adding two strings together).
```
function marsExploration(s) {
    let counter = 0;
    let unalteredString = '';
    while (unalteredString.length < s.length) {
        unalteredString = unalteredString.concat('SOS')
    }
}
```
11:13 -- Now that the length of *unalteredString* is at least as long as *s*, we can use a for loop to count how many differences there are between the two.

We'll set our for loop to continue running for as long as our variable *i* is less than the length of *s*.

If at any point *s[i]* does not equal *unalteredString[i]* we'll increment our variable *counter* by one.

In other words, each time the first letter or second letter or third letter and so on of *s*, are not equal to the first letter second letter or third letter and so on of *unalteredString*, we'll know the message got altered during the process of cosmic radiation and thus we need to increment our counter variable by 1.

When we eventually break out of this for loop, we can return *counter* as our solution to this algorithm!
```
function marsExploration(s) {
    let counter = 0;
    let unalteredString = '';
    while (unalteredString.length < s.length) {
        unalteredString = unalteredString.concat('SOS')
    }

    for (let i = 0; i < s.length; i++) {
        if (s[i] !== unalteredString[i]) {
            counter += 1
        }
    }
    return counter
}
```
11:19 -- We're done. Way to go!