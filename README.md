# Data-structures #
lectures: https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/video_galleries/lecture-videos/
# Time complexity #
- Time complexity is not the time taken by an algorithm to run on a machine.
- Rate at which the time taken increases wrt the input size.It is the time taken by an algo/operation as a function of input size(n).
- Time complexity is represented in **BIG O notation**. This represents the worst case senario or upper bound.For **average case theta()**. For **best case omega**.
- O(1) is called best time complexity.
- Rules are important while calculating the time complexity of any algo
  1) Time complexity ios calculated for worst case senario.
  2) Avoid constants.
  3) Avoid lower values and consider higher values.
  ![image](https://github.com/user-attachments/assets/ed909dff-bec7-4f3e-907b-c1a26954803c)

As the values of timecomplexity go near y axis the algo beacomes the worst.

**O(1)**
----------
- Example: Check Even/Odd Using Bitwise AND
```
#include <stdio.h>
void checkEvenOdd(int num) {
    if (num & 1)  // Bitwise AND with 1 (O(1) operation)
        printf("%d is Odd\n", num);
    else
        printf("%d is Even\n", num);
}

int main() {
    int num = 37; // Example number
    checkEvenOdd(num); // O(1) execution

    return 0;
}
```
- The operation num & 1 is constant time (O(1)) since it performs a single bitwise AND operation.
- It does not depend on the size of the number or involve loops or recursion. So timecoplexity is O(1), as even though input is 10^6 still the if condition will get execute for once only.

**O(n) linear time complexity**
--------------------------------

- Example: Print the elements of an array
```
#include <stdio.h>

int main() {
    int arr[] = {5, 10, 15, 20, 25};  
    int n = sizeof(arr) / sizeof(arr[0]);

    for (int i = 0; i < n; i++)
    {  // Loop runs 'n' times
        printf("%d ", arr[i]);
    }
    
    return 0;
}
```

- Why is this O(n)?
  - The loop iterates through all elements once.And for "n" no. of elements it will run "n" times
  - As the array size n increases, execution time linearly increases.
  - No nested loops or extra computations—just one full traversal.
    
**O($n^2$) **
--------------------------

- Example: Bubble Sort algorithm in C

```
#include <stdio.h>

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};  
    int n = sizeof(arr) / sizeof(arr[0]);  

    for (int i = 0; i < n - 1; i++)
    {  
        for (int j = 0; j < n - i - 1; j++)
        {  
            if (arr[j] > arr[j + 1])
            {  
                // Swap arr[j] and arr[j+1]
                int temp = arr[j];  
                arr[j] = arr[j + 1];  
                arr[j + 1] = temp;  
            }
        }
    }

    printf("Sorted array: ");
    for (int i = 0; i < n; i++) {  
        printf("%d ", arr[i]);  
    }

    return 0;
}
```
**Why is Bubble Sort O(n²)?**
- Nested loops: The outer loop runs (n-1) times we can consider it as n times only, and the inner loop runs (n-i-1) times.
- Worst case: If the array is reverse sorted, every element must be compared and swapped, leading to O(n²) complexity.
- Not efficient for large datasets, but useful for small or nearly sorted arrays.
![image](https://github.com/user-attachments/assets/0d055179-d93c-4414-b649-03a145f97fba)

![image](https://github.com/user-attachments/assets/a384104a-2bd3-4d11-a850-ced34092e189)

**O($n^3$)**
-------------
![image](https://github.com/user-attachments/assets/c5ad209e-fe06-4278-a2ee-e4f7d9b27984)

- Example: Nested Loops (Matrix Multiplication)
```
#include <stdio.h>

#define N 3  // Matrix size

int main() {
    int A[N][N] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    int B[N][N] = {{9, 8, 7}, {6, 5,4}, {3, 2, 1}};
    int C[N][N] = {0};  // Result matrix initialized to zero

    // Triple nested loop (O(n³))
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            for (int k = 0; k < N; k++) {
                C[i][j] += A[i][k] * B[k][j];  // Matrix multiplication
            }
        }
    }

    // Print result matrix
    printf("Resultant Matrix:\n");
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            printf("%d ", C[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

**O(logn)**
-------------
![image](https://github.com/user-attachments/assets/ef501634-0c90-4ec7-a9ee-c249e3c3896b)

- Example: Binary search(applied only on sorted array otherwise dont apply)

```
Certainly! Binary Search is an efficient algorithm for searching a sorted array, with a time complexity of O(log n). It works by repeatedly dividing the search range in half.
C Code for Binary Search (O(log n))
#include <stdio.h>

int binarySearch(int arr[], int left, int right, int target) {
    while (left <= right) {
        int mid = left + (right - left) / 2;  // Calculate middle index

        if (arr[mid] == target)  
            return mid;  // Found the target, return index
        else if (arr[mid] < target)  
            left = mid + 1;  // Search right half
        else  
            right = mid - 1;  // Search left half
    }
    return -1;  // Target not found
}

int main() {
    int arr[] = {10, 20, 30, 40, 50, 60, 70};  // Sorted array
    int n = sizeof(arr) / sizeof(arr[0]);  
    int target = 40;

    int result = binarySearch(arr, 0, n - 1, target);
    
    if (result != -1)
        printf("Element found at index %d\n", result);
    else
        printf("Element not found\n");

    return 0;
}
```
Why is Binary Search O(log n)?
- Each iteration divides the array in half, reducing the search space exponentially.
- If the array has n elements, binary search completes in log₂(n) steps.
- More efficient than linear search (O(n)), especially for large datasets.

Would you like an example with recursion instead of loops? 


# Space complexity #
- Amount of space taken by an algo as a function of input size (n).Its not the actual space taken by the program.
- Our code consist of input and auxilary input so space complexity is calculated for auxilary input not for actual input.
  - Example arr[] is an input array, so the quesn is like store the square of each element of input array (arr[]) to the squar[]. so if arr will have 10 elements so squar will also have squared value of 10 elements. so space complexityu for squar[] is O(n).
