# link #


# 383. Ransom Note #
https://leetcode.com/problems/ransom-note/?envType=study-plan-v2&envId=top-interview-150
  - few test case are not getting passed try WITHOUT HASHING in free time
    
**Without hashing**

```
bool canConstruct(char* ransomNote, char* magazine) 
{
    int i=0,j=0,count=0,index=-1;
    while(*(ransomNote+i)!='\0')
    {        
            j=0;
        while(*(magazine+j)!='\0')
        {
            if(j==index)
            {
                j++;
                continue;
            }
            if(*(ransomNote+i) ==*(magazine+j))
            {
                count++;
                index =j;
                break;
            }
            j++;
        }
        i++;
    }
    if(count == strlen(ransomNote))
    {
        return true;
    }
    else
    {
        return false;
    }
    

    
}
```
**algo using Hashing**

Your algorithm efficiently checks whether ransomNote can be constructed using letters from magazine, ensuring each letter is used only once. It uses hashing via an array (freq[26]) to store character frequencies efficiently

HOW HASHING WORKS IN MY ALGO
- A hash function (char - 'a') maps each lowercase letter ('a' to 'z') to a unique index (0 to 25).
- The freq array acts as a hash table, storing counts of each letter from magazine.
- Each lookup and update operation occurs in O(1) constant time, making it highly efficient.
-steps in algo
  - 1️⃣Create a frequency table (array freq[26]) to count occurrences of each letter in magazine.
  - 2️⃣ Loop through each letter in magazine, storing its frequency in freq.
  - 3️⃣ Loop through each letter in ransomNote, checking if it's available in freq.
      - If the letter count in freq is zero, return false.
      - Otherwise, decrement the frequency in freq.
  - 4️⃣ If all letters in ransomNote were found, return true
  
![image](https://github.com/user-attachments/assets/f2aec970-c7e1-4a6b-958c-3dc2abc12c7e)

 - Time Complexity Analysis
    - Building frequency table (magazine) → O(m)
    - Checking ransomNote requirements → O(n)
    - Overall Complexity: O(m + n) (Fast and optimized)
- Why Hashing is Efficient
  - Direct Access → No need to search for letters, lookup happens in constant time (O(1)).
  - Avoids Sorting or Nested Loops → Faster than O(n²) brute-force methods.
  - Memory-Efficient → Uses only 26 integer slots instead of complex data structures.


```
bool canConstruct(char* ransomNote, char* magazine) 
{
    int freq[26] = {0};
    //store freq of each element in magazine in hash table
    for(int i=0;magazine[i]!='\0';i++)
    {
        freq[magazine[i]-97]++;
    }
    for(int i =0;ransomNote[i]!='\0';i++)
    {
        if(freq[ransomNote[i]-97]==0)
        {
            return false;
        }
        freq[ransomNote[i]-97]--;
    
    }
    return true;
```


# selection sort #

Selection Sort is a simple sorting algorithm that repeatedly **finds the minimum element from the unsorted part of the array and swaps it with the first element of the unsorted section. sorted array is in ascending order**. It works by dividing the array into two parts: the sorted portion and the unsorted portion.

**How Selection Sort Works:**
- Find the smallest element in the unsorted section.
- Swap it with the first element of the unsorted section.
- Move the boundary between sorted and unsorted sections one step forward.
- Repeat until the entire array is sorted.

**Step-by-Step Explanation of Your Selection Sort Logic**
  - ```for(int i=0; i<=n-2; i++)```
    - The outer loop iterates through the array from index 0 to n-2.
    - Why n-2? Because the last element doesn’t need a selection step—once the second-last element is sorted, the last one is automatically in place.
  - ```int min = i;```
    - min holds the index of the smallest element found in the unsorted portion of the array.
    - Initially, we assume the first element of the unsorted section (arr[i]) is the smallest.
 - ```for(int j=i+1; j<n; j++)```
    - Inner loop searches for the smallest element from i+1 to n-1.
    - It compares every element arr[j] with arr[min] to find the minimum.
 - if(arr[j] < arr[min]){
    min = j;}   
    - If arr[j] is smaller than arr[min], update min to j, marking the new smallest element.
 - Swapping the Minimum Element
    - Once the smallest element is found, swap it with arr[i], placing it in its correct position.
    - This ensures that the sorted section grows and the unsorted section shrinks in each iteration.

  - How Sorting Progresses
    - Iteration 1: Finds the smallest element in the entire array and places it at index 0.
    - Iteration 2: Finds the next smallest element and places it at index 1.
    - Iteration 3: Finds the next smallest element and places it at index 2.
    - …until the entire array is sorted.
      
**Time complexity:** O($n^2$), (where N = size of the array), for the best, worst, and average cases.
Reason: If we carefully observe, we can notice that the outer loop, say i, is running from 0 to n-2 i.e. n-1 times, and for each i, the inner loop j runs from i to n-1. For, i = 0, the inner loop runs n-1 times, for i = 1, the inner loop runs n-2 times, and so on. So, the total steps will be approximately the following: (n-1) + (n-2) + (n-3) + ……..+ 3 + 2 + 1. The summation is approximately the sum of the first n natural numbers i.e. (n*(n+1))/2. The precise time complexity will be O(n2/2 + n/2). Previously, we have learned that we can ignore the lower values as well as the constant coefficients. So, the time complexity is O(n2). Here the value of n is N i.e. the size of the array.

Space Complexity: O(1)

```

int main() {

int arr[] = {13,46,9,52,20,9};
int n = sizeof(arr)/sizeof(arr[0]);
//print sorted  array
printf("unsorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
printf("\n");
//sorting
for(int i=0;i<=n-2;i++)
{
    int min = i;
    for(int j=i+1;j<n;j++)
    {
        if(arr[j]<arr[min])
        {
            min = j;
        }
    }
    //swaping
    int temp =arr[min];
    arr[min]= arr[i];
    arr[i]=temp;
}
//print sorted  array
printf("sorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
    return 0;
}

```
