# 2014-10-20 JavaScript - private variables

tags: JavaScript, prototypical inheritance, revealing module pattern, revealing prototype pattern, scope

Here's an example of the Module Pattern, read the comments to understand how it works:


```javascript
// module is the value of what is returned from the Immediately Invoked Function Expression (IIFE).
var module = (function() {
  // 'Private' variable, defined within the scope of the executed IIFE.
  var _version = "1.0.0.0";
  
  // Returns a new object, with the property 'getVersion' that is pointing to an anonymous function.
  return {
    getVersion: function() {
      // When the anonymous function was defined, it was executing in the context of the IIFE
      // and so has access to _version.
      return _version;
    }
  };
})();
 
module.getVersion(); // returns "1.0.0.0"
 
// If we try set _version, what we're doing is setting the property on the object,
// and not the variable defined in the IIFE - we're not executing in that context,
// so we don't have access to it.
module._version = "2.0.0.0";
 
module.getVersion(); // still returns "1.0.0.0"
```
So, this solves the problem of having a private variable that we don't want to expose. Now lets see an example of a "class" in JavaScript (note: future versions will have class constructs built into the language, I'm just showing how people do it today):


```javascript
// By convention, if a function is a constructor function, use UpperCamelCase
function Person(firstName, lastName) {
  // constructor when used with the 'new' keyword
  this.firstName = firstName;
  this.lastName = lastName;
}
Person.prototype.getName = function() {
  return this.firstName + ' ' + this.lastName;
};
 
var p = new Person('joe', 'bloggs');
p.getName(); // returns 'joe bloggs'
p.firstName = 'fred';
p.getName(); // returns 'fred bloggs'
```

This works, but the property `firstName`, is being used by the `getName` function, and is public. This means we can just override the property.

How would we create a private property in this case? Well, what if we try the same concept of scoping things to the execution of the constructor function, first attempt:


```javascript
function Person(firstName, lastName) {
  // these are private to the constructor function
  var _firstName = firstName;
  var _lastName = lastName;
}
Person.prototype.getName = function() {
  // Won't work, since 'this' is scoped to the object that getName is executing on
  // and not to the scope of the constructor function.
  return this._firstName + ' ' + this._lastName;
};
 
var p = new Person('joe', 'bloggs');
p.getName(); // returns 'undefined undefined'
```

The function now doesn't have access to the variables, so what if we move this into the scope of the constructor... second attempt:


```javascript
function Person(firstName, lastName) {
  var _firstName = firstName;
  var _lastName = lastName;
  Person.prototype.getName = function() {
    return _firstName + ' ' + _lastName;
  };
}
 
var p = new Person('joe', 'bloggs');
p.getName(); // returns 'joe bloggs'
var q = new Person('fred', 'flintstone');
q.getName(); // returns 'fred flintstone'
p.getName(); // also returns 'fred flintstone', since all objects are referring to the same prototype

```
At first glance, this seems to work, but we actually override the prototype each time the constructor runs... bad! Instead we should rather be defining the function on the actual instance being created:


```javascript
function Person(firstName, lastName) {
  var _firstName = firstName;
  var _lastName = lastName;
  this.getName = function() {
    return _firstName + ' ' + _lastName;
  };
}
 
var p = new Person('joe', 'bloggs');
p.getName(); // returns 'joe bloggs'
var q = new Person('fred', 'flintstone');
q.getName(); // returns 'fred flintstone'
p.getName(); // returns 'joe bloggs'
```

This then solves the problem of keeping the variables private to each instance. One downside to this then is that each instance is referring to its own function, and not sharing one common function on the prototype, taking up more memory, but giving the advantage of private scope.

For some extra reading on scopes in JavaScript, read ["Private Members in JavaScript"](http://crockford.com/javascript/private.html) by [Douglas Crockford](https://www.crockford.com/about.html)

Another similar way of doing this is with the Revealing Prototype Pattern, explained in [Dan Wahlin's](https://blog.codewithdan.com/) post ["Revealing Prototype Pattern - Techniques, Strategies and Patterns for Structuring JavaScript Code"](https://weblogs.asp.net/dwahlin/techniques-strategies-and-patterns-for-structuring-javascript-code-revealing-prototype-pattern)

