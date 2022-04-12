# My Solution
```javascript
function gridChallenge(grid) {
  // Write your code here
  const newGrid = [];
  for (let str of grid) {
    let strArr = [];
    for (let char of str) {
      strArr.push(char);
    }
    strArr.sort();
    newGrid.push(strArr.join(''));
  }

  for (let i = 0; i < grid.length - 1; i++) {
    for (let j = 0; j < grid.length; j++) {
      if (newGrid[i][j] > newGrid[i + 1][j]) {
        return 'NO';
      }
    }
  }
  return 'YES';
}
```