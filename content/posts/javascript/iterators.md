---
title: "Iterators and Generators"
date: 2021-11-07T15:31:03+13:00
 

menu:
  sidebar:
    name: Iterators and Generators
    identifier: iterators_and_generators
    parent: java-script
    weight: 10

---

---


 

 ## What do we mean by Iterators  


When ever you have a some datasource .Iterators can consume values in that datasource one at a time.


 # What is Iterables and Iterators?

ES6 introduced new mechanisam for traversing data called iteration.Two cocepts are central to iteration

1.An iterable is a data structure that wants to make its elements accessible to the public. It does so by implementing a method whose key is Symbol.iterator. That method is a factory for iterators.

2.An iterator is a pointer for traversing the elements of a data structure (think cursors in databases)




**The following values are iterable:**

1. Strings 
2. Maps 
3. Sets 
4. DOM data structures (work in progress)
 
Plain objects are not itertable

**There are two parties invloled in when it comes to iterability**

1. Data Consumers - Language construts that consume data .eg for of loop over values and spread operator (...) inserts data
2. Data Sources -Data Consumers can extract data from differnt sources .For example, you may want to iterate over the elements of an Array, the key-value entries in a Map or the characters of a string.

![image alt text](/images/it.jpeg)

**How Iterators Works?**
```JavaScript
var obj = {
a : 1,
b : 2,
c : 3,

[Symbol.iterator]: function(){
   var keys = Object.keys(this);
   var index = 0;
   return {
       next:() => (index <keys.length) ?
    
             { done:false,value: this[keys[index++]] } : 
             { done:true, value :undefined    }
    
    };
   
   }
};
 
 console.log([...obj]);

```

Here used the name Symbol.itertor.Symbols provide names unique to and cannot clash with oter property name.Symbol.itertor will return an **object called** and itertaor. This iterator includes function called next which will return done and value.

The following ES6 language constructs make use of the Iterable:

1. Destructuring via an Array pattern
2. for-of loop
3. Array.from()
4. Spread operator (...)
5. Constructors of Maps and Sets
6. Promise.all(), Promise.race()
7. yield*

As we can see iterator is fairly imparative approach to adapoting the iterator protocol for an object (An imperative approach, a developer writes code that specifies the steps that the computer must take to accomplish the goal.)
  

In contarst to Itetor Generator follows decalarative approach.Note the new syntax: function* is a new “keyword” for generator functions (there are also generator methods). yield is an operator with which a generator can pause itself. Additionally, generators can also receive input and send output via yield.
sample code using generator:

```JavaScript
 function *main(){
 
  yield 1;
  yield 2;
  yield 3;
  yield 4;
  return 5;
 }
 
 var it = main();
 
 console.log(it.next());
 console.log(it.next());
 console.log(it.next());
 console.log(it.next());
 console.log(...main());
 ```

 