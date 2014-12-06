Bitwise operators are very powerful, even in Javascript.

Here are some cool things you can do with them:

###XOR SWAP:

You can use the XOR (^) operator in Javascript to swap two numbers without using a temporary variable.

```
var five = 5;
var three = 3;

five ^= three;
three ^= five;
five ^= three;

five === 3; // true
three === 5; //true
```

###Shiftiness:

Left shifting (<<) a number by a value returns that number times two to the power of that value.

x << y returns x * 2 ^ y;
```
9 << 2 === 36; //true
```

###That's Odd:
A quick way to determine if a number is odd is to use the & operator to compare it with 1. This will return whether the bit at b0 has a value of 0 or 1. All odd numbers have a value of 1 at b0.

```
!!(5 & 1); //Evaluates to true
!!(2 & 1); //Evaluates to false
```

###Power of Two:

The following function, using bitwise operators, determines if a number is a power of 2.
```
function isPowerOfTwo(n){
  return (n& (n-1)) === 0;
}
```
For visual clarity, look at what the number 8 and the number 7 look like in binary.

```
7..toString(2); // 111
8..toString(2); //1000
```

As you can see here, 8 has no bits in common with 7, and would return true when passed to the function.

These are just some basic things you can do with bitwise operators. There is a bitwise nQueens solution, hashing functions use bitwise operators, and a lot of cryptography uses bitwise operators as well.