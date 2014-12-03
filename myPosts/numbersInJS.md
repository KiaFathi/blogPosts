Javascript is not good at handling large numbers. The Number type can only handle numbers who have absolute values lesss than 2 to the 53rd power.

It is easy to test the veracity of this statement:

```
Math.pow(2,53) === Math.pow(2,53) + 1 // true
```

What can be done in the rare case that our JS code needs to handle numbers outside of this range? 

One answer could be to use a different langauge.

A more involved answer could be treating the numbers as strings. 

The following is an example of an addition function that takes two integers as strings and finds their sums:

```
function sumStrings(a,b) { 
  var arrA = a.split('').reverse();
  var arrB = b.split('').reverse();
  var ans = '';
  var i = 0;
  var carry = 0;
  while(arrA[i] !== undefined || arrB[i] !== undefined){
    var a = parseInt(arrA[i]) || 0;
    var b = parseInt(arrB[i]) || 0;
    var sum = a + b + carry;
    if(sum > 9){
      carry = 1;
      sum -= 10;
    }
    else {
      carry = 0;
    }
    ans = parseInt(sum) + ans;
    i++;
  }
  if(carry){
    ans = '1' + ans;
  }
  var flag = false;
  while(!flag){
    flag = true;
    if(ans[0] === '0'){
      flag = false;
      ans = ans.substring(1);
    }
  }
  return ans;
}
```




