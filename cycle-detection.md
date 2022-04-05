# My Solution
```javascript
function hasCycle(head) {
  if (head === null) return 0;
  let node = head;
  const arr = [];
  let hasCycle;
  let i = 0;

  while (node) {
    node.data = i++;
    arr.push(node);

    if (node.next) {
      hasCycle = arr.find((e) => node.next.data === e.data);
    }
    if (hasCycle) return 1;
    node = node.next;
  }

  return 0;
}
```