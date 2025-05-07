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

# Armstrong Number or not #

**logic**

To check if a number is an armstrong number, we can use the algorithm created in Extract Digits.

An Armstrong number, also known as a narcissistic number or plenary number, is a number that is equal to the sum of its own digits each raised to the power of the number of digits.

Number of digits: 3, 153 = 13+53+33

We extract the digits of the number, raise each digit to the power of the total number of digits in the number. Sum up all the results obtained and check if the sum equals to the original number.

**Algorithm**

Step 1:Calculate the number of digits in the input number and store it in k. Read more about this Approach here: Count Digits

Step 2: Initialise a variable sum to 0. This variable will store the sum of each digit raised to the power of number of digits in number.

  - Make a copy of the original number to store it in a temporary variable.
Step 3: Run a while loop with the condition n>0 and at each iteration:

  - Get the last digit of n by using the modulus operator % with 10 and store it in a temporary variable ld.
  - Add the digit ld raised to the power of k of the sum.
  - Update n by integer division with 10 effectively removing the last digit.
    
Step 4: After the loop, check if the original input number is equal to the sum of the digits raised to the power of the number of digits in the number.

  - If they are equal, return true indicating the number is an Armstrong number.
  - If they are not equal, return false indicating that the number is not an Armstrong number.

```
int main()
{
int n;
int num;
int old =0;
printf("enter the value \n");
scanf("%d",&n);
int nbackup = n;
while(n!=0)
{
 num = n%10; //extracting the digit
old = (num*num*num) +old;
n=n/10; //
}
printf("nbackup = %d : finalnumber = %d\n",nbackup,old);
if (old == nbackup)
{
    printf("no. is armstrong \n");
}
else
{
    printf("no. is not armstrong \n");
}
    return 0;
}

```

# Print all Divisors of a given Number #

- A divisor of an integer N is a positive integer that divides N without leaving a remainder. In other words, if N is divisible by another integer without any remainder, then that integer is considered a divisor of N.

**brute force approach**
A brute force approach would be to iterate from 1 to n checking each value if it divides n without leaving a remainder. For each divisor found, store it in an array and a count of divisors is maintained. After iterating through all possible values, the size of the array is updated with the count of divisors and the array is returned.

  **Algorithm:**

  Step 1:Initialise an array to store the divisors.

  Step 2:Iterate from 1 to n using a loop variable ‘i’. For each value of ‘i’:

    - Check if ‘i’ is a divisor of ‘n’ by checking if ‘n’ is divisible by ‘i’ without a     remainder (‘n’%i == 0).
    - If i is a divisor, store it in the array of divisors and increment the count of divisors.
    
Step 3:After the loop, return the array of divisors.

**Time Complexity:** O(N) where N is the input number. The algorithm iterates through each number from 1 to n once to check if it is a divisor.
