####How can you tell an extrovert from an introvert at NSA? 
####Va gur ryringbef, gur rkgebireg ybbxf ng gur BGURE thl'f fubrf.

The answer to the super lame joke above is encoded using the ROT13 Cipher. ROT13 is an example of a Caesar Cipher, or a cipher in which characters are shifted by a certain number. 

In the case of ROT13, charcters are "rotated by 13".

For example, 'a' when passed to a ROT13 cipher would be encoded as 'n', 'b' would be 'o'. 

ROT13 is a reciprocal cipher, meaning that you can encode and decode using the same exact cipher. For this reason, it is often cited as a very low security cipher, mostly used for lame jokes like the one above.

The following is a function to encode and decode using ROT13, using RegExp in JavaScript:

```
function rot13(str) {
  return str.replace(/[a-zA-Z]/g,function(c){
    return String.fromCharCode((c<="Z"?90:122)>=(c=c.charCodeAt(0)+13)?c:c-26);
  });
}
```