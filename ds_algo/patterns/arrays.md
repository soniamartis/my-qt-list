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

### Moore's voting algo
- Used to find the majority element
- eg1: [2,2,2,2,4,5,6]
- In this example, 3 of the 2's are offset by rest of the numbers and yet 2 stays in majority by 1
```java
        int count = 0;
        int num = -1;
        for(int i=0;i<arr.length;i++){
            if(count==0){
                num = arr[i];
                count++;
            }
            else{
                if(arr[i]==num){
                    count++; // increase the count of 2
                }
                else{
                    count--; // offset the count of 2 if the current number is not 2
                }
            }
        }
        
        if(isMajority(num, arr)){ // check is required for validation
            return num;
        }
        return -1;
```

### Kadane's algorithm
- Used to find max subarray sum
```java
        int maxSoFar = arr[0];
        int currMax = arr[0];
        for(int i=1;i<arr.length;i++){
            currMax = Math.max(arr[i], arr[i]+ currMax);
            maxSoFar = Math.max(currMax,maxSoFar); 
        }
        
        return maxSoFar;
```  



### Important java methods in arrays

#### System.arraycopy()
- Copies elements from source array to destination array with startIndex of source, startIndex of destination and number of elements
- System.arraycopy(sourceArr, 0, destArr, l,sourceArr.length)


### Arrays Extra information
- Java uses TimSort which is a combination of insertion sort and merge sort and is a stable sorting algorithm
- A stable algo preserves the insertion order of the elements of the array while sorting


