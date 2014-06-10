__This is a WIP and eventually evole in to resource with a collection of implementations of data structures.__


Let create a `Node` class that will be useful in the upcoming D.S

```js
class Node {
  constructor(value){
    this.value = value;
    this.next  = null;
    this.prev  = null;
  }
}
```

#Stack

[Stacks](http://en.wikipedia.org/wiki/Stack_(data_structure)) is javascript can be as simple as:

```js
var stack = [];
stack.push(4);       // stack -> [4]
stack.push(2);       // stack -> [4,2]
console.log ( stack.pop(); ); // 2
```

But let us elaborate a bit more and implements methods like: `peek`, `isEmpty`, `top`, `hasNext` without arrays ;)

```js
class Stack {
  constructor() {
    this.first=null;
    this.last=null;
  }
  
  push(elem){
    var node = new Node(elem);
    this.first = !this.first ? node : this.first;
    if(this.last) {
      this.last.next = node;
    } 
    node.prev = this.last;
    this.last = node;
  }
  
  pop(){
    if( !this.isEmpty() ){
      var popped = this.last;
      this.last = popped.prev;
      popped.prev=null;
      if(!this.last){ 
        this.first=null;
      } else {
        this.last.next=null;
      }
      return popped.value;
    }
  }
  
  peek() {
    return this.last.value;
  }
  
  hasNext() {
    return !!this.last;
  }
  
  isEmpty(){
    return !this.last;
  }
}
```

```js
var s = new Stack();

s.push(42);

console.log( s.peek() ); //42
console.log( s.hasNext() ); // True
console.log( s.isEmpty() ); // False

s.push(420); 

console.log( s.hasNext() ); // True

while( s.hasNext() ) s.pop();

console.log( s.hasNex() ) // False
```
