## Bubble Sort
#### Klassik
```java
public static void bubbleSortClassic(int[] arr) {  
    int temp;  
  
    for (int i = 0; i < arr.length - 1; i++) {  
        for (int j = 0; j < arr.length - 1; j++) {  
            if (arr[j+1] < arr[j]) {  
                temp = arr[j];  
                arr[j] = arr[j+1];  
                arr[j+1] = temp;  
            }  
        }
    }
}
```
#### Normal
```java
public static void bubbleSortNormal(int[] arr) {  
    int temp;  
    boolean swapped;  
  
    do {  
        swapped = false;  
        for (int i = 0; i < arr.length - 1; i++) {  
            if (arr[i+1] < arr[i]) {  
                temp = arr[i];  
                arr[i] = arr[i+1];  
                arr[i+1] = temp;  
                swapped = true;  
            }  
        }    
    } while (swapped);  
}
```
#### Optimiert
```java
public static void bubbleSortOptimized(int[] arr) {  
    int temp;  
    boolean swapped;  
    int i = 0;  
  
    do {  
        swapped = false;  
        for (int j = 0; j < arr.length - 1 - i; j++) {  
            if (arr[j+1] < arr[j]) {  
                temp = arr[j];  
                arr[j] = arr[j+1];  
                arr[j+1] = temp;  
                swapped = true;  
            }  
        }        
        i++;  
    } while (swapped);  
}
```

## Selection Sort
```java
public static void selectionSort(int[] arr) {  
    int temp, minPos;  
    for (int insPos = 0; insPos < arr.length; insPos++) {  
        minPos = insPos;  
        for (int i = insPos; i < arr.length; i++) {  
            if (arr[i] < arr[minPos]) {  
                minPos = i;  
            }  
        }        temp = arr[insPos];  
        arr[insPos] = arr[minPos];  
        arr[minPos] = temp;  
    }  
}
```
## Insertion Sort
```java
public static void insertionSort(int[] arr) {  
    for (int i = 1; i < arr.length; i++) {  
        if (arr[i] < arr[i-1]) {  
            int insPos = i;  
            int insValue = arr[i];  
            while (insPos > 0 && insValue < arr[insPos - 1]) {  
                arr[insPos] = arr[insPos - 1];  
                insPos--;  
            }  
            arr[insPos] = insValue;  
        }  
    }
}
```

## Quick Sort
```java
public static void quickSort( int [] arr, int left, int right) {  
    int middle = (right + left) / 2; 
     
    if( arr[left] < arr[middle] && arr[middle] < arr[right]) {  
        swap(arr, right, middle);  
    } else if( arr[middle] < arr[left] && arr[left] < arr[right]) {  
        swap(arr, right, left);  
    }  
  
    int pivot = arr[right];  
    int i = left, j = right-1;  
    while( i <= j ) {  
        while( i < right && arr[i] <= pivot) {                  
			i++;  
        }  
        while( j >= left && arr[j] >= pivot) {  
            j--;  
        }  
        if (i < j) {  
            swap( arr, i, j);  
        }  
    }    
    
    swap(arr, right, i);  
    int newRight = i - 1, newLeft = i + 1;  
  
    if ( left < newRight) {  
        quickSort( arr, left, newRight);  
    }  
  
    if ( newLeft < right) {  
        quickSort( arr, newLeft, right);  
    }  
}
```

#### Swap
```java
public static void swap(int [] arr, int i, int j){  
    int temp = arr[i];  
    arr[i] = arr[j];  
    arr[j] = temp;  
}
```