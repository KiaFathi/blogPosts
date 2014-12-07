###Thats ~ right:
The bitwise not operator (~) inverts all the bits of a given number. For example, if we have the binary number 1010, equivalent to the decimal number 10, and we invert all the bits we should get the binary numbr 0101, equivalent to the decimal number 5.

In Javascript, we can use the number method toString to see the binary represenation of a number.
```
var five = 5;
five.toString(2); // 101

var eight = 8;
eight.toString(2); // 1000
```

Intuitively, it would make sense for ~five to equal 010, or 2, and ~eight to equal 0111, or 7. Let's see what happens when we do this in Javascript:

```
var five = 5;
five.toString(2); // 101

var eight = 8;
eight.toString(2); // 1000

~five; // -6
~eight; // -9

```

Why do we see this unexpected behavior in Javascript?

###Complements of Two's Complement

What is Two's Complement? It is a system to represent positive and negative numbers using bits. 

Two's Complement works by using the most significant bit as a signal for whether a number is positive or negative. A 0 in the most siginificant place represents a positive number, and a 1 represents a negative number.

The following are all the 3 bit numbers in Two's Complement:
```
011; // 3
010; // 2
001; // 1
000; // 0
111; // -1
110; // -2
101; // -3
```

The way the system works is different dependent on the sign of the number.

All positive numbers have an extra 0 as their most significant bit, but work like regular binary.

####7 is equal to 111
  - 1 in b0 is equal to 1
  - 1 in b1 is equal to 2
  - 1 in b2 is qual  to 4
  - 4 + 2 + 1 = 7

All negative numbers are preceded by a 1, and the value of a negative number is found by subtracting all the bits after the most significant bit from the most significant bit.

####-3 is equal to 101.
 - 1 in b2 represents 4.
 - 1 in b0 represents 1.
 - 4 - 1 = 3
 - Since we have a negative number, this results
in -3

####-13 is equal to 10011.
  - 1 in b4 is equal to 16
  - 1 in b1 is equal to 2, plus 1 in b0 is equal to 3
  - 16 - 3 = 13
  - Since we have a negative number, this results in -16