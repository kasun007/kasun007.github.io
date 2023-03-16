---
title: "Alternatives to Switch statment"
date: 2021-11-07T15:31:03+13:00
draft: false

menu:
  sidebar:
    name: JavaScript Fundamental
    identifier: switch
    parent: java-script
    weight: 10

---

### What is the switch statement?

It is very much similar to If-Else Statment. It takes one parameter and returns a result according to the parameters it receives.

  
```JavaScript
var type = 'coke';
var drink;
switch(type) {
case 'coke':
  drink = 'Coke';
  break;
case 'pepsi':
  drink = 'Pepsi';
  break;
default:
  drink = 'Unknown drink!';
}
console.log(drink); // 'Coke'

```
 But if you look into the syntax the switch statement is written you can see its repeating nature. Imagine a switch statement with a lot of conditions. It makes maintaining the code more difficult. So what is the alternative to it.


 ### Object Literal lookups


```JavaScript
 function getDrink (type) {
  var drinks = {
    'coke': 'Coke',
    'pepsi': 'Pepsi',
    'lemonade': 'Lemonade',
    'default': 'Default item'
  };
  return 'The drink I chose was ' + (drinks[type] || drinks['default']);
}

var drink = getDrink('coke');
// The drink I chose was Coke
console.log(drink);

```
We’ve saved a few lines of code from the switch, and to me the data is a lot cleaner in presentation. We can even simplify it further, without a default case:

```JavaScript

function getDrink (type) {
  return 'The drink I chose was ' + {
    'coke': 'Coke',
    'pepsi': 'Pepsi',
    'lemonade': 'Lemonade'
  }[type];
}


```


We might, however, need more complex code than a String, which could hang inside a function. For sake of brevity and easy to understand examples, I’ll just return the above strings from the newly created function:


```JavaScript

var type = 'coke';

var drinks = {
  'coke': function () {
    return 'Coke';
  },
  'pepsi': function () {
    return 'Pepsi';
  },
  'lemonade': function () {
    return 'Lemonade';
  }
};



```
Ternary operator is also another alterative to switch statements

```JavaScript

const distinguish = type =>
  type === 'admin'
    ? 'This is admin'
    : type === 'user'
    ? 'This is user'
    : type === 'manager'
    ? 'This is manager'
    : 'Uknown guy, denied';

['admin', 'manager', 'nonsense'].map(value => console.log(distinguish(value)));



```



