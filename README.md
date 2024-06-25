# Typescript-Programs

## Algorithims

### 1. Binary Search Algorith(Iterative method)

```typescript
     function binarySearch(arr: number[], target: number): number {
       let left = 0;
       let right = arr.length - 1;
       while (left <= right) {
         const mid = Math.floor((left + right) / 2);
         if (arr[mid] === target) return mid;
         else if (target > arr[mid]) left = mid + 1;
         else right = mid - 1;
       }
       return -1;
     }

     console.log(BinarySearch([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], 8)); // Outputs: 7
     
```
### 2. Binary Search Algorith(Recursive method)

```typescript
     function binarySearchRecursive(arr: number[], target: number, left: number = 0, right: number = arr.length - 1): number {
       if (left > right) {
         return -1;
       }
       const mid = Math.floor((left + right) / 2);
       if (arr[mid] === target) return mid;
       else if (arr[mid] < target) return binarySearchRecursive(arr, target, mid + 1, right);
       else return binarySearchRecursive(arr, target, left, mid - 1);
     }

     console.log([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], 3); // Outputs: 2

```

### 3. Linear Search

```typescript
function linearSearch(arr: number[], target: number): number {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === target) {
      return i; // Target found, return the index
    }
  }
  return -1; // Target not found
}

const result = linearSearch([10, 3, 5, 17, 9, 11, 13, 15, 1, 19], 5); // Outputs: 2
```

### 4. **Quick Sort**

```typescript
function quickSort(arr: number[]): number[] {
  if (arr.length <= 1) return arr;
  const pivot = arr[Math.floor(arr.length / 2)];
  const left = arr.filter(x => x < pivot);
  const middle = arr.filter(x => x === pivot);
  const right = arr.filter(x => x > pivot);
  return [...quickSort(left), ...middle, ...quickSort(right)];
}

console.log(quickSort([3, 6, 8, 10, 1, 2, 1])); // [1, 1, 2, 3, 6, 8, 10]
```

## Data Structures

### 1. **Stack**
- A stack is a linear data structure that follows the Last-In-First-Out (LIFO) principle, meaning the last element added to the stack is the first one to be removed.
  
```typescript
class Stack<T> {
  private items: T[] = [];

  push(item: T) {
    this.items.push(item);
  }

  pop(): T | undefined {
    return this.items.pop();
  }

  peek(): T | undefined {
    return this.items[this.items.length - 1];
  }

  size(): number {
    return this.items.length;
  }
}

const stack = new Stack<number>();
stack.push(1);
stack.push(2);
console.log(stack.peek()); // 2
console.log(stack.pop()); // 2
console.log(stack.pop()); // 1
```

### 2. **Queue**
- A queue is a linear data structure that follows the First-In-First-Out (FIFO) principle, meaning the first element added to the queue is the first one to be removed.
  
```typescript
class Queue<T> {
  private items: T[] = [];

  enqueue(item: T) {
    this.items.push(item);
  }

  dequeue(): T | undefined {
    return this.items.shift();
  }

  front(): T | undefined {
    return this.items[0];
  }

  size(): number {
    return this.items.length;
  }
}

const queue = new Queue<number>();
queue.enqueue(1);
queue.enqueue(2);
console.log(queue.front()); // 1
console.log(queue.dequeue()); // 1
console.log(queue.dequeue()); // 2
```

### 3. Find the maximum element in an array(Array Operations)?

```typescript
function findMax(arr: number[]): number {
    if (arr.length === 0) throw new Error("Array is empty");
    let max = arr[0];
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}

const arr = [3, 5, 7, 2, 8];
console.log(findMax(arr)); // Output: 8
```

### 4. Singly Linked List(Linked List Implementation)?

```typesccript
class ListNode {
    value: number;
    next: ListNode | null = null;

    constructor(value: number) {
        this.value = value;
    }
}

class LinkedList {
    head: ListNode | null = null;

    // Append a new node with the given value to the end of the list
    append(value: number): void {
        const newNode = new ListNode(value);
        if (this.head === null) {
            this.head = newNode;
        } else {
            let current = this.head;
            while (current.next !== null) {
                current = current.next;
            }
            current.next = newNode;
        }
    }

    // Prepend a new node with the given value to the beginning of the list
    prepend(value: number): void {
        const newNode = new ListNode(value);
        newNode.next = this.head;
        this.head = newNode;
    }

    // Delete the first node that contains the given value
    delete(value: number): void {
        if (this.head === null) return;

        if (this.head.value === value) {
            this.head = this.head.next;
            return;
        }

        let current = this.head;
        while (current.next !== null && current.next.value !== value) {
            current = current.next;
        }

        if (current.next !== null) {
            current.next = current.next.next;
        }
    }

    // Search for a node with the given value
    search(value: number): ListNode | null {
        let current = this.head;
        while (current !== null && current.value !== value) {
            current = current.next;
        }
        return current;
    }

    // Print all values in the list
    printList(): void {
        let current = this.head;
        while (current !== null) {
            console.log(current.value);
            current = current.next;
        }
    }
}

const list = new LinkedList();
list.append(10);
list.append(20);
list.append(30);

console.log("Initial List:");
list.printList(); // Output: 10 20 30

list.prepend(5);
console.log("After Prepending 5:");
list.printList(); // Output: 5 10 20 30

list.delete(20);
console.log("After Deleting 20:");
list.printList(); // Output: 5 10 30

const node = list.search(10);
if (node) {
    console.log("Found Node:", node.value); // Output: Found Node: 10
} else {
    console.log("Node not found");
}

```
