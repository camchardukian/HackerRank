# Time Conversion Hackerrank Algorithm Solution

17:46 -- First we create a function *timeConversions* which has a parameter *s* that takes in a string for an argument. We also initialize our result variable to an empty array.
```
function timeConversion(s) {
  let result = [];
}
```
17:48 -- Next, we use a for loop to loop through the string passed to *s*, pushing everything except for "AM" or "PM" to our results array.
```
  for (let i = 0; i < s.length - 2; i++) {
  result.push(s[i])
}
```
17:50 -- Moving on, the next thing we need to identify is whether our string passed to *s* contains "AM". We can do this using the indexOf() method.
```
s.indexOf("AM")
```
17:52 -- If our string contains "AM" we can simply join our results array (converting it to a string in the process), return that, and we're finished... Unless we have a situation like 12:15A.M. or 12:30A.M.

12:15am in the 24-hour system should display as 00:15. For that reason, we add an additional *if statement* saying that if our array starts with "12" (i.e. the first item is 1 and the second item is 2), we convert the first two items in our array to 0 in order to correctly display our time as starting at the 0th hour.
```
function timeConversion(s) {
  let result = [];
  for (let i = 0; i < s.length - 2; i++) {
  result.push(s[i])
}
if (s.indexOf("AM") != -1) {
  if (result[0] > 0 && result[1] == 2) {
result[0] = 0
result[1] = 0
result = result.join("");
  }
  else {
result = result.join("");
}
}
```
18:01 -- If our string doesn't contain "AM", however, we'd then proceed to our else clause in which we'd add 12 (by adding 1 to our array's first item and adding 2 to our arrays second item) to properly format our "PM" times to the 24-hour system.
>07P.M. --> 19

>10P.M. --> 22

>01P.M. --> 13

18:04 -- The one exception of course would be if we had 12pm. If we have 12pm, we don't want to add 12 because the time is already formatted properly and the 24th hour doesn't exist:
> 12:30P.M. --> 24:30
This obviously isn't what we're looking for. In the case of a P.M. formatted string, we can just return it as is (without including the P.M. of course!)

18:07 -- We've now gone through every scenario and can return our string!
```
function timeConversion(s) {
  let result = [];
  for (let i = 0; i < s.length - 2; i++) {
  result.push(s[i])
}
if (s.indexOf("AM") != -1) {
  if (result[0] > 0 && result[1] == 2) {
result[0] = 0
result[1] = 0
result = result.join("");
  }
  else {
result = result.join("");
}
}


else {
  if (result[0] > 0 && result[1] < 2) {
 result[0] = parseInt(result[0])+ 1;
 result[1] = parseInt(result[1]) + 2;
 result = result.join("");
  }

  else if (result[0] > 0 && result[1] == 2) {
  result = result.join("");
}

  else {
      result[1] = parseInt(result[1])+ 12;
      result.shift();
      result = result.join("");
  }

}
return result
}
timeConversion("12:05:45AM")
```
18:08 -- I hope that walking through this algorithm together helped you understand it!