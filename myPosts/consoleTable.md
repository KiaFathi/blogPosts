Since today is Thanksgiving, I spent a lot of time sitting at the table. Probably too much time. For that reason, I am going to introduce you to a cool debugger tool:

###console.table()

<strong>console.table</strong> has two paramters, data and columns. Data can be either an array or an object to display. Columns is an array of the names of the columns to include in the displayed table.

Let's explore the primary use case:

###Displaying Objects:
```
var testObj = {};
testObj.array1 = [1,2,3,4,5];
testObj.array2 = testObj.array1.map(function(val){
  return val * 2;
});
testObj.array3 = testObj.array2.map(function(val){
  return val * 3;
});

// Display the entire object in a table
console.table(testObj);

// Display the arrays and their lengths
console.table(testObj, 'length');

// Display the arrays and their first three indices
console.table(testObj, [0,1,2]);
```

Pretty cool trick huh?

Happy Thanksgiving!