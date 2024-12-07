# Array patterns

### Merge 2 arrays
```java
int l = 0, r = 0, int k = 0;
int []arr = new int[len];
while(l < arr1.length && r < arr2.length){
  if(arr1[l]<arr2[r]){
    arr[k++] = arr1[l++];
  }
  else{
    arr[k++] = arr2[r++]; 
 }
}

//remaining elements
while(l<arr1.length){
  arr[k++] = arr1[l++];
}
while(r<arr2.length){
  arr[k++] = arr2[r++];
}
```

### Quicksort partitioning
- Partition the array around a pivot(could be first element, last element, random element)
- Such that all elems less than pivot lie to the left and all greater than pivot to the right
- This partition function puts the pivot at its correct sorted location, so it desnt need to be included any further for sorting
- Unstable sorting algo, but fast and easily cacheable, as we do not require any arrays
- Worst case occurs when elements are already sorted and is O(n^2)
```java
int partition(int []arr, int low, int high){
        int pivot = arr[high];
        int index = low-1;
        for(int i=low;i<high;i++){
            if(arr[i]<pivot){
               index++;
               swap(arr,i,index);
            }
        }
        index++;
        swap(arr,high,index);
        return index;
}

```



### Important java methods in arrays

#### System.arraycopy()
- Copies elements from source array to destination array with startIndex of source, startIndex of destination and number of elements
- System.arraycopy(sourceArr, 0, destArr, l,sourceArr.length)


### Arrays Extra information
- Java uses TimSort which is a combination of insertion sort and merge sort and is a stable sorting algorithm
- A stable algo preserves the insertion order of the elements of the array while sorting


