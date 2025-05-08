Reference : https://takeuforward.org/strivers-a2z-dsa-course/strivers-a2z-dsa-course-sheet-2/

# BasicMaths #

# 1) Count digits in a number #

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

# 2) reverse the number #

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
# 3) Check if a number is Palindrome or Not #

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

**Time Complexity:** O(log10N + 1) where N is the input number. The time complexity is determined by the number of digits in the input integer N. In the worst case when N is a multiple of 10 the number of digits in N is log10 N + 1.

In the while loop we divide N by 10 until it becomes 0 which takes log10N iterations.
In each iteration of the while loop we perform constant time operations like modulus and division and pushing elements into the vector.
Space Complexity: O(1) as only a constant amount of additional memory for the reversed number regardless of size of the input number.

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

# 4) Armstrong Number or not #

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
    
**Time Complexity:** O(log10N + 1) where N is the input number. The time complexity is determined by the number of digits in the input integer N. In the worst case when N is a multiple of 10 the number of digits in N is log10 N + 1.

In the while loop we divide N by 10 until it becomes 0 which takes log10N iterations.
In each iteration of the while loop we perform constant time operations like modulus and division and pushing elements into the vector.
Space Complexity: O(1) as only a constant amount of additional memory for the reversed number regardless of size of the input number.

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

# 5) Print all Divisors of a given Number #

- A divisor of an integer N is a positive integer that divides N without leaving a remainder. In other words, if N is divisible by another integer without any remainder, then that integer is considered a divisor of N.

**Brute force approach**
A brute force approach would be to iterate from 1 to n checking each value if it divides n without leaving a remainder. For each divisor found, store it in an array and a count of divisors is maintained. After iterating through all possible values, the size of the array is updated with the count of divisors and the array is returned.

  - **Algorithm:**

    Step 1:Initialise an array to store the divisors.

    Step 2:Iterate from 1 to n using a loop variable ‘i’. For each value of ‘i’:

      - Check if ‘i’ is a divisor of ‘n’ by checking if ‘n’ is divisible by ‘i’ without a     remainder (‘n’%i == 0).
      - If i is a divisor, store it in the array of divisors and increment the count of divisors.
    
    Step 3:After the loop, return the array of divisors.

  - **Time Complexity:** O(N) where N is the input number. The algorithm iterates through each number from 1 to n once to check if it is a divisor.

```
int main() {
int i;
int n;
printf("enter the value \n");
scanf("%d",&n);
for(i =1;**i<=n**;i++)
{
 if(n%i == 0)
 {
    printf("%d\n",i);
 }
}
    return 0;
}

```

**Optimal approach**

![image](https://github.com/user-attachments/assets/a63a9b05-e535-4720-afd4-1fd7a3f1f2d2)

![image](https://github.com/user-attachments/assets/2e7e6dee-2291-494a-a72d-5184059cd6be)

  - We can optimise the previous approach by using the property that for any non-negative integer n, if d is a divisor of n then n/d is also a divisor of n.

  - This property is symmetric about the square root of n by traversing just the first half we can avoid redundant iteration and computations improving the efficiency of the algorithm.

  - But this approach prints aaray in unsorted order. Sorting algo needs to be applied
  - **Time Complexity(without sorting algo)** - O(sqrt(n))

```
#include <stdio.h>
#include <math.h>
int main() {
int i;
int n;
printf("enter the value \n");
scanf("%d",&n);
for(i =1;**i*i<=n**;i++)  **//i*i<=n shows squareroot(36) ie 6 <= n**
{
 if(n%i == 0)
 {
    printf("%d\t",i);
 }
 if((n/i)!=i)
 {
     printf("%d\t",n/i);
 }
}
    return 0;
}

```

# 6) Check if a number is prime or not #

  - A prime number is a number that exactly has 2 factors i.e 1 and itself.

We can iterate through numbers from 1 to n, counting how many of these numbers divide n without a remainder. If exactly two numbers do, so n is prime otherwise it is not prime.

**Algorithm:(brut force)**

Step 1:Initialise a variable cnt to count the number of factors and set it to 0.

Step 2:Start a loop from 1 to n, iterating through each number i. Inside the loop:

  - Check if n is divisible by i without any remainder.
  - If it is, increment the counter variable by 1.
    
Step 3:After the loop if the number of divisors is equal to 2, return true indicating the number is prime.

If the number of divisors is not equal to 2 (but greater), return false indicating that the number is not prime.

**Time Complexity:** O(N) where N is the input number as we iterate from 1 to N performing constant-time operation for each iteration.

Space Complexity : O(1) as the space used by the algorithm does not increase with the size of the input.

```
#include <stdio.h>
#include <math.h>
int main() {
int i;
int n;
int count =0;
printf("enter the value \n");
scanf("%d",&n);
for(i =1;i<=n;i++)  //i*i<=n shows squareroot(36) ie 6 <= n
{
 if(n%i == 0)
 {
    count++;
 }
}
if(count == 2)
printf("number is prime");
else
printf("number is not prime");
    return 0;
}

```

**Algorithm:(optimized force)**

We can optimise the algorithm by only iterating up to the square root of n when checking for factors. This is because if n has a factor greater than its square root, it must also have a factor smaller than its square root.

This property is symmetric about the square root of n by traversing just the first half we can avoid redundant iteration and computations improving the efficiency of the algorithm. Discusses in detail here:Print All Divisiors

Step 1: Initialise a counter variable cnt to count the number of factors to 0.

Step 2: Begin a loop from 1 to the square root of n. This loop iterates through possible factors of n. For each value of i within the loop:

  - Check if n is divisible by i without any remainder.
  - If n is divisible by i, it means i is a factor of n, so increment the counter variable cnt by 1.
  - Check if the reciprocal factor of i ie. n/i is not equal to i. If they are not equal, it means there is a distinct factor so increment cnt by 1 again.
    
Step 3: After the loop, cnt will contain the total numbers of factors of n.

Step 4: Check if the value of cnt is exactly 2, it means that n has exactly two distinct factors (1 and itself), indicating that it is a prime number.

If the the number of factors is greater than 2 then it is a composite number, return false.

**Time Complexity:** O(sqrt(N))where N is the input number. The loop iterates up to the square root of n performing constant time operations at each step.

Space Complexity : O(1) as the space complexity remains constant and independent of the input size. Only a fixed amount of memory is required to store the integer variables.

```
int main() {
int i;
int n;
int count =0;
printf("enter the value \n");
scanf("%d",&n);
for(i =1;i*i<=n;i++)  //i*i<=n shows squareroot(36) ie 6 <= n
{
 if(n%i == 0)
 {
    count++;
    if((n/i)!=i)
    {
        count++;
    }
 }
}
printf("count = %d\n",count);
if(count == 2)
printf("number is prime");
else
printf("number is not prime");
    return 0;
}

```

# Recursion #
  - when a funtion calls itself until a specific condition is met

# Print Name N times using Recursion #

**Algorithm**

Since in this problem, there is no count that can be incremented each time we call a function, how can we keep a track of how many times we have printed the name?

For this problem, we’re going to be using a function along with parameters in which we can keep track of the number of times we’ve printed something.

we first call the function when the value of i is 1 and then print the name and increment i by 1 inside the parameter of the function and make a call again. But, we know that this will go on forever as i will be increasing continuously after every function call. So, to avoid this we put a base condition that if i exceeds n, then simply terminate the current recursive call and return to the previous call.

![image](https://github.com/user-attachments/assets/ea901a9a-eedf-4b86-bd7a-5a0d465f515a)

**Time Complexity:** O(N) { Since the function is being called n times, and for each function, we have only one printable line that takes O(1) time, so the cumulative time complexity would be O(N) }

Space Complexity: O(N) { In the worst case, the recursion stack space would be full with all the function calls waiting to get completed and that would make it an O(N) recursion stack space }

```
void print_name(int n,int i)
{
    if(i > n)
    {
        return;
    }
    printf("trupti\n");
    print_name(n,i+1);
}

int main() {

int n;
int i =1;
printf("enter the value \n");
scanf("%d",&n);
print_name(n,i);
    return 0;
}

```

# Print 1 to N using Recursion #

**Algorithm**

For this problem, we’re going to be using a function along with parameters that get incremented with each function call through which we can keep track of the integer count while printing.

we first call the function when the value of i is 1 and then print the value of i and increment i by 1 inside the parameter of the function and make a call again. But, we know that this will go on forever as i will be increasing continuously after every function call. So, to avoid this we put a base condition that if i exceeds n, then simply terminate the current recursive call and return to the previous call.

In this way, all the integers from 1 to N would get printed and as soon as we exceed the count of printing by n, the function terminates

```
void print_name(int i,int n)
{
    if(i > n)
    {
        return;
    }
    printf("%d\n",i);
    print_name(i+1,n);
}

int main() {

int n;
int i =1;
printf("enter the value \n");
scanf("%d",&n);
print_name(i,n);
return 0;
}

```

# Print N to 1 using Recursion #

**Algorithm**

For this problem, we’re going to be using a function along with parameters that get decremented with each function call through which we can keep track of the integer count while printing.

We can clearly see in this pseudocode that we first call the function when the value of i is n and then print the value of i and decrement i by 1 inside the parameter of the function and make a call again. But, we know that this will go on forever as i will be decreasing continuously after every function call. So, to avoid this we put a base condition that if i is less than 1, then simply terminate the current recursive call and return to the previous call.

In this way, all the integers from N to 1 would get printed and as soon as the count becomes less than 1, the function terminates

```
void print_name(int i,int n)
{
    if(n < i)
    {
        return;
    }
    printf("%d\n",n);
    print_name(i,n - 1);
}

int main() {

int n;
int i =1;
printf("enter the value \n");
scanf("%d",&n);
print_name(i,n);
return 0;
}

```

```
**This will work for both if N is -ve and +ve**
void print_name(int i,int n)
{
    if(n>=0)
    {
        if(n <= i)
        {
            return;
        }
        printf("%d\n",n);
        print_name(i,n - 1);
    }
    else
    {
        if(n == 0)
        {
            return;
        }
        printf("%d\n",n);
        print_name(i,n + 1);
    }
}

int main() {

int n;
int i =0;
printf("enter the value \n");
scanf("%d",&n);
print_name(i,n);
return 0;
}
```
