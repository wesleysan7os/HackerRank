# My Solution
```javascript
function processData(input) {
  //Enter your code here
  const lines = input.split("\n");
  const queriesNumber = +lines[0];
  let primaryStack = [];
  let auxiliarStack = [];
  
  this.enqueue = function(elem) {
    primaryStack.push(elem);
  }
  
  this.dequeue = function() {
    while (primaryStack.length > 0) {
      auxiliarStack.push(primaryStack.pop());
    }
    
    const deletedElem = auxiliarStack.pop();
    
    while (auxiliarStack.length > 0) {
      primaryStack.push(auxiliarStack.pop());
    }
    
    return deletedElem;
  }
  
  this.print = function() {
    while (primaryStack.length > 0) {
      auxiliarStack.push(primaryStack.pop());
    }
    
    const firstElem = auxiliarStack.pop();
    
    console.log(firstElem);
    
    auxiliarStack.push(firstElem);
    
    while (auxiliarStack.length > 0) {
      primaryStack.push(auxiliarStack.pop());
    }
  }
  
  for (let i = 1; i <= queriesNumber; i++) {
    let args = lines[i].split(" ");
    
    switch(+args[0]) {
      case 1:
        this.enqueue(+args[1]);
        break;
      case 2:
        this.dequeue();
        break;
      case 3:
        this.print();
        break;
    }
  }
} 

process.stdin.resume();
process.stdin.setEncoding("ascii");
_input = "";
process.stdin.on("data", function (input) {
    _input += input;
});

process.stdin.on("end", function () {
   processData(_input);
});
```