An anagram is a word formed by rearranging the letters of another. An example is the word cinema made from the word iceman.

The following is how you can programmatically create all anagrams of a given word using a depth-first recursion.

###Example:

```
function allAnagrams(word){
  var anagrams = [];
  function subroutine(remaining, word){
    //base case
    if(remaining.length === 0){
      anagrams.push(word);
    } else {
      for(var i = 0; i < remaining.length; i++){
        var newWord = word + remaining[i];
        var newRemainder = remaining.substring(0,i) + remaining.substring(i + 1);
        subroutine(newRemainder, newWord);
      }
    }
  }
  subroutine(word, '');
  return anagrams;
}

```

This can be improved by using a dictionary to check which words are actually valid words.