Composition is a key tenet of functional programming. Composition allows programmers to merge simple functions to build combined functions with more complex behavior. On higher level, function composition is very declarative, enabling programmers to write short, readable, and precise code.

In JavaScript, functions are treated as first class citizens. This means we can pass them as arguments to functions, or create them as the result of other functions. This makes basic composition pretty easy to accomplish.

The following is an example compose function:

###Compose:
```
//This compose takes two functions as arguments
var compose = function(g, f){
  //A new function that applies f to its argument and then g to the result
  return function(x){
    return g(f(x));
  };
};
```

Let's see how we could use this function:

```
function exclaim(str){
  return str.toUpperCase() + '!';
}

function greet(str){
  return 'hello ' + str;
}

function properNoun(str){
  return str.substring(0,1).toUpperCase() + str.substring(1);
}

var greetExcitedly = compose(exclaim, greet);
greetExcitedly('franky'); //'HELLO FRANKY!'

var greetProperly = compose(properNoun, compose(greet, properNoun));
greetProperly('johnny'); //'Hello Johnny'
```

These are very basic examples of function composition. For more functional programming, I encourage you to experiment with the <a href='https://www.npmjs.org/package/ramda'>Ramda</a> library.
