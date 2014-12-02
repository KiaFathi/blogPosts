Merge sort is a tried and true sorting algorithm with a great time complexity, O(nlog(n)) at worst case.

Merge sort is a divide and conquer algorithm. It begins by splitting its input list recursively until it reaches inherently sorted list, which in my implementation are arrays of length 1. Merge sort then 'merges' these sorted lists of length 1 into sorted lists of length 2 and vice versa until the list itself is produced in its entirety, fully sorted.

The following is a basic implementation of merge sort:
```
var mergeSort = function(array){
  var arrayA = array.slice(0, Math.floor(array.length/2));
  var arrayB = array.slice(Math.floor(array.length/2));
  if(arrayA.length > 1){arrayA = mergeSort(arrayA);}
  if(arrayB.length > 1){arrayB = mergeSort(arrayB);}
  var newArray = [];
  var a = 0;
  var b = 0;
  while(newArray.length < (arrayA.length + arrayB.length)){
    if(arrayA[a] < arrayB[b] || (arrayB[b] === undefined && arrayA[a] !== undefined)){
      newArray.push(arrayA[a]);
      a++;
    } 
    else if(arrayB[b] <= arrayA[a] || (arrayA[a] === undefined && arrayB[b] !== undefined)){
      newArray.push(arrayB[b]);
      b++;
    }
  }
  return newArray;
};
```

My implementation treats arrays of length 1 as sorted, but a better implementation may identify already sorted sublists and stop further recursive calls at that point.