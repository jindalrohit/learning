#### Closure
___
At the end of this file you will be able to know about the followings:
- What is Closure?
- Why do we need Closure?
___

##### What is Closure
A closure gives you access to an outer function’s scope from an inner function. In JavaScript, 
closures are created every time a function is created, at function creation time.
###### Conside following example :
```
function makeFunc() {
  var x = 'Learning Closure';
  function displayX() {
    console.log(x);
  }
  return displayX;
}

var myFunc = makeFunc();
myFunc();
```
Explanation: A closure is the combination of a function and the lexical environment within which that function was declared. In this case, myFunc is a reference to the instance of the function displayName created when makeFunc is run. The instance of displayName maintains a reference to its lexical environment, within which the variable name exists. For this reason, when myFunc is invoked, the variable x remains available for use, and "Learning Closure" is passed to console.
___
##### Why do we need Closure
- Closures are useful because they let you associate data (the lexical environment) with a function that operates on that data like OOPs
- Closures are useful where you might normally use an object with only a single method. Much of the code written in front-end JavaScript is event-based. You define some behavior, and then attach it to an event that is triggered by the user (such as a click or a keypress). The code is attached as a callback (a single function that is executed in response to the event).
- JavaScript does not provide a native way of declare methods as private but it is possible using closures, like this:
```
// Here privateCounter and privateChangeBy both are private members
var makeCounter = function() {
  var privateCounter = 0;
  function privateChangeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      privateChangeBy(1);
    },

    decrement: function() {
      privateChangeBy(-1);
    },

    value: function() {
      return privateCounter;
    }
  }
};
```
###### NOTE: Using closures in this way provides benefits that are normally associated with object-oriented programming. In particular, data hiding and encapsulation.
___

#### Performance considerations

It is unwise to unnecessarily create functions within other functions if closures are not needed for a particular task, as it will negatively affect script performance both in terms of processing speed and memory consumption.

For instance, when creating a new object/class, methods should normally be associated to the object's prototype rather than defined into the object constructor. The reason is that whenever the constructor is called, the methods would get reassigned (that is, for every object creation).

##### Source : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures
