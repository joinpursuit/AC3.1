Q1.
```js
function numberOfSpaces(string) {
 var count = 0;
 for (var i = 0; i < string.length; ++i) {
     if (string[i] == ' ') {
         ++count;
     }
 }
 return count;
}
```

Q2. 
```
0
```

Q3. 

```
E
U
L
T
A
```

Q4.
```javascript
var removeZero = function (str) {
  res = "";
  for (var i = 0; i < str.length; i++) {
    if (str[i] != "0") {
      res += str[i];
    }
  }
  return res;
}
```

Q5.
```javascript
var min = function (num1, num2) {
  if (num1 <= num2) {
    return num1;
  } else {
    return num2;
  }
}
```

Q6.
```javascript
function sumEveryThird(arr){
  var sum = 0;
  for(var i = 0; i < arr.length; i++) {
    if((i + 1) % 3 === 0) sum += arr[i];
  }
  return sum;
}
```

Q7.
```javascript
var findLongestWord = function (arr) {
  var longestLength = 0;
  for (var i = 0; i < arr.length; i++) {
    if (arr[i].length > longestLength) {
      longestLength = arr[i].length;
    }
  }
  return longestLength;
}
```

Q8.
```javascript
function tipCalculator(total, tip, peeps) {
  return total * (tip / 100) / peeps;
}
```

Q9.
```javascript
var repeat = function (str, count) {
  var result = str;
  for (var i = 0; i < count - 1; i++) {
    result += str;
  }
  return result; 
} 
```

Q10.
```javascript
var i = 1;
var gap = 0;
while (i < 100){
  console.log(i);
  gap += 1;
  i += gap;
}
```

Q11.
```javascript
function anagramChecker(str1, str2) {
  var sorted1 = str1.split('').sort().join('');
  var sorted2 = str2.split('').sort().join('');
  return sorted1 === sorted2;
}
```

Q12. 
```javascript
function maxSliceSum(arr) {
  var max = -Infinity;
  for(var i = 0; i <= arr.length -1; i++){
    for(var j = 1; j <= arr.length; j++){
      if(arrAdd(arr.slice(i, j)) > max) max = arrAdd(arr.slice(i,j))
    }
  }
  return max;
}

function arrAdd(arr) {
  var sum = 0;
  for(var i = 0; i < arr.length; i++){
    sum += arr[i];
  }
  return sum;
}
```

