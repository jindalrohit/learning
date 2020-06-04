### Javascipt Inheritance
___

```
function Person(name) {
  this.name = name;
};

Person.prototype.greeting = function() {
  console.log('Hi! I\'m ' + this.name + '.');
};

function Teacher(name, subject) {
  Person.call(this, name);
  this.subject = subject;
}

```
Person.call is required to allows you to call a function defined somewhere else, but in the current context. 
We want the Teacher() constructor to take the same parameters as the Person() constructor it is inheriting from, 
so we specify them all as parameters in the call() invocation.

###### Now run this code

```
var t = new Teacher('India', 'Computer');
t.greeting();

```
###### Output:

```
"error"
"TypeError: t.greeting is not a function ...
```
Beacuse it does not contain the methods of the Person constructor's prototype property. To fix this problem we need to create a new object and make it the value of Teacher.prototype. The new object has Person.prototype as its prototype and will therefore inherit, if and when needed, all the methods available on Person.prototype.

```
Teacher.prototype = Object.create(Person.prototype);
```
Now run again and output would be :
```
"Hi! I'm India."
```

Still there is one more problem. Teacher.prototype's constructor property is now equal to Person(), 
because we just set Teacher.prototype to reference an object that inherits its properties from Person.prototype
To fix this do this:
```
Object.defineProperty(Teacher.prototype, 'constructor', { 
    value: Teacher, 
    enumerable: false, // so that it does not appear in 'for in' loop
    writable: true });
----------OR---------------
Teacher.prototype.constructor = Teacher;
```
Now run this :

```
console.log(Teacher.prototype.constructor);
//Output would be Teacher constructor function
```

###### Here is the complete code :
```
function Person(name) {
  this.name = name;
};

Person.prototype.greeting = function() {
  console.log('Hi! I\'m ' + this.name + '.');
};

function Teacher(name, subject) {
  Person.call(this, name);
  this.subject = subject;
}

Teacher.prototype = Object.create(Person.prototype);
Teacher.prototype.constructor = Teacher;

console.log(Teacher.prototype.constructor);

var t = new Teacher('India', 'Computer');
t.greeting();

```
