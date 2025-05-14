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
**- Using Two Pointers approach(i and j)**
    - i tracks the position where the next unique element should be stored.
    - j iterates through the array to find elements different from the last stored unique value (nums[i]).
  - When a Unique Element is Found
    - If nums[j] is not a duplicate (nums[i] != nums[j]), copy nums[j] to nums[i + 1] (next available spot).
    - Move i forward to reflect the new unique element count.
  -  Return the Count of Unique Elements
    - i + 1 is returned, representing the total number of unique elements (k) in nums.
      
**Time Complexity**
✔ O(n) → Since we loop through the array once.
Space Complexity
✔ O(1) → Works in-place without extra memory



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



