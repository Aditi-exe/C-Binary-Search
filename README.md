# Binary Search 

Binary search is an algorithm for finding the position of a target value within a sorted array. It works by repeatedly dividing the search interval in half until the target value is found or the search interval is empty. 
Binary search requires the array to be sorted in order for it to work correctly. If the array is not sorted, binary search will not find the target value correctly.

The process of a binary search algorithm can be represented in the following manner:

![Working of a binary search algorithm](https://res.cloudinary.com/practicaldev/image/fetch/s--Uj818KRw--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/i/5hsod7t93v85b23rk671.png)

An implementation of Binary Search is given below:

```
#include <stdio.h>

int binarySearch(int arr[], int n, int x) {
    int left = 0, right = n - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == x)
            return mid;
        else if (arr[mid] < x)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return -1; // If element is not present in array
}

int main() {
    int arr[] = { 2, 3, 4, 10, 40 };
    int n = sizeof(arr) / sizeof(arr[0]);
    int x = 10;
    int result = binarySearch(arr, n, x);
    if (result == -1)
        printf("Element is not present in array");
    else
        printf("Element is present at index %d", result);
    return 0;
}
```

In this implementation, the binarySearch function takes an array arr of size n and a value x to search for. It initializes two pointers, left and right, to the beginning and end of the array, respectively. It then enters a while loop that continues until left is greater than right. On each iteration, it calculates the midpoint mid of the current range and compares the value at that index to the search value x. If arr[mid] is equal to x, the function returns mid. If arr[mid] is less than x, the range is shifted to the right of mid. If arr[mid] is greater than x, the range is shifted to the left of mid. If the while loop completes without finding x, the function returns -1.

In the main function, an example array arr is defined, along with its size n and a value x to search for. The binarySearch function is called with these values, and the result is stored in the result variable. If result is -1, the element was not found in the array, and a message is printed to that effect. If result is not -1, the element was found, and its index is printed.


The program in this repository demonstrates binary search by first sorting the given array using Bubble Sort, the basics of which are given below:

## Bubble Sort

Bubble sort is a simple sorting algorithm that repeatedly steps through a list of elements, compares adjacent elements and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted.

Bubble sort can be represented as follows:

![Bubble Sorting procedure](http://www.computersciencebytes.com/wp-content/uploads/2016/10/bubble_sort.png)

Algorithm for bubble sort:
1. Start at the beginning of the list and compare the first two elements.
2. If the first element is greater than the second element, swap them.
3. Move to the next pair of elements and repeat step 2.
4. Continue through the list until no more swaps are needed (i.e. the list is sorted).
Here is an example of bubble sort in action:

Considering an unsorted list: [5, 2, 8, 4, 7]

First pass:

- Compare 5 and 2, swap them => [2, 5, 8, 4, 7]
- Compare 5 and 8, do not swap => [2, 5, 8, 4, 7]
- Compare 8 and 4, swap them => [2, 5, 4, 8, 7]
- Compare 8 and 7, swap them => [2, 5, 4, 7, 8]

Second pass:

- Compare 2 and 5, do not swap => [2, 5, 4, 7, 8]
- Compare 5 and 4, swap them => [2, 4, 5, 7, 8]
- Compare 5 and 7, do not swap => [2, 4, 5, 7, 8]

Third pass:

- Compare 2 and 4, do not swap => [2, 4, 5, 7, 8]
- Compare 4 and 5, do not swap => [2, 4, 5, 7, 8]
- Compare 5 and 7, do not swap => [2, 4, 5, 7, 8]

After the third pass, the list is sorted in ascending order.


### Code:

```
// implementing binary search

#include <stdio.h>

void Bubble(int a[], int n);
int Binary(int a[], int element, int n);

int main()
{
    int arr[5] = {23, 17, 8, 95, 14};

    int key;

    printf("Enter an element: ");
    scanf("%d", &key);

    // calling the sort and search functions
    Bubble(arr, 5);
    int result = Binary(arr, key, 5);

    if(result == 1)
    {
        printf("Element found.\n");
    }
    else
    {
        printf("Element not found.\n");
    }
    

    return 0;
}


// bubble sort (ascending order)
void Bubble(int a[], int n)
{
    // no. of passes (p) and no. of comparisons for each pass
    int p = n - 1;
    int c = n - 1;

    int i, j;

    for(i = 0; i < p; i++)
    {
        for(j = 0; j < c - i; j++)
        {
            // swapping the adjacent elements if the first is larger than the second 
            if(a[j] > a[j + 1])
            {
                int temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }

        }
    }
}


// binary search
int Binary(int a[], int element, int n)
{
    int lower = 0;
    int upper = n;

    int mid;

    while(lower <= upper)
    {
        // finding the middle element of the passed array
        mid = (lower + upper) / 2;

        if(element == a[mid])
        {
            return 1;
        }
        else if(element > a[mid])
        {
            lower = mid + 1;
        }
        else
        {
            upper = mid - 1;
        }

    }

    return -1;
}
```

### Output:

![binarySearch.c output](https://github.com/Aditi-exe/C-Binary-Search/blob/main/binarySearch.png)

