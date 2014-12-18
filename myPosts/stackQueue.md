A stack is a basic data structure in computer science that follows one rule: <strong>LIFO</strong>, which stands for Last In First Out. You can view a stack as a deck of cards that can only have things added or removed from the top.

A queue is another fundamental data structure science that follows the rule: <strong>FIFO</strong>, which stands for First In First Out. You can imagine a queue as a line for tickets at the movie theater. The people who get in line first, get tickets first and then leave the line.

The following code snippet is how you would implement a Stack class in JavaScript and how you can then use that Stack Class to build a Queue class.

```
var Stack = function(){
  this.storage = [];
};

Stack.prototype.push = function(value){
  this.storage.push(value);
};

Stack.prototype.pop = function(value){
  return this.storage.pop();
};

Stack.prototype.size = function(){
  return this.storage.length;
};

var Queue = function(){
  //create an outbox for things to be removed from
  this.outbox = new Stack();
  //create an inbox for things to be added into
  this.inbox = new Stack();
};

Queue.prototype.enqueue = function(value){
  this.inbox.push(value);
};

Queue.prototype.dequeue = function(){
  //if the outbox is empty, want to refill it with inbox items
  if(!this.outbox.size()){
    while(this.inbox.size()){
      this.outbox.push(this.inbox.pop());
    }
  }
  return this.outbox.pop();
};
```