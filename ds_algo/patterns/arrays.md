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

### Important java methods in arrays

#### System.arraycopy()
- Copies elements from source array to destination array with startIndex of source, startIndex of destination and number of elements
- System.arraycopy(sourceArr, 0, destArr, l,sourceArr.length)
