# Typescript-Programs

## Algorithims

### 1. **Binary Search Algorith(Iterative method)**

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
### 2. **Binary Search Algorith(Recursive method)**

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
