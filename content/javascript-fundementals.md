---
title: "JavaScript Fundamentals"
date: 2021-11-08T15:31:03+13:00
draft: true
---

 


### statment  

statement is a collection of work numbers and operators that perform particular task

a=b *2 
 what is Variable
To store values we use things called variables. The word 'variable' means 'can change' and is used because variables can store many different types of values and can change their value many times. They are pretty much like mailboxes. We put something in a variable, like our sentence, and then give the variable an address that we can use to look up the sentence later. In real life mailboxes have to have PO Box numbers but in JavaScript you usually just use lowercase letters or numbers without any spaces.
javascript variable types


Variable types available in javascript

- String.
- Number.
- Boolean.
- Null.
- Undefined.
- Symbol.
- BigInt.
- Object

In javascript variables do not have types values do



## Function

function is  collection of statements  like paragraph in a novel . function  consist of collection of things that we want to perform  . It can be reused in multiple places in the Application. Actually technically the computer science programming term for function is Procedure.

   
Function in includes the  word function  to note it   and a  name .  Function can have n number of parameters .Some function return a value some does not.It is totally up to developer to decide it


## Three Pillars of  JS

types/Coercion
Scope/Closure
this/Prototypes


   typeof 42          number
   typeof ("Kyle");  string
   typeof (true); boolean
   typeof {age:39}.  Object
   typeof  null    object
  typeof ([1,2,3]); object

So you may wondering  why null is an object.Reason  is   it is a bug that we cant do anything about  it and array also consider as  object  because of  array is a subtype of object


scope 
Simply put Scope is where to look things. This definition  leads to couple of question  like what we are looking for.So simply  we are looking for identifiers
  
x=54;  -
console.log(y);

Every Variable  play one of the following role in the program


1.Variable declaration and assign a value  to it 
2.Retrieve the value form variable

When Java script engine  process a code  first it asks   what position is it in and What scope does it belong to. The real world example to explain  this process  is putting marbles into color-coded buckets.Lets take a look at the following code piece.

```JavaScript 
var car ="BMW"; <-- Red Bucket (Global Scope)

function myFunction() {  <--Red Bucket (Global Scope)
  let carName = "Volvo"; <-- Blue Bucket(Function Scope)
  console.log(carName);
  
}
```

Two Actors  are involved in processing a javascript program.One  is javascript compiler that is processing the javascript program and Scope manager.
1st compiler comes   line one and create a marble and ask scope manger where it should put this marble . In this case  variable car is in the global scope.So then  Scope Manager creates a bucket and puts that marble into Red bucket (Here I m going to create three buckets with 3 different colours(Red ,Green blue)). Now we have a red bucket that represents Global scope.  Then the  compiler goes to the second line and find the formal declaration, Which  in this case  is a marble called  "my Function" and ask scope manager  it has  ever heard of this marble.Scope manager replied back with NO and    puts that marble   into Red bucket.

Then it goes inside to the function scope(myFunction).Function scope creates a new scope which means it  creates a new  blue bucket.Then compiler  comes  line 3 and ask scope manager where it should put  this marble . So the scope manager puts the marble into Blue bucket



### Lexical Scope

Lexical Scope is definition area of a  expression.It is decided in the compile time and it is totally decided by author
```JavaScript 
   var teacher = "Kyle"

   function otherclass() {

	var teacher = "Suzane";

	      function ask(question) {
                    console.log(teacher,question);

	     }

	  ask("Why");
   }
```

on the above code each colour represents the Lexical scope  .

### "this" Key Word   

A function's this references the execution context for that call , determined by how the function was called.Not like in other programming languages  this key word in JavaScript behave differently.All the other languages this keyword refer to the current states of object within class while java script refers to this keyword by function is invoked.

```JavaScript 
function ask(question) {
    console.log(this.teacher, question);
  }
  
  function otherClass() {
    
  var teacher = "Suzy";
   ask("Why");
  }
  
  
  otherClass();
```


As you can see in the above  lines of code when the  function otherclass  is called ,it calls the function ask .Then  function ask prints the value suzy.The reason for such a behaviour is function ask is called with the context of  other class.so the  this  keyword in ask function refers to the context in other class and able to access the variables declare in other class