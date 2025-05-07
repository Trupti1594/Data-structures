# Count digits in a number #
**logic**

TThe modulus operator % computes the remainder when a number is divided by another number. When we perform N % 10 we get the last digit of the number N.

Eg. N = 7789, then N%10 results in 9 which is the last digit.

After extracting the last digit we need to remove the last digit as well which can be done via division operator.

Eg. N = 7789 then N/10 results in 778, removing the last digit.

Together with these operators we can effectively extract digits from right to left by repeatedly taking the last digit using % and then removing it using / until the number has been broken down into individual digits and only 0 is left.

![image](https://github.com/user-attachments/assets/4913c9da-93f4-42e9-b997-670ef7c93373)

**Algorithm**

Step 1:Initialise an empty vector ans to store the extracted digits.

Step 2: While N is greater than 0, execute the following:
  - Get the last digit of the N by taking N%10 and store it in a variable lastDigit.
  - Add lastDigit to the ans vector.
  - Update N by removing its last digit by performing a modulo 10 (%10) operation on it.

Step 3: Reverse the vector ans as the digits have been added from right to left and we need to return them in the order left to right.

Step 4: Return the ans vector.

```
#include <stdio.h>

int main() {
int n;
int rem;
int count =0;
printf("enter the value \n");
scanf("%d",&n);
while(n!=0)
{
rem = n%10; //extracting the digit
count++; //counting the no. of digit and increment by 1 in each run
n=n/10; //
}
printf("count = %d",count);
    return 0;
}

```

**Time Complexity:** whenever no. of iteration depends on division then we can see logarithmic time complexity at that time O(log10N + 1)

# reverse the number #

**Algorithm**

![image](https://github.com/user-attachments/assets/4b7cf45d-2a0f-40b1-86cd-b9f5ce68bb5d)

Step 1:Initialise an integer revNum to 0. This variable will store the reversed number.

Step 2: Using a while loop we iterate while n is greater than 0 and at each iteration:
  - Calculate the last digit of the number using the modulus operator (N%10) and store it in a variable last digit.
  - Update the reversed number by multiplying it with 10 and adding the last digit. This effectively appends the last digit to the end of the reversed number.
  - Remove the last digit of the number by dividing it by 10.
    
Step 3: After exiting the while loop, return the reversed number.

```
#include <stdio.h>

int main() {
int n;
int lastdigit,reverse = 0;
int count =0;
printf("enter the value \n");
scanf("%d",&n);
while(n!=0)
{
lastdigit = n%10; //extracting the digit
reverse = (reverse *10) +lastdigit;
count++; //counting the no. of digit and increment by 1 in each run
n=n/10; //
}
printf("reverse = %d",reverse);
    return 0;
}
```
# Check if a number is Palindrome or Not #

- A palindrome is a number that reads the same backward as forward. For example, 121, 1331, and 4554 are palindromes because they remain the same when their digits are reversed.
  
**Algorithm**

Step 1:Initialise an integer revNum to 0. This variable will store the reverse of the number.

Step 2: Make a duplicate of the original number and store it in an integer dup for later comparison.

Step 3: Run a while loop with the condition n>0 to reverse the number and at each iteration:
 - Get the last digit of n by using the modulus operator % with 10 and store it in a temporary variable ld.
 - Update the revNum by multiplying it by 10 and adding the last digit ld.
 - Update n by integer division with 10 effectively removing the last digit.
   
Step 4: After the loop, check if the original number dup is equal to the reversed number revNum.
 - If they are equal, return true indicating the number is a palindrome.
 - If they are not equal, return false indicating that the number is not a palindrome.

```
int main() {
int n;
int lastdigit,reverse = 0;
int nbackup;
printf("enter the value \n");
scanf("%d",&n);
nbackup = n;
while(n!=0)
{
lastdigit = n%10; //extracting the digit
reverse = (reverse *10) +lastdigit;
n=n/10; //
}
printf("reverse = %d : number = %d\n",reverse,nbackup);
if (reverse == nbackup)
{
    printf("no. is pallindrome \n");
}
else
{
    printf("no. is not pallindrome \n");
}
    return 0;
}
```
