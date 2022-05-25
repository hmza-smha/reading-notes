# Insertion Sort

### Insertion sort is a simple sorting algorithm that builds the final sorted array (or list) one item at a time.

#### Insertion sort is a simple sorting algorithm that works similar to the way you sort playing cards in your hands. The array is virtually split into a sorted and an unsorted part. Values from the unsorted part are picked and placed at the correct position in the sorted part.

```
InsertionSort(int[] arr)

    FOR i = 1 to arr.length

      int j <-- i - 1
      int temp <-- arr[i]

      WHILE j >= 0 AND temp < arr[j]
        arr[j + 1] <-- arr[j]
        j <-- j - 1

      arr[j + 1] <-- temp

```

![image](images/Insertion-sort-example-300px.gif)

At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there. It repeats until no input elements remain.

Sorting is typically done in-place,

## Code 

```c#
    void sort(int[] arr)
    {
        int n = arr.Length;
        for (int i = 1; i < n; ++i) {
            int temp = arr[i];
            int j = i - 1;
 
            while (j >= 0 && arr[j] > temp) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = temp;
        }
    }
```

## Trace
Sample Array: ```[8, 4, 23, 42, 16, 15]```

**Pass 1:**

Take the **second** element => ```4```, keep comparing it with the previous elements.
1. if the previous element is greater then SWAP places.
2. else take the next element *(third element)*.

```8``` > ```4``` ? yes! then swap.

=> ```[4, 8, 23, 42, 16, 15]```

**Pass 2:**

Take the **third** element => ```23```, keep comparing it with the previous elements
1. if the previous element is greater then SWAP places.
2. else take the next element *(4th element)*.

```8``` > ```23``` ? No! then stop, and take the next element i.e. ```42```.

=> ```[4, 8, 23, 42, 16, 15]```

**Pass 3:**

Take the **4th** element => ```42```, keep comparing it with the previous elements
1. if the previous element is greater then SWAP places.
2. else take the next element *(5th element)*.

```23``` > ```42``` ? No! then take the next element i.e. ```16```.

=> ```[4, 8, 23, 42, 16, 15]```

**Pass 4:**

**5th** element => ```16```

```42``` > ```16``` ? yes! then swap.

=> ```[4, 8, 23, 16, 42, 15]```

```23``` > ```16``` ? yes! then swap.

=> ```[4, 8, 16, 23, 42, 15]```

```8``` > ```16``` ? No! then take the next element i.e. ```15```.

**Pass 6:**

**6th** element => ```15```

```42``` > ```15``` ? yes! then swap.

=> ```[4, 8, 16, 23, 15, 42]```

```23``` > ```15``` ? yes! then swap.

=> ```[4, 8, 16, 15, 23, 42]```

```16``` > ```15``` ? yes! then swap.

=> ```[4, 8, 15, 16, 23, 42]```

```8``` > ```15``` ? No! then STOP.

## Complexity
- Time: O(N^2) 
- Space: O(1)