# Sort Algorithms

### Bubble Sort

**Time Complexity: O(n^2)**

* Start at the beginning of an array.
* Swap the first two element if the first is bigger/smaller than the second.
* Go to next pair.
* In the end of first scanning, the last element must the biggest/smallest one in this array.

Implementation:

```java
void bubbleSort(int[] arr) {
    int len = arr.length;
    // O(n^2)
    for (int i = 0; i < len - 1; i++) {
        for(int j = 0; j < len -1 - i; j++) {
            int first = arr[j];
            int second = arr[j+1];
            if(first > second) {
                arr[j] = second;
                arr[j+1] = first;
            }
        }
    }
}
```

### Selection Sort

**Time Complexity: O(n^2)**

* Linear scan to find the smallest element and move it to the front
* Find the next sallest element in the rest, and move on

Implementation:

```java
void selectionSort(int[] arr) {
    int len = arr.length;
    // O(n^2)
    for (int i = 0; i < len - 1; i++) {
        // Find the minimum element in unsorted array
        int minP = i;
        for(int j = i; j < len; j++) {
            if(arr[j] < arr[minP])
                minP = j;
        }
        int temp = arr[i];
        arr[i] = arr[minP];
        arr[minP] = temp;
    }
}
```

### Merge Sort

Merge sort is a stable sort, but not in place.

**Time Complexity: O(n Log n)**

* Sort each **pair** of elements.
* Sort every four elements by mergin every two pairs.
* Continue until all elements are in place.

![merge sort](img/Merge-Sort.png)

Implementation:

```java
void merge(int[] arr, int left, int mid, int right) {
    int leftLen = mid - left + 1;
    int rightLen =  right - mid;
    int len = leftLen + rightLen;
    int[] L = new int[leftLen];
    int[] R = new int[rightLen];
    for (int i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for (int i = 0; i < n2; i++)
        R[i] = arr[mid + 1+ i];

    int l = 0;
    int r = 0;
    int i = 0;
    while (l < leftLen && r < rightLen) {
        if (L[i] <= R[j]) {
            arr[i] = L[l];
            l++;
        } else {
            arr[i] = R[r];
            r++;
        }
        i++;
    } 

    while (l < leftLen) {
        arr[i] = L[l];
        i++;
        l++;
    }
 
    while (r < rightLen) {
        arr[i] = R[r];
        r++;
        i++;
    }
    
}

void sort(int[] arr, int left, int right) {
    if(left < right) {
        int mid = (left+right) / 2;
        sort(arr, left, mid);
        sort(arr, mid+1, right);
        merge(arr, left, mid, right);
    }
}

void mergeSort(int[] arr) {
    int len = arr.length;
    sort(arr, 0, len -1);
}
```

### Quick Sort

**Time Complexity: Expected O(n Log n), Worst Case O(n^2)**

* Pick a random element, first, last or pure random as pivot.
* Partition the array, such that all numbers that are less than it come before all elements that are greater than it.
* Continue for each half.

Implementation: always pick the last as pivot.

```java
void partition(int[] arr, int left, int right) {
    int pivot = arr[right];
    int low = left;
    for(int i = left; i < right; i++) {
        if(arr[i] < pivot) {
            int temp = arr[i];
            arr[i] = arr[low];
            arr[low] = temp;
            low++;
        }
    }

    // swap arr[i+1] and arr[high] (or pivot)
    int temp = arr[i+1];
    arr[i+1] = arr[high];
    arr[high] = temp;
}

void quickSort(int[] arr) {
    sort(arr, 0, arr.length -1);
}
```

### Bucket Sort

Bucket sort is mainly useful when input is **uniformly distributed** over a range

**Time Complexity: O(n + m)**

* Partition the array into a finite number of buckets.
* Sort each bucket individually.

