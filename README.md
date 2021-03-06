# JS Fundamentals Checkpoint 6 Drills

## 1
**Learning:** basic arithmetic operations, precedence

**Question:** Write a function named `celciusToFahrenheit` that accepts a numeric parameter named `celcius` representing a temperature in degrees celcius. Return the temperature converted to degrees fahrenheit. Remember that the formula to convert celcius to fahrenheit is `fahrenheit = (celcius x 9/5) + 32`.

**Solution:**

```
  function celciusToFahrenheit(celcius) {
    return (celcius * 9/5) + 32;
  }
```

## 2
**Learning:** basic arithmetic operations, Math object

**Question:** Write a function named `circleArea` that accepts a single numeric value named `r` representing the radius of a circle. Return the area of teh circle using the formula `area = PI x r^2`.

**Solution:**

```
function circleArea(r) {
  return Math.PI * Math.pow(r, 2);
}
```

## 3
**Learning:** arithmetic expressions, modulus, numeric types are not integers, string construction using template literals

**Question:** Write a function named `integerDivision` that accepts two numbers named `a` and `b` and calculates the integer value `a/b` and the remainder after division. Then return a string in the format `"a / b is quotient with remainder r"`. 

*Hint: which method of the Math object will give you just the integer part of a number?* 

**Solution:**

```
function integerDivision(a, b) {
  let quotient = Math.trunc(a / b);
  let remainder = a % b;
  return `${a} / ${b} is ${quotient} with remainder ${remainder}`;
}
```

## 4
**Learning:** simple conditional, basic validation

**Question:** Revisit the integer division question from above. In that question we did not consider what happens if the function was called with the parameter b = 0. Since division by zero is not defined it would not be possible to perform that operation. Write a new function that provides the same functionality as `integerDivision` but if `b = 0` returns `'Sorry, cannot divide by zero'` instead.

**Solution:**

```
function integerDivision2(a, b) {
  if(b == 0) {
    return 'Sorry, cannot divide by zero';
  } else {
    return integerDivision(a, b);
  }
}
```

## 5

**Learning:** Math object, arithmetic expressions

**Question:** Write a function named `hypotenuse` that takes two numbers `a` and `b` that represents the two sides of a right angled triangle. Return the length of the hypotenuse, named c, of the triangle using the formula: `a^2 + b^2 = c^2`.

**Solution:**

```
function hypotenuse(a, b) {
  return Math.sqrt(Math.pow(a, 2) + Math.pow(b, 2));
}
```

## 6
**Learning:** conditional operators, boolean types, returning booleans, evaluating boolean expressions

**Question:** Write a function named `canFit` that accepts three parameters `a`, `b`, and `r` where `a` and `d` are the lengths of two sides of a right angled triangle and `r` is the radius of a circle. A triangle can fit inside of a circle if the hypotenuse of the triangle is less than or equal to the radius of the circle. Return true if the triangle with sides `a` and `b` can fit inside the circle with radius `r`, false otherwise.

**Solution:**

```
function canFit(a, b, r) {
  const hyp = hypotenuse(a, b);
  return hyp <= r;
}
```

## 7

**Learning:** modulus, returning booleans

**Question:** Write a function named `isOdd` that accepts a single value `n`. Return true is `n` is an odd number, false otherwise.

**Solution:**

```
function isOdd(n) {
  return n % 2 == 1;
}
```

## 8
**Learning:** random number generator, random range, invoking functions, predicate functions, basic conditional, modulus

**Question:** Write a function named `pinGenerator` that generates a random 5 digit PIN. The PIN must be an even number. 

*Hints: How would you generate a 5 digit random integer? How can you check if the number is odd? If it is odd, what can you do to make it even?*

**Solution:**

```

function pinGenerator() {
  const min = 10000;
  const max = 99999;
  const ran = Math.round(Math.random() * (max - min) + min);
  if (isOdd(ran)) {
    ran = ran + 1;
  }
  return ran;
}
```

## 9
**Learning:** Sequential steps, mutating variables, modulus, constructing strings with template literals

**Question:** Write a function named `coinChange` that accepts a single parameter `n` representing an amount of money between 0 and 100 inclusive. Calculate the number of coins necessary to make up that amount of money. For instance to make $0.12 you need a ten cent piece and 2 one cent pieces. Return a string in the format: `'0 25 cent pieces, 1 ten cent pieces, 0 five cent pieces and 2 one cent pieces'`

**Solution:**

```
function coinChange(n) {
  const quarters = Math.trunc(n / 25);
  n = n % 25;
  const dimes = Math.trunc(n / 10);
  n = n % 10;
  const nickels = Math.trunc(n / 5);
  const cents = n % 5;
  return `${quarters} 25 cent pieces, ${dimes} ten cent pieces, ${nickels} five cent pieces and ${cents} one cent pieces`;
}
```

## 10

**Learning:** basic conditional, accessing property of object, boolean evaluation

**Question:** Write a function that accepts a user object that either represents a user that is logged in or not. If the user is logged in then the object looks like this:

```
{
  id: 3224,
  logged_in: true,
  firstname: 'Samwise',
  lastname: 'Gamgee'
}
```

And if the user is not logged in the object looks like this:

```
{
  id: 3224,
  logged_in: false
}
```

If the user is logged in, display a greeting by name. `"Hello Samwise Gamgee"`. Otherwise display the gtreeting: `"Welcome, please log in"`.

**Solution:**
```
function greet(user) {
  if(user.logged_in) {
    return `Hello ${user.firstname} ${user.lastname}`;
  } else {
    return `Welcome, please log in`;
  }
}
```

## 11
 **Learning:** Multiple independent conditionals in sequence, boundary values
 
 **Question:** An electric company charges customers a flat rate of $6.00 for administrative costs and a unit charge for the amount of electricity used according to the following schedule:
 
     First 400 kWh @ $0.26
     Next 600 kWh  @ $0.32
     Over 1000kWh  @ $0.37

Write a function that accepts the amount of electricity used by a customer and calculates the total bill.
 
 **Solution:**
 ```
 function electricBill(kwh) {
  let total = 6;
  if(kwh > 1000) {
    total = total + ((kwh - 1000)* 0.37);
    kwh = 1000;
  } 

  if(kwh > 400) {
    total = total + ((kwh - 400) * 0.32);
    kwh = 400;
  } 

  total = total + (kwh * 0.26);
  
  return total;

}
```

## 12
**Learning:** Accessing properties of objects, basic arithmetic, 

**Question:** Write a function that accepts an object containing user information for a credit card company and determines if the user has exceeded her credit limit for the month. The user object contains the following properties:

```
  {
    account_number: 12345,
    name: 'Brie Larson',
    balance_beginning_of_month: 300,
    total_charges_in_month: 700,
    total_credits_in_month: 200,
    credit_limit: 500
  }
```

The new balance at the end of the month is given by *balance_beginning_of_month + total_charges_in_month - total_credits_in_month*. If the credit limit has been exceeded return the string 'Credit limit exceeded', otherwise return 'Credit available'.



**Solution:**

```
function creditLimit(user) {
  const new_balance = user.balance_beginning_of_month + user.total_charges_in_month - user.total_credits_in_month;
  if(new_balance > user.credit_limit) {
    return 'Credit limit exceeded';
  } else {
    return 'Credit available';
  }
}

```

 ## 13
 
 **Learning:** Multiple conditions using and and or ( or nested if statements )
 
 **Question:** A palindrome is a number or text phrase that reads the same backwards and forwards. For example, this 5 digit number is a palindrome: 12321. Write a function that accepts a five digit number as a parameter. If the number is not five digit long return the message: 'Incorrect input'. If it is a five digit number, determine if it is a palindrome or not. If it is a palindrome return 'Yes, it is a palindrome', otherwise return 'No, not a palindrome'.
 
 **Solution:**

```
function palindrome(n) {
  if(n > 99999 || n < 10000) {
    return 'Incorrect input';
  }

  const first_digit = Math.trunc(n / 10000);
  const last_digit = n % 10;
  const first_and_last = first_digit === last_digit;

  n = n % 10000;
  n = Math.trunc(n / 10);

  const second_digit = Math.trunc(n / 100);
  const second_to_last_digit = n % 10;
  const second_digits = second_digit === second_to_last_digit;

  if(first_and_last && second_digits) {
    return 'Yes, it is a palindrome';
  } else {
    return 'No, not a palindrome';
  }


```

## 14

**Learning:** dangling else, value of indentation, block

**Question:** Consider the two snippets of code below labelled a and b. For each snippet try to predict the output if that code is executed. To make this more challenging, the snippets are not indented the way you were taught to properly indent your code. After you predict what you think this will output, try running the snippets in your browser's console and see if it does what you expect. If it does not correspond to your prediction try to determine why. *Hint: try indenting the code properly to see if that makes it easier to interpret*.

```
// a.
let x = 5;
let y = 11;
if(x < 10)
if(y > 10)
console.log('Yes');
else
console.log('No');
console.log('Maybe');

// b.
let x = 5;
let y = 11;
if(x < 10){
if(y > 10)
console.log('Yes');
}
else {
console.log('No');
console.log('Maybe');
}
```
