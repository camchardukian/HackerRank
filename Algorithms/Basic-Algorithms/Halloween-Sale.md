# Halloween Sale HackerRank Algorithm Solution

You can view the [Halloween Sale algorithm on HackerRank here](https://www.hackerrank.com/challenges/halloween-sale/problem).
___


21:46 -- It looks like we're trying to buy video games from an online video game store. We're in luck, however, because the store has a Halloween sale going on.

Our job is to determine how many video games we can purchase based on the following parameters:
* *p* -- An integer representing the  price for the first video game one purchases during the sale.
* *d* -- An integer representing the discount applied (with discount stacking possible) for each additional game purchased after the first video game.
* *m* -- An integer representing the minimum cost for a single video game. Once this price is reached, the discounts from *d* can no longer be applied.
* *s* -- An integer representing the number of dollars we have available for spending.

Here's our basic setup:
```
function howManyGames(p, d, m, s) {

}
```
21:48 -- The next thing we're going to need is a few variables. We'll need a counter to count how many video games we've already purchased.

I've declared a variable *totalGamesPurchased* and initialized it to 0.

We're also going to want another variable *currentCost*. The reason we want this second variable is that our cost per video game will decrease as we purchase more games.

We'll initialize this second variable to the value of *p*.

One question you may have is why we need to declare another variable when we could have just used the value *p*.

In reality, either method is workable. The reason I'm declaring an additional variable, however, is because I think doing so will make my code more readable for you.
```
function howManyGames(p, d, m, s) {
let totalGamesPurchased = 0;
let currentCost = p;
    }
```
21:53 -- Moving forward, the next thing we need to do is subtract the cost of a game from our amount of money.

This is probably going to be a repeatable action -- something we're done multiple times.

We know this because we're probably going to buy multiple games to take advantage of the sales promotion at the store.

That's why we're using a loop. Our loop will continue running for as long as our amount of money (*s*) is greater than or equal to the cost of the next game with any applicable discounts applied(*currentCost*).
```
function howManyGames(p, d, m, s) {
let totalGamesPurchased = 0;
let currentCost = p;
while (s >= currentCost) {
    }
}
```
21:57 -- Finally, let's talk about the logic that we're going to put inside of our loop.

Each time we go through our loop, we're going to decrement *s* by *currentCost*. We do this because obviously our money will decrease each time we purchase another game.

We'll also increment *totalGamesPurchased* by one because if we have enough money for our loop to continue running, we obviously had enough money for us to purchase a game.

While we won't take any discounts into account the first time around (per HackerRank's instructions), the 2nd, 3rd, 4th time etc, we're going to need to pay attention to any applicable discounts.

Keeping in mind that our *currentCost* or the cost of a single video game will never be less than the minimum cost *m*, we can use the following logic:

> If the cost of our video game is decreased by the value of our discount, will our video game's cost still be greater than or equal to the minimum cost *m*? 

If so, we'll set the value of *currentCost* equal to the value of *currentCost* decremented by the value of our discount *d* (to account for the discount the next time we go through our loop).

Otherwise, if stacking another discount onto our current price would put us below the allowed minimum cost, we'll simply set *currentCost* equal to the minimum permissible cost *m*.

We'll go through this process as long as our money *s* remains greater than or equal to the cost of the next video game *currentCost*.

When this eventually stops being true, we'll break out of our loop and return *totalGamesPurchased* as our solution to this algorithm!
```
function howManyGames(p, d, m, s) {
let totalGamesPurchased = 0;
let currentCost = p;
while (s >= currentCost) {
s-= currentCost
totalGamesPurchased+=1
if (currentCost - d >= m) {
  currentCost-=d
    }
else {
  currentCost = m
    }   
  }
  return totalGamesPurchased
}
```
22:08 -- Way to stick with it. You made it all the way through the 'Halloween Sale' algorithm!