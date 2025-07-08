Absolutely, Trupti! Here's a **targeted interview question set** covering **arrays, pointers, stacks, queues, bitwise operations, and trees**—all tailored for embedded systems and Qualcomm-style interviews:

---

## 🔢 **Arrays**

1. Rotate an array of size `n` to the right by `k` positions in-place. -> practise optimal approach, brutforce is given below
2. Find the subarray with the maximum sum (Kadane’s Algorithm).
3. Remove duplicates from a sorted array in-place.
4. Merge two sorted arrays without using extra space.
5. Given an array of size `n`, find the missing number from 1 to `n`.

---

## 🧭 **Pointers (C-specific)**

1. What’s the difference between `char *str = "abc"` and `char str[] = "abc"`?
2. Implement a function that swaps two integers using pointers.
3. What is a dangling pointer? How do you avoid it?
4. Explain `const int *ptr`, `int *const ptr`, and `const int *const ptr`.
5. Write a function that returns a pointer to the maximum element in an array.

---

## 📚 **Stacks**

1. Implement a stack using arrays with push, pop, and getMin in O(1).
2. Evaluate a postfix expression using a stack.
3. Check for balanced parentheses in an expression.
4. Design a stack that supports `getMiddle()` in O(1) time.
5. Convert infix to postfix notation using a stack.

---

## 📬 **Queues**

1. Implement a circular queue using arrays.
2. Implement a queue using two stacks.
3. Design a queue that supports `getMax()` in O(1).
4. Simulate a task scheduler using a queue (e.g., round-robin).
5. Reverse the first `k` elements of a queue.

---

## 🧮 **Bitwise Operations**

1. Count the number of set bits in an integer.
2. Check if a number is a power of 2 using bitwise operators.
3. Swap two numbers without using a temporary variable.
4. Reverse bits of a 32-bit unsigned integer.
5. Find the only non-repeating element in an array where every other element repeats twice.

---

## 🌳 **Trees**

1. Inorder, Preorder, and Postorder traversal (recursive and iterative).
2. Find the Lowest Common Ancestor (LCA) of two nodes in a binary tree.
3. Check if a binary tree is height-balanced.
4. Serialize and deserialize a binary tree.
5. Convert a binary tree to its mirror tree.

---

Would you like me to turn this into a printable PDF workbook or simulate a mock round with 2–3 questions from each topic? I can also add Qualcomm-style follow-ups and edge cases to test your thinking under 


-------------------------------------------------------------------------------------------------------------------------------------------------------
**Rotate an array of size `n` to the right by `k` positions in-place**
```

// Approach1 brute force
#include <stdio.h>

void rotate_array(int arr[],int n,int k)
{
    //rotate array right by k times
    int i=1;
    while(i<=k)
    {
        int temp = arr[n-1];
        int j = n-1;
        
        while(j>0)
        {
            arr[j]= arr[j-1];
            j--;
        }
        arr[j]=temp;
        i++;
    }
}


int main() {

int arr[] = {1,2,3,4,5,6,7};
int k;
int n = sizeof(arr)/sizeof(arr[0]);

printf("unsorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
printf("\nRatate the array by how many times to right\n");
scanf("%d",&k);
rotate_array(arr,n,k);
printf("\nfinal array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}

    return 0;
}
```
