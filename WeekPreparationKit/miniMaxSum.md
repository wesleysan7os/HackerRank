# My Solution
```javascript
'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the 'miniMaxSum' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function miniMaxSum(arr) {
  let max = -Infinity;
  let min = Infinity;
  let maxIndex = 0;
  let minIndex = 0;
  
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] > max) {
      max = arr[i];
      maxIndex = i;
    }
    
    if (arr[i] < min) {
      min = arr[i];
      minIndex = i;
    }
  }
  
  const minArr = arr.filter((number, index) => arr.indexOf(number, index) !== maxIndex);
  const maxArr = arr.filter((number, index) => arr.indexOf(number, index) !== minIndex);
  
  const maxSum = BigInt(maxArr.reduce((previous, current) => {
    return previous + current;
  }, 0))
  
  const minSum = BigInt(minArr.reduce((previous, current) => {
    return previous + current;
  }, 0))
  
  console.log(`${minSum} ${maxSum}`);
}

function main() {

    const arr = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    miniMaxSum(arr);
}
```