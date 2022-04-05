# My Solution
```javascript
function processData(input) {
  //Enter your code here
  const lines = input.split("\n");
  const queriesNumber = +lines[0];
  let pushStack = [];
  let popStack = [];
  
  this.enqueue = function(elem) {
    pushStack.push(elem);
  }
  
  this.dequeue = function() {
    if (popStack.length > 0) {
      return popStack.pop();
    }

    while (pushStack.length > 0) {
      popStack.push(pushStack.pop());
    }
    
    return popStack.pop();
  }
  
  this.print = function() {
    if (popStack.length > 0) {
      const firstElem = popStack.pop();
      console.log(firstElem);
      popStack.push(firstElem);
      return;
    }

    while (pushStack.length > 0) {
      popStack.push(pushStack.pop());
    }
    
    const firstElem = popStack.pop();
    console.log(firstElem);
    popStack.push(firstElem);
  }
  
  for (let i = 1; i <= queriesNumber; i++) {
    let [cmd, arg] = lines[i].split(" ");
    
    switch(+cmd) {
      case 1:
        this.enqueue(+arg);
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