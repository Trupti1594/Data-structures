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
    
**O(n^2)**
----------
# Space complexity #
- Amount of space taken by an algo as a function of input size (n).Its not the actual space taken by the program.
- Our code consist of input and auxilary input so space complexity is calculated for auxilary input not for actual input.
  - Example arr[] is an input array, so the quesn is like store the square of each element of input array (arr[]) to the squar[]. so if arr will have 10 elements so squar will also have squared value of 10 elements. so space complexityu for squar[] is O(n).
