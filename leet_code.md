# link #

# 27. Remove Element #

https://leetcode.com/problems/remove-element/description/?envType=study-plan-v2&envId=top-interview-150

Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

**logic**
  - **Use two pointer approach**
    - One pointer (i) keeps track of where the next valid element should be stored.
    - The second pointer (j) scans the array looking for elements that should be kept.
  -  wrong approach : Dont shift the elemnets of an array its tedious approach, instaead of shifting just play with array index.

**code**
- Step 1: Start with an empty position (i = 0)
  - i represents the new size of the array (where valid elements will be stored).
  - j moves through the array one element at a time to check each value.
- Step 2: Process each element
  - If nums[j] == val, we skip it (don’t copy it).
  - If nums[j] != val, we copy it to nums[i], then move i forward.
- Step 3: Return i as the new array size
- After scanning all elements, i tells us how many valid elements remain.

```
int removeElement(int* nums, int numsSize, int val) {

int i=0;
for(int j=0;j<numsSize;j++)
{
    if(nums[j]!=val)
    {
        nums[i]=nums[j];
        i++;
    }
}
return i;
}
```

# 26. Remove Duplicates from Sorted Array #

Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.

**logic**
  - **Using Two Pointers approach(i and j)**
    - i tracks the position where the next unique element should be stored.
    - j iterates through the array to find elements different from the last stored unique value (nums[i]).
  - When a Unique Element is Found
    - If nums[j] is not a duplicate (nums[i] != nums[j]), copy nums[j] to nums[i + 1] (next available spot).
    - Move i forward to reflect the new unique element count.
  -  Return the Count of Unique Elements
    - i + 1 is returned, representing the total number of unique elements (k) in nums.
      
**Time Complexity**
  - ✔ O(n) → Since we loop through the array once.
**Space Complexity**
  - ✔ O(1) → Works in-place without extra memory

```
int removeDuplicates(int* nums, int numsSize)
{

int i=0;
for(int j=i+1;j<numsSize;j++)
{
    if(nums[i]!=nums[j])
    {
        nums[i+1]=nums[j];
        i++;
    }
}
return i+1;
}
```
# 80. Remove Duplicates from Sorted Array II #
https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/?envType=study-plan-v2&envId=top-interview-150

Given an integer array nums sorted in non-decreasing order, remove some duplicates in-place such that each unique element appears at most twice. The relative order of the elements should be kept the same.

**Logic**
  - two-pointer approach
    - 1️⃣ Initialize a pointer i = 1 → This pointer will track the last valid position in the modified array.
    - 2️⃣ Iterate using j from index 2, checking if nums[j] is different from nums[i - 1].
    - 3️⃣ If nums[j] is unique (beyond two occurrences), store it at nums[i] and move i forward.
    - 4️⃣ Return i + 1, which represents the total count of valid elements (k)

**Time Complexity**
  - ✔ O(n) → Since we loop through the array once.
**Space Complexity**
  - ✔ O(1) → Works in-place without extra memory

  
```
// Online C compiler to run C program online
#include <stdio.h>

int removeDuplicates(int* nums, int numsSize)
{
    
    if (numsSize <= 2) 
    {
        return numsSize; // If the array has 2 or fewer elements, return as is
    }

    int i = 1; // Pointer to track valid elements
    int j= 2;
    while(j<numsSize) 
    {
        // If the current number is not the same as the number two positions before
        if (nums[j] != nums[i - 1]) {
            i++; // Move the pointer for storing the valid element
            nums[i] = nums[j]; // Store the unique element
        }
        j++;
    }

    return i + 1; // k = number of valid elements
}

int main()
{

//int arr[] = {1,2,3,3,5,5,5};
int arr[] = {5,1};
int n = sizeof(arr)/sizeof(arr[0]);

printf("unsorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
//remove duplicates elemets
int index = removeDuplicates(arr,n);
printf("\nfinal array\n");
for(int i=0;i<index;i++)
{
    printf("%d\t",arr[i]);
}

    return 0;
}
```
# 169. Majority Element #
Given an array nums of size n, return the majority element.
The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.
https://www.youtube.com/watch?v=_xqIp2rj8bo
**Logic Moore's Voting Algorithm**
  - Traverse thorugh the array from 1st element k/as candidte "element" and
  - This algorithm works on the fact that if an element occurs more than N/2 times, it means that the remaining elements other than this would definitely be less than N/2. So let us check the proceeding of the algorithm.
  - First, choose a "candidate" from the given set of array elements if on traversing array[i] it is the same as the candidate element, increase the "votes". Otherwise, decrease the votes if votes become 0, select another new element as the "candidate" element.
  - Intuition Behind Working :
    - When the elements are the same as the candidate element, votes are incremented whereas when some other element is found (not equal to the candidate element), we decreased the count. This actually means that we are decreasing the priority of winning ability of the selected candidate, since we know that if the candidate is in majority it occurs more than N/2 times and the remaining elements are less than N/2. We keep decreasing the votes since we found some different element(s) than the candidate element. When votes become 0, this actually means that there are the equal  number of votes for different elements, which should not be the case for the element to be the majority element. So the candidate element cannot be the majority and hence we choose the present element as the candidate and continue the same till all the elements get finished. The final candidate would be our majority element. We check using the 2nd traversal to see whether its count is greater than N/2. If it is true, we consider it as the majority element.
      
```
int majorityElement(int* nums, int numsSize) {

// Step 1: Find the candidate
    int element/candidate = 0,freq/vote =0;
    for(int i =0;i<numsSize;i++)
    {
        if(freq == 0)
        {
            element = nums[i];
        }
        if(element == nums[i])
        {
            freq++;
        }
        else
        freq--;
    }
//Issue:
//- The algorithm correctly finds a candidate for the majority element using Moore’s Voting Algorithm.
//- However, it does not verify whether the candidate actually appears more than ⌊n/2⌋ times in the array.
//- If the array does not contain a majority element, your function will still return a candidate, which may be incorrect.so step 2 is needed

// Step 2: Verify the candidate has freq > n/2
freq =0;

for(int i =0;i<numsSize;i++)
{
    if(element == nums[i]);
    {
        freq++;
    }
}
if(freq>(numsSize/2))
{
    return element;
}
else
{
    return -1;

}

```

# 189. Rotate Array #

  Given an integer array nums, rotate the array to the **right by k steps**, where k is non-negative.

  - Step 1: Reverse the **last k elements** of the array
  - Step 2: Reverse the **first n-k elements** of the array.
  - Step 3: Reverse the whole array.
  - Time Complexity: O(n) (since 3 * O(n) = O(n)).Since 3 times we are calling "reverse"
  - Space Complexity: O(1).

 ```
void reverse(int nums[],int start,int end)
{
    while(start<end)
    {
        int temp = nums[end];
        nums[end] = nums[start];
        nums[start]= temp;
        start++;
        end--;
    }
}
void rotate(int* nums, int numsSize, int k) {

    //Note : To handle edge cases like when numsSize is leess then k we need to use this
    //reference :time at 11.24 : https://www.youtube.com/watch?v=wvcQg43_V8U&t=61s
    k=k%numsSize;

    reverse(nums,0,numsSize-k-1);
    reverse(nums,numsSize-k,numsSize-1);
    reverse(nums,0,numsSize-1);

}

```
# 121. Best Time to Buy and Sell Stock #

**problem statement :**
  - You are given an array prices where prices[i] is the price of a given stock on the ith day.
  - You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.
  - Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

**logic**
  - Think of it like going to a market every day, and you want to buy something cheap and sell it when the price is highest to make the most money. So, you need to:
    - Find the lowest price to buy.
    - Check each day's price to see if selling gives a better profit than before.
    - Keep updating the best profit you've found so far
    - Time Complexity: O(n)
    - Space Complexity: O(1).
      
**Breaking Down the Code**
  - Step 1: Set up the lowest price and max profit
    ```
      int min = prices[0];  // Assume the first day's price is the lowest for now
      int max = 0;          // Start with 0 profit (we haven't made a sale yet)
     ```
    - min keeps track of the cheapest stock price found so far.
    - max keeps track of the best profit found so far
  - Step 2: Go through each day's price
    ```
      for (int i = 0; i < n; i++) {
     ```
    - Start looking at each day's price one by one.
  - Step 3: If we find a lower price, update "min"
     ```
      if (prices[i] < min) {
    min = prices[i];  // If today's price is lower, update min
      }
     ```
    - If today's stock price is cheaper than the previous minimum, update min because now we have a better buying price.
  - Step 4: If selling today gives a better profit, update max
     ```
      else {
          if (max < (prices[i] - min)) {
            max = prices[i] - min;  // Update max if we get a better profit
            }
      }
     ```
     - If today's price is higher than the lowest price we've seen, check the profit (prices[i] - min).
     - If this profit is better than the previous max, update max
  - Step 5: At the end, return the best profit found
      ```
      return max;
      ```
    - After checking all days, max will hold the highest profit we can make.
    - If no profit is possible (prices just go down), max remains 0, and we return 0

**Key Takeaways**
  - We track the lowest price (min) seen so far.
  - We check each day's price to see if selling makes a bigger profit (max).
  - At the end, max holds the best profit we can make.
  - If prices always go down, max remains 0 (no profit possible)

![image](https://github.com/user-attachments/assets/fb6e4c88-f60d-4fd4-9d5f-0bdb46f9e7d9)

```
    
int maxProfit(int* prices, int n) {
    int min=prices[0]; // Assume the first day's price is the lowest for now
    int max=0;          // Start with 0 profit (we haven't made a sale yet)
    for(int i=0;i<n;i++){
        if(prices[i]<min){
            min=prices[i];
        }
        else{
            if(max<(prices[i]-min)){
                max=prices[i]-min;
            }
        }
    }
    return max;
}
```
# 238. Product of Array Except Self #

**logic**
  - Approach 1: Brute force
    - The given function calculates the product of all elements in an array except the current index using a nested loop approach.
    - The result array is dynamically allocated using malloc().
    - returnSize is set to numsSize.
    - The outer loop iterates through each index i.
    - The inner loop calculates the product of all elements except nums[i].
    - A temporary variable temp stores the cumulative product, skipping the current index.
    - After calculating the product (excluding the current element), store it in result[i].
    - Time Complexity: O(n²) Nested loops lead to slow execution for large arrays


 - Approach 2: Optimal
    - 1️⃣ Allocate Memory for result Array
      - malloc() is used to dynamically allocate memory for storing the output.
      - returnSize is set to numsSize, ensuring the returned array has the same size as nums.
    - 2️⃣ Compute Prefix Products (Left to Right Pass)
      - prefix tracks the cumulative product of elements before index i.
      - Each result[i] stores the product of all previous elements.
    - 3️⃣ Compute Suffix Products (Right to Left Pass)
      - suffix tracks the cumulative product of elements after index i.
      - Multiply result[i] by suffix, completing the product computation.
    - ✅ Final Output:
      - Each index i in result contains the product of all elements except nums[i], efficiently computed in two passes
    - Time Complexity: O(n) → Two separate loops (prefix & suffix).


```
//Approach 1 Brute force : this will time out for large arrays
Time complexity: O($n^2$)

int* productExceptSelf(int* nums, int numsSize, int* returnSize) {
    int* result =(int*)malloc(numsSize*sizeof(int));
    *returnSize = numsSize;
    for(int i=0;i<numsSize;i++)
    {
        int temp =1;
        for(int j=0;j<numsSize;j++)
        {
            if(i!=j)
            {
                temp = temp * nums[j];
            }
        }
        result[i]= temp;
    }
    return result;
}
```
```
//Approach 2: Optimal
Iime Complexity: O(n)
/**
 * Note: The returned array must be malloced, assume caller calls free().
 reference : https://www.youtube.com/watch?v=TW2m8m_FNJE
 */
int* productExceptSelf(int* nums, int numsSize, int* returnSize) {
    int* result =(int*)malloc(numsSize*sizeof(int));
    *returnSize = numsSize;

    int prefix=1,suffix = 1;
    //prefix calculation
    for(int i=0;i<numsSize;i++)
    {
        result[i]= prefix;
        prefix = prefix * nums[i];
    }
    //suffix calculation
    for(int i=numsSize-1;i>=0;i--)
    {
        result[i]= result[i] * suffix;
        suffix = suffix * nums[i];
    }
    return result;

```





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



