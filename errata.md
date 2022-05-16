# Errata for *Book Title*

***

### page 22
On **page 22**

**Before**:
```latex
$(-1)^{\text{sign}} \times 2^{e-127} \times \left(1 + \sum_{i=1}^{23} b_{52-i} 2^{-i} \right)$
```

**Corrected**
```latex
$(-1)^{\text{sign}} \times 2^{e-1023} \times \left(1 + \sum_{i=1}^{52} b_{52-i} 2^{-i} \right)$
```


*** 

### page 23
On **page 23**

**Before**: 0.00110011

**Corrected**: 0.000110011

***

### page 65
On **page 65** [Summary of error]:

**Before**:
```javascript
var evenOffset = pos % 2 == 0 ? 1 : 0,
    offsetMinus = Math.floor(pos / 2) - evenOffset,
    offsetPlus = Math.floor(pos / 2) + evenOffset;


if (median1 < median2) {
    return medianOfTwoSortedArray(arr1.slice(offsetMinus), arr2.slice(offsetMinus), offsetPlus);
} else {
    return medianOfTwoSortedArray(arr2.slice(offsetMinus), arr1.slice(offsetMinus), offsetPlus);
}
```

**Corrected**:
```javascript
var evenOffset = pos % 2 == 0 ? 1 : 0,
    offsetMinus = Math.floor(pos / 2) - evenOffset,
    offsetPlus = pos - Math.floor(pos / 2) + evenOffset;


if (median1 < median2) {
    return medianOfTwoSortedArray(arr1.slice(offsetMinus), arr2.slice(0, -offsetMinus), offsetPlus);
} else {
    return medianOfTwoSortedArray(arr2.slice(offsetMinus), arr1.slice(0, -offsetMinus), offsetPlus);
}
```

***

### page 70
On **page 70** [Summary of error]:
 
Details of error here. Highlight key pieces in **bold**.

**Before**:
```javascript
var matrix3by3 = [[1,2,3],[4,5,6],[7,8,9]];
matrix3by3[0]; // [1,2,3] 
matrix3by3[1]; // [4,5,6]
matrix3by3[1]; // [7,8,9]
```

**After**:
```javascript
var matrix3by3 = [[1,2,3],[4,5,6],[7,8,9]];
matrix3by3[0]; // [1,2,3] 
matrix3by3[1]; // [4,5,6]
matrix3by3[2]; // [7,8,9]
```

***

### page 130
On **page 130** [Summary of error]:
 
Bubble sort had minor **index** issue.

**Before**:
```javascript
function bubbleSort(array) {
    for (var i = 0, arrayLength = array.length; i < arrayLength; i++) {
        for (var j = 0; j <= i; j++) {
            if (array[i] < array[j]) {
                var temp = array[i];
                array[i] = array[j];
                array[j] = temp;
            }
        }
    }
    return array;
}
```

**Corrected**:
```javascript
function bubbleSort(array) {
    for (var i = 0, arrayLength = array.length; i < arrayLength; i++) {
        for (var j = 0; j < arrayLength - 1 - i; j++) {
            if (array[j] > array[j+1]) {
                var temp = array[j];
                array[j] = array[j+1];
                array[j+1] = temp;
            }
        }
    }
    return array;
}
```

***

### page 183

On **page 183** [Summary of error]:

**Before**:
```javascript
DoublyLinkedList.prototype.deleteAtHead = function() {
    var toReturn = null;

    if (this.head !== null) {
        toReturn = this.head.data;

        if (this.tail === this.head) {
            this.head = null;
            this.tail = null;
        } else {
            this.head = this.head.next;
            this.head.prev = null;
        }
    }
    this.size--;
    return toReturn;
}
```

**Corrected**:
```javascript
SinglyLinkedList.prototype.deleteAtHead = function() {
    var toReturn = null;

    if (this.head !== null) {
      toReturn = this.head.data;
      this.head = this.head.next;
      this.size--;
    }
    return toReturn;
}
```

***


On **AVL Trees** [Summary of error]:

`getDepthFromChildren()` and `updateInNewLocation()` needs to be renamed to: `setDepthBasedOnChildren()`
