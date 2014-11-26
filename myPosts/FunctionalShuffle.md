###Functional Shuffle

Recently, I have been exploring functional programming and writing my own custom functional methods. In writing 'functional' code, I have been stressing the following guidelines:

1. Code is declarative
1. Code does not produce side effects
1. Data is immutable

For example, let's explore how we could write a shuffle method for Arrays.

###Shuffle 1:
```
Array.prototype.shuffle = function(){
  var shuffled = [],
      randomIndex;
  while(this.length){
    randomIndex = Math.floor(Math.random() * this.length);
    shuffled.push(this.splice(randomIndex,1)[0]);
  }
  return shuffled;
};
```

Even though the above method is declarative, it produces a shuffled array, it does not adhere to the functional paradigm. 

This shuffle method has side effects, it removes all the contents of the original array. For the same reason, the input array is not being treated as an immutable object with this shuffle method.

Additionally, the above solution has a time complexity of O(n^2) because each splice operation is linear with respect to the rest of the array after the splice index, and we are splicing n times. If you are shuffling large arrays, this can become extremely cumbersome.

The following is a better solution:

###Shuffle 2:
```
Array.prototype.shuffle = function(){
  var length = this.length,
      shuffled = new Array(length),
      randomIndex;
  for(var i = 0; i < length; i++){
    randomIndex = Math.floor(Math.random()*(i));
    if(randomIndex !== i){
      shuffled[i] = shuffled[randomIndex];
    }
    shuffled[randomIndex] = this[i];
  }
  return shuffled;
}
```

This shuffle method is more functional for the following reasons:
1. It is declarative.
1. The original array is not mutated in any way.
1. There are no side-effects produced.

For time complexity, this solution is linear, O(n), with respect to the length of the array, as we are only iterating over the array once.

Overall, both of these shuffle methods get the same job done. There are some distinct advantages to the functional approach though. 
1. By not mutating inputs, their values are retained for re-use.
1. By reducing side-effects, the interfaces of functions are cleaner, and we reduce the likelihood of unexpected behavior.
1. The declarative style of functional programming can make code more readable.