- [Count_digits_in_a_number](#Count_digits_in_a_number)
- [Reverse_the_number](#Reverse_the_number)
- [Check_if_a_number_is_Palindrome_or_Not](#Check_if_a_number_is_Palindrome_or_Not)
- [Armstrong_Number_or_not](#Armstrong_Number_or_not)
- [Print_all_Divisors_of_a_given_Number](#Print_all_Divisors_of_a_given_Number)
- [Check_if_a_number_is_prime_or_not](#Check_if_a_number_is_prime_or_not)
- [Print_Name_N_times_using_Recursion](#Print_Name_N_times_using_Recursion)
- [Print_1_to_N_using_Recursion](#Print_1_to_N_using_Recursion)
- [Print_N_to_1_using_Recursion](#Print_N_to_1_using_Recursion)
- [Sum_of_first_N_Natural_Numbers](#Sum_of_first_N_Natural_Numbers)
- [Factorial_of_a_Number_using_Recursive](#Factorial_of_a_Number_using_Recursive)
- [Reverse_a_given_Array](#Reverse_a_given_Array)
- [using_recursion_Check_if_the_given_String_is_Palindrome_or_not](#using_recursion_Check_if_the_given_String_is_Palindrome_or_not)
- [Print_Fibonacci_Series_up_to_Nth_term_without_recursion](#Print_Fibonacci_Series_up_to_Nth_term_without_recursion)
- [Print_Fibonacci_Series_up_to_Nth_term_with_recursion](#Print_Fibonacci_Series_up_to_Nth_term_with_recursion)
- [Selection_sort](#Selection_sort)
- [Bubble_sort](#Bubble_sort)
- [Insertion_sort](#Insertion_sort)
- [Merge_sort](#Merge_sort)
- [Quick_sort](#Quick_sort)
- [Find_the_Largest_element_in_an_array](#Find_the_Largest_element_in_an_array)
- [Find_the_2nd_Largest_element_in_an_array](#Find_the_2nd_Largest_element_in_an_array)
- [Check_if_an_Array_is_Sorted](#Check_if_an_Array_is_Sorted)
- [Remove_Duplicates_in_place_from_Sorted_Array](#Remove_Duplicates_in_place_from_Sorted_Array)
- [Left_Rotate_the_Array_by_One](#Left_Rotate_the_Array_by_One)
- [Rotate_array_by_K_elements](#Rotate_array_by_K_elements)
- [Reverse_linked_list](#Reverse_linked_list)
- [Implementation_of_stack_using_array](#Implementation_of_stack_using_array)
- [Implementation_of_stack_using_linked_list](#Implementation_of_stack_using_linked_list)
- [Implementation_of_stack_using_queue](#Implementation_of_stack_using_queue)
- [find_and_Remove_duplicates_from_string](#find_and_Remove_duplicates_from_string)
- [sort_array_of_strings_using_quick_sort](#sort_array_of_strings_using_quick_sort)
- [insert_element_in_singlle_ll_front_position_end](#insert_element_in_singlle_ll_front_position_end)
- [Delete_element_in_single_ll_front_position_end](#Delete_element_in_single_ll_front_position_end)
- [Implement_stack_using_array](#Implement_stack_using_array)
- [Implement_stack_using_linked_list](#Implement_stack_using_linked_list)





Reference : https://takeuforward.org/strivers-a2z-dsa-course/strivers-a2z-dsa-course-sheet-2/


# BasicMaths #

# Count_digits_in_a_number #

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

# Reverse_the_number #

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
# Check_if_a_number_is_Palindrome_or_Not #

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

# Armstrong_Number_or_not #

**logic**

To check if a number is an armstrong number, we can use the algorithm created in Extract Digits.

An Armstrong number, also known as a narcissistic number or plenary number, is a number that is equal to the sum of its own digits each raised to the power of the number of digits.

Number of digits: 3, 153 = $1^3$ + $5^3$ + $3^3$

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

# 5) Print_all_Divisors_of_a_given_Number #

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
    if((n/i)!=i)
    {
     printf("%d\t",n/i);
    }
 }
}
    return 0;
}

```

# 6) Check_if_a_number_is_prime_or_not #

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

# Print_Name_N_times_using_Recursion #

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

# Print_1_to_N_using_Recursion #

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

# Print_N_to_1_using_Recursion #

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
**Below will work for both if N is -ve and +ve**

```

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

# Sum_of_first_N_Natural_Numbers #

**1) Algorithm using recursion but printing in recursion function and recursive function not returning sum**

In this approach, instead of using a global variable for calculating the sum, we pass the sum in the parameters of the function each time we add an integer to it during the function call. The sum gets incremented by an ith integer and i get decremented by 1 in each function call. At the end when i becomes less than 1, we simply return the calculated sum until that point.

we first call the function when the value of sum is 0 and then we increment the value of sum by i (initially i is n) and decrement i by 1 inside the parameter of the function and make a call again. But, we know that this will go on forever as i will be decreasing continuously after every function call. So, to avoid this we put a base condition that if i is less than 1, then simply terminate the current recursive call and return the calculated sum.

![image](https://github.com/user-attachments/assets/b4de73a7-6fb2-4054-a625-a4f773d945ea)

```
**void** print_sum(int sum,int i)
{
        if(i < 1)
        {
            **printf("%d\n",sum);**
            return;
        }
        print_sum(sum+i,i - 1);
        
}

int main() {

int n;
int sum =0;
printf("enter the value \n");
scanf("%d",&n);
print_sum(sum,n);
return 0;
}

```

**2) Algorithm using recursion but recursive function returning sum**

This approach is a lot simpler than the parameterized recursion. We can visualize the sum of n natural numbers in the following way as shown below:

  - **sumOfNaturalNumbers(N) = N + sumOfNaturalNumbers(N-1);**

The Sum of N natural numbers would just be the Nth integer added to the Sum of (N-1) natural numbers. The base case can be visualized as if n decreases to 0, then we return 0 because the sum of 0 natural numbers is 0 only. Here, we’ve just broken the problem into 2 subparts and the answers of both these subparts would be added and stored in the Sum(n) function which would then be printed at last.

![image](https://github.com/user-attachments/assets/e5e16c62-3538-4d68-969e-48b5c258d7ec)

```
**int** print_sum(int n)
{
        if(n < 1)
        {
            return 0;
        }
        return(n+print_sum(n-1));
}

int main() {

int n;
printf("enter the value \n");
scanf("%d",&n);
int sum = print_sum(n);
**printf("sum = %d",sum);**
return 0;
}

```
**3) Algorithm using formula**

We can use the formula for the sum of N numbers, i.e N(N+1)/2.
  - Take a variable sum.
  - Initialize it with N(N+1)/2, where N is a given number.
  - Time Complexity: O(1)
  - Space Complexity: O(1)


# Factorial_of_a_Number_using_Recursive #

**Algorithm**

The Factorial of a number N can be calculated by multiplying all the natural numbers till the number N. Through this approach, we can visualize the factorial of n natural numbers in the following way as shown below:

factorial(N) = N * factorial(N-1);

The Factorial of N natural numbers is the Nth integer multiplied by the Factorial of (N-1) natural numbers. The base case can be visualized as if n decreases to 0, then we return 1 because the factorial of 0 is 1 only. Here, we’ve just broken the problem into 2 subparts and the answers of both would be multiplied together and stored in the factorial(n) function which would then be printed at last.

**Time Complexity:** O(N) { Since the function is being called n times, and for each function, we have only one printable line that takes O(1) time, so the cumulative time complexity would be O(N) }

Space Complexity: O(N) { In the worst case, the recursion stack space would be full with all the function calls waiting to get completed and that would make it an O(N) recursion stack space }
![image](https://github.com/user-attachments/assets/6c90390a-7f35-4d65-aef8-99c117a161ad)

```
int print_factorial(int n)
{
        if(n == 1)
        {
            return 1;
        }
        return(n * print_factorial(n - 1));
}

int main() {

int n;
printf("enter the value \n");
scanf("%d",&n);
int factorial = print_factorial(n);
printf("factorial = %d\n",factorial);
return 0;
}

```

# Reverse_a_given_Array #
  - methods
    - using recursion
    - using 2 pointers
    - using one extra array
      
 **Array basics**
 
   - its ok to write array as int arr[] = {1,2,3,4,5,6}; instead of int arr[10] = {1,2,3,4,5,6};
   - while passing array as an function argument pass it like reverse(arr); not like reverse(arr[]) because In C, array arguments are passed by reference, and the array name decays into a pointer to the first element.
   - In function defination array should be collected as reverse(int arr[]) not as reverse(int arr) becuase reverse(int arr[]) is actually treated as reverse(int *arr) internally.The arr name itself represents the memory address of the first element, so specifying arr[] in a function call is unnecessary.But in function calls, C only requires the array name (which acts as a pointer), so arr[] becomes invalid syntax.

**alogorithm using recursion**

  - Create a function that takes an array, ,temp,start index, and end index of the array as parameters.
Swap the elements present  at the start and end index
  - The portion of the array left to be reversed is arr[start+1,end-1]. Make a recursive call to reverse the rest of the array. While calling recursion pass start +1  and ends - 1 as parameters for the shrunk array. Repeat step 2.
  - Continue recursion as long as the ‘start < end’ condition is satisfied. This is the base case for our recursion.
```
void reverse(int arr[],int temp,int start,int end)
{
    if(start>=end)
    {
        return;
    }
    temp = arr[end];
    arr[end] = arr[start];
    arr[start] = temp;
    reverse(arr,temp,start+1,end-1);
}

int main() {

int n;
printf("enter the no. of elemets in an array \n");
scanf("%d",&n);
int arr[n]; //this will work for c99 and above compiler but for others it may give error
printf("enter the array elements\n");
for(int i = 0;i<n;i++)
{
    scanf("%d",&arr[i]);
    
}
printf("\noriginal aray\n");
for(int i = 0;i<n;i++)
{
    printf("%d\t",arr[i]);
    
}
int temp,start =0;
int end = sizeof(arr)/sizeof(arr[0]); //to calculate no. of element
reverse(arr,temp,start,end -1);
printf("\nreverse aray\n");
for(int i = 0;i<end;i++)
{
    printf("%d\t",arr[i]);
    
}
return 0;
}
```

# using_recursion_Check_if_the_given_String_is_Palindrome_or_not #

**Algorithm**

  - In this approach, we check the string using functional recursion where firstly, the letters on the two ends of the string (start, end) are compared to see if they’re the same or not.
  - If they’re the same then we simply call recursion for the next elements (start+1, end-1) and so on until the start becomes greater than or equal to the end. 
  - If at any point the start and the end differ, we return false stating that the string is not a palindrome.
  - Otherwise, if the base condition is reached, then the string is obviously a palindrome and we return true.

**Time Complexity:** O(N) { Precisely, O(N/2) as we compare the elements N/2 times and swap them}.

Space Complexity: O(1) { The elements of the given array are swapped in place so no extra space is required}.

```
#include <stdio.h>
#include <stdbool.h>

bool pallin(char arr[],int end,int start)
{
    if(start>=end)
    {
        return 1;
    }
    if(arr[start] != arr[end])
    {
        return 0;
    }
    return pallin(arr,end-1,start+1);
}


int main() 
{

char arr[] = "madame";
int temp,start =0;
int end = sizeof(arr)/sizeof(arr[0]); //to calculate no. of element
printf("%s\n",arr);
bool val = pallin(arr,end-2,start);
if(val == 0)
{
    printf("string not pallindrome\n");
}
else
    printf("string pallindrome\n");
return 0;
}

```

# Print_Fibonacci_Series_up_to_Nth_term_without_recursion #

**Algorithm**

For calculating the ith term we only need the last and second last term i.e (i-1)th and (i-2)th term, so Take two variables last and secondLast for storing (i-1)th and (i-2)th term.
Now iterate from 2 to n and calculate the ith term. ith term is last + secondLast term.
Then update secondLast term to the last term and the last term to ith term as we iterate.

**Time Complexity:** O(N).As we are iterating over just one for a loop.

Space Complexity: O(1).

```
int main() 
{
int n,cur;
printf("enter the number\n");
scanf("%d",&n);
int last =0;
int secondlast = 1;
printf("%d\t %d\t",last,secondlast);
for(int i =2;i<n;i++)
{
    cur=secondlast+last;
    printf("%d\t",cur);
    last =secondlast;
    secondlast = cur;
}

return 0;
}
```

# Print_Fibonacci_Series_up_to_Nth_term_with_recursion #

**Time Complexity**: O($2^N$) { This problem involves two function calls for each iteration which further expands to 4 function calls and so on which makes worst-case time complexity to be exponential in nature }.

Space Complexity: O(N) { At maximum there could be N function calls waiting in the recursion stack since we need to calculate the Nth Fibonacci number for which we also need to calculate (N-1) Fibonacci numbers before it }.

**example**
  - Let's take n = 6 as our example value and walk through the memoized recursive Fibonacci function step by step.
  - Step-by-Step Execution for fibonacci(6, memo)
    - Initialization : We create an array memo[n]
    - Recursive Flow
      - 1️⃣ Call fibonacci(6, memo)
          - memo[6] == -1, so we compute fibonacci(5, memo) + fibonacci(4, memo)

      -  2️⃣ Call fibonacci(5, memo)
          - memo[5] == -1, compute fibonacci(4, memo) + fibonacci(3, memo)

      - 3️⃣ Call fibonacci(4, memo)
          - memo[4] == -1, compute fibonacci(3, memo) + fibonacci(2, memo)

      - 4️⃣ Call fibonacci(3, memo)
          - memo[3] == -1, compute fibonacci(2, memo) + fibonacci(1, memo)

      - 5️⃣ Call fibonacci(2, memo)
          - memo[2] == -1, compute fibonacci(1, memo) + fibonacci(0, memo)

      -  6️⃣ Base Cases Reached
        - fibonacci(1) = 1 ✅ (Base case)
        - fibonacci(0) = 0 ✅ (Base case)


    - Memoization Storage
      -  Now, we compute backwards while storing results:
          - memo[2] = fibonacci(1) + fibonacci(0) = 1 + 0 = 1
          - memo[3] = fibonacci(2) + fibonacci(1) = 1 + 1 = 2
          - memo[4] = fibonacci(3) + fibonacci(2) = 2 + 1 = 3
          - memo[5] = fibonacci(4) + fibonacci(3) = 3 + 2 = 5
          - memo[6] = fibonacci(5) + fibonacci(4) = 5 + 3 = 8


  -  🚀 Final Memoization Table
    -  After execution, memo[] contains:
      -  memo = {0, 1, 1, 2, 3, 5, 8}


```
int fibo(int n,int arr[])
{
    if(n<=1)
    {
        arr[n] =n;
        return n;
    }
    arr[n] = fibo(n-1,arr)+fibo(n-2,arr);
    return arr[n];
}


int main() 
{
int n;
printf("enter the number of fibonachi terms\n");
scanf("%d",&n);
int arr[n];
fibo(n,arr);

printf("fibonachi series for %d terms is\n",n);
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
return 0;
}

```
# Selection_sort #
  - Select the minimum value in array and swap that min value with the elemnet present at ith index.keep on repeating this till i<n-1(because in n-2 iteration your array is already sorted  )
    
Selection Sort is a simple sorting algorithm that repeatedly **finds the minimum element from the  array and swaps it with the first element of the unsorted section. sorted array is in ascending order**. It works by dividing the array into two parts: the sorted portion and the unsorted portion.

**How Selection Sort Works:**
  - First, we will select the range of the unsorted array using a loop (say i) that indicates the starting index of the range.The loop will run forward from 0 to n-1. The value i = 0 means the range is from 0 to n-1, and similarly, i = 1 means the range is from 1 to n-1, and so on.
(Initially, the range will be the whole array starting from the first index.)
  - Now, in each iteration, we will select the minimum element from the range of the unsorted array using an inner loop.
  - After that, we will swap the minimum element with the first element of the selected range(in step 1). 
  - Finally, after each iteration, we will find that the array is sorted up to the first index of the range. 
  - Note: Here, after each iteration, the array becomes sorted up to the first index of the range. That is why the starting index of the range increases by 1 after each iteration. This increment is achieved by the outer loop and the starting index is represented by variable i in the following code. And the inner loop(i.e. j) helps to find the minimum element of the range [i…..n-1].

**Dry run:**

  - The following dry run will clarify the concepts:

  - Assume the given array is: {7, 5, 9, 2, 8}

  - Outer loop iteration 1:
    - The range will be the whole array starting from the 1st index as this is the first iteration. The minimum element of this range is 2(found using the inner loop).
    - ![image](https://github.com/user-attachments/assets/6bede632-f49b-4782-b9d5-b379f26230be)

  - Outer loop iteration 2:
    -  The range will be from the [2nd index to the last index] as the array is sorted up to the first index. The minimum element of this range is 5(found using the inner loop).
    -  ![image](https://github.com/user-attachments/assets/6811bdfa-125f-42d2-9a22-3aae2ad2b0b5)

  - Outer loop iteration 3:
    - The range will be from the [3rd index to the last index]. The minimum element of this range is 7(found using the inner loop).
    - ![image](https://github.com/user-attachments/assets/004d2180-05da-4be0-bdfb-c18c14359f32)

  - Outer loop iteration 4:
    - The range will be from the [4th index to the last index]. The minimum element of this range is 8(found using the inner loop).
    - ![image](https://github.com/user-attachments/assets/8916ef4b-4ab4-4381-8dd3-e8768f0ba419)

  - So, after 4 iterations(i.e. n-1 iterations where n = size of the array), the given array is sorted.


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
      
**Time complexity:O($n^2$)**, (where N = size of the array), for the best, worst, and average cases.
Reason: If we carefully observe, we can notice that the outer loop, say i, is running from 0 to n-2 i.e. n-1 times, and for each i, the inner loop j runs from i to n-1. For, i = 0, the inner loop runs n-1 times, for i = 1, the inner loop runs n-2 times, and so on. So, the total steps will be approximately the following: (n-1) + (n-2) + (n-3) + ……..+ 3 + 2 + 1. The summation is approximately the sum of the first n natural numbers i.e. (n*(n+1))/2. The precise time complexity will be O(n2/2 + n/2). Previously, we have learned that we can ignore the lower values as well as the constant coefficients. So, the time complexity is O(n2). Here the value of n is N i.e. the size of the array.

**Space Complexity: O(1)**

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
# Bubble_sort #

- Push maximum value to the last by adjacent swaps.
  
Bubble Sort is a simple sorting algorithm that **repeatedly swaps adjacent elements if they are in the wrong order. It gradually moves the largest element to the end in each pass**, just like bubbles rising to the surface.

**How Bubble Sort Works:**
  - Compare adjacent elements.
  - Swap if the first is greater than the second.
  - Repeat for all elements.
  - Largest element moves to the end after one full pass.
  - Continue until the array is fully sorted.
  - If given array is already sorted, then their will be no swapping in the 1st iteration of i itself and swap variable will be 0(as swap =1 only during swaping) so i loop willbe broken and for this time conplexity is O(n)

**Step-by-Step Breakdown of Your Code**
  - Let's go through the code with explanations for each part:
      1) ``` for(int i=0; i<n-1; i++) //pass through the array multiple times ```
        - This loop runs n-1 times because we need multiple passes to sort the entire array.
Each pass ensures that the largest unsorted element moves to its correct position.
      2) ```for(int j=0; j<n-1-i; j++) //compare adjacent elements```
        - This loop runs n-1-i times because after each pass, the last i elements are already sorted.It compares two adjacent elements (arr[j] and arr[j+1]).
      3)  Swap if elements are in the wrong order
         
    ```    
         if(arr[j] > arr[j+1])
         {
           int temp = arr[j+1];
           arr[j+1] = arr[j];
           arr[j] = temp;
         }
    ```
    - If the first element is greater than the second, swap them.
    - This moves the larger element one step forward.

**Example Walkthrough**
Initial Array: {5, 2, 9, 1, 6}
  - Pass 1 (move the largest element to the end):
    - Compare 5 and 2 → Swap → {2, 5, 9, 1, 6}
    - Compare 5 and 9 → No Swap
    - Compare 9 and 1 → Swap → {2, 5, 1, 9, 6}
    - Compare 9 and 6 → Swap → {2, 5, 1, 6, 9}
    -  (✔ 9 is now sorted)
 - Pass 2 (move the second largest to its place):
    - Compare 2 and 5 → No Swap
    - Compare 5 and 1 → Swap → {2, 1, 5, 6, 9}
    - Compare 5 and 6 → No Swap
    - ( ✔ 6 is now sorted)
 - This process continues until the entire array is sorted.

**Time Complexity**
- Worst-case and average-case: **O(n²)** (because of two nested loops)
- Best case (already sorted array): O(n) (optimized version)
**Space Complexity: O(1)**
```
//Time complexity here is O(n) if given array is in ascending order and already sorted

int main() {

int arr[] = {13,46,24,52,20,9};
int n = sizeof(arr)/sizeof(arr[0]);
//print sorted  array
printf("unsorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
printf("\n");
//sorting
for(int i=0;i<n-1;i++)
{
    int swap = 0;
    for(int j=0;j<n-1-i;j++)
    {
        if(arr[j]>arr[j+1])
        {
            //swaping
            int temp =arr[j+1];
            arr[j+1]= arr[j];
            arr[j]=temp;
            swap =1;
            
        }
    }
    if(swap == 0)
    {
        break;
    }
    
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
# Insertion_sort #

**How Insertion Sort Works:**
- Takes an element and places at its correct position.
- Always consider 1st elemet as sorted so it starts from index i =1;
- Insertion Sort is a simple sorting algorithm that works the way you might sort playing cards in your hand. You take one card at a time and place it in the correct position relative to the already sorted cards.

**Time complexity: O($n^2$)**, (where N = size of the array), for the worst, and average cases.
Reason: If we carefully observe, we can notice that the outer loop, say i, is running from 0 to n-1 i.e. n times, and for each i, the inner loop j runs from i to 1 i.e. i times. For, i = 1, the inner loop runs 1 time, for i = 2, the inner loop runs 2 times, and so on. So, the total steps will be approximately the following: 1 + 2 + 3 +......+ (n-2) + (n-1). The summation is approximately the sum of the first n natural numbers i.e. (n*(n+1))/2. The precise time complexity will be O(n2/2 + n/2). Previously, we have learned that we can ignore the lower values as well as the constant coefficients. So, the time complexity is O(n2). Here the value of n is N i.e. the size of the array.

**Space Complexity: O(1)**

**Step-by-Step Explanation**
- Start with the first element (considered already sorted).
- Take the next element and compare it with the sorted part.
- If it’s smaller, shift larger elements to the right and insert it in the correct position.
- Repeat for every element in the list until everything is sorted.
  
- The purple color represents the unsorted array.
- The yellow color represents the current element that needs to be placed in the appropriate position.
- The green color represents the sorted array.
- Outer loop iteration 1(selected index i = 0): The element at index i=0 is 13 and there is no other element on the left of 13. So, currently, the subarray up to the first index is sorted as it contains only element 13.


![image](https://github.com/user-attachments/assets/68542990-65e1-45c2-ba90-133df857c490)

- Outer loop iteration 2(selected index i = 1):The selected element at index i=1 is 46. Now, we will try to move leftwards and put 46 in its correct position. Here, 46 > 13 and so 46 is already in its correct position. Now, the subarray up to the second index is sorted.


![image](https://github.com/user-attachments/assets/a02caa55-8cce-493f-bb5b-51ca54b572cd)

- Outer loop iteration 3(selected index i = 2): The selected element at index i=2 is 24. Now, we will try to move leftwards and put 24 in its correct position. Here, the correct position for 24 will be index 1. So, we will insert 24 in between 13 and 46. We will do it by swapping 24 and 46. Now, the subarray up to the third index is sorted.


![image](https://github.com/user-attachments/assets/66579d8a-1852-4283-9427-8113de129307)

- Outer loop iteration 4(selected index i = 3):The selected element at index i=3 is 52. Now, we will try to move leftwards and put 52 in its correct position. Here, the correct position for 52 will be index 3. So, we need not swap anything. Now, the subarray up to the fourth index is sorted.


![image](https://github.com/user-attachments/assets/68b06267-1ae7-457d-aafa-78ca898893ca)

- Outer loop iteration 5(selected index i = 4):The selected element at index i=4 is 20. Now, we will try to move leftwards and put 20 in its correct position. Here, the correct position for 20 will be index 1. So, we need to swap adjacent elements until 20 reaches index 1. Now, the subarray up to the fifth index is sorted.


![image](https://github.com/user-attachments/assets/367ec960-d158-4be7-a0b6-941fad7abb95)

- Outer loop iteration 6(selected index i = 5):The selected element at index i=5 is 9. Now, we will try to move leftwards and put 9 in its correct position. Here, the correct position for 9 will be index 0. So, we need to swap adjacent elements until 9 reaches index 0. Now, the whole array is sorted.


![image](https://github.com/user-attachments/assets/fa3379bb-03a2-4a6c-a500-b578fdf4742b)

```
int main() {

//int arr[] = {13,46,24,52,20,9};
int arr[] = {5,3,1};
int n = sizeof(arr)/sizeof(arr[0]);
//print sorted  array
printf("unsorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
printf("\n");
//sorting
for(int i=1;i<=n;i++)
{
    int j = i;
    while(arr[j]<arr[j-1] && j>0)
    {
            int temp =arr[j-1];
            arr[j-1]= arr[j];
            arr[j]=temp;
            j--;
    }
            
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

# Merge_sort #
references : https://www.youtube.com/watch?v=jlHkDBEumP0
- bubble,insertion,selcetion haave time worst case complexity O($n^2$).Merge sort is better then them as it has timecomplexity of O(nlogn) 
- This is divide and merge algo.For dividing the array we will use recursion
- Merge Sort is a divide and conquers algorithm, it divides the given array into equal parts     and then merges the 2 sorted parts. here we need one extra array to store the sorted values.
- There are 2 main functions :
  - merge(): This function is used to merge the 2 halves of the array. It assumes that both parts of the array are sorted and merges both of them.
  - mergeSort(): This function divides the array into 2 parts. low to mid and mid+1 to high where,
   - low = leftmost index of the array
   - high = rightmost index of the array
   - mid = Middle index of the array 
- We recursively split the array, and go from top-down until all sub-arrays size becomes 1.

**Approach:**

- We will be creating 2 functions mergeSort() and merge().
- mergeSort(arr[], low, high):
    - In order to implement merge sort we need to first divide the given array into two halves. Now, if we carefully observe, we need not divide the array and create a separate array, but we will divide the array's range into halves every time. For example, the given range of the array is 0 to 4(0-based indexing). Now on the first go, we will divide the range into half like (0+4)/2 = 2. So, the range of the left half will be 0 to 2 and for the right half, the range will be 3 to 4. Similarly, if the given range is low to high, the range for the two halves will be low to mid and mid+1 to high, where mid = (low+high)/2. This process will continue until the range size becomes.
    - So, in mergeSort(), we will divide the array around the middle index(rather than creating a separate array) by making the recursive call :
        1) mergeSort(arr,low,mid)   [Left half of the array]
        2) mergeSort(arr,mid+1,high)  [Right half of the array]
where low = leftmost index of the array, high = rightmost index of the array, and mid = middle index of the array.
    - Now, in order to complete the recursive function, we need to write the base case as well. We know from step 2.1, that our recursion ends when the array has only 1 element left. So, the leftmost index, low, and the rightmost index high become the same as they are pointing to a single element.
Base Case: if(low >= high) return;

  **Pseudocode**

    ![image](https://github.com/user-attachments/assets/08e430d4-d60c-4174-a62b-511d7b777322)

- merge(arr[], low, mid, high):
  - In the merge function, we will use a temp array to store the elements of the two sorted arrays after merging. Here, the range of the left array is low to mid and the range for the right half is mid+1 to high.
  - Now we will take two pointers left and right, where left starts from low and right starts from mid+1.
  - Using a while loop( while(left <= mid && right <= high)), we will select two elements, one from each half, and will consider the smallest one among the two. Then, we will insert the smallest element in the temp array.
  - After that, the left-out elements in both halves will be copied as it is into the temp array.
  - Now, we will just transfer the elements of the temp array to the range low to high in the original array. The pseudo code will look like the following:
      ![image](https://github.com/user-attachments/assets/f3d8f153-3889-415a-99ee-2af1a7ec5179)

**Time complexity: O(nlogn)**

  - Reason: At each step, we divide the whole array, for that logn and we assume n steps are taken to get sorted array, so overall time complexity will be nlogn

**Space complexity: O(n)** 

  - Reason: We are using a temporary array to store elements in sorted order.
  - Auxiliary Space Complexity: O(n)

```
// Online C compiler to run C program online
#include <stdio.h>
void merging(int arr[],int low,int mid,int high)
{
    int temp[7]; //temp array
    int left = low; // starting index of left half of arr
    int right = mid+1; // starting index of right half of arr
    int k = low;
     //storing elements in the temporary array in a sorted manner//
    while(left <=mid && right <=high) 
    {
        if(arr[left]<=arr[right])
        {
            temp[k] = arr[left];
            left++;
            k++;
        }
        else
        { 
            temp[k] = arr[right];
            k++;
            right++;
        }
    }
  //  if elements on the right half are still left //
    if(left>mid) 
    {
        while(right<=high)
        {
            temp[k] = arr[right];
            k++;
            right++;
        }
    }
    else
    {
        while(left<=mid)  // if elements on the left half are still left //
        {
            temp[k] = arr[left];
            k++;
            left++;
        }
    }
    // transfering all elements from temporary to arr //
    for(int i=low;i<=high;i++)
    {
         arr[i]=temp[i];
    }
}

void merge_sort(int arr[],int low,int high)
{
    if(low==high)
    {
        return;
    }
    int mid = (low+high)/2;
    merge_sort(arr,low,mid); // left half
    merge_sort(arr,mid+1,high); / right half
    merging(arr,low,mid,high); // merging sorted halves
}

int main() {

int arr[]={3,2,8,5,1,4,23};
int size = 7;
int low = 0;
int high = size -1;
printf("unsorted array\n");
for(int i=0;i<size;i++)
{
    printf("%d\t",arr[i]);
}
//calling merge sorting
merge_sort(arr,low, high);
printf("\nsorted array\n");
for(int i=0;i<size;i++)
{
    printf("%d\t",arr[i]);
}

    return 0;
}
```

# Quick_sort #

- has time complexity of O(nlogn), but space complexity of O(1) as it doesn't need extra temp array like merge sort.
- Quick Sort is a divide-and-conquer algorithm like the Merge Sort. But unlike Merge sort, this algorithm does not use any extra array for sorting(though it uses an auxiliary stack space). So, from that perspective, Quick sort is slightly better than Merge sort.
- Note: Here in this tutorial, we have chosen the first element as our pivot. You can choose any element as per your choice.
  
**algorithm**

1) pick a pivot elemnt.pivot can be any elemnt in an array it can be the 1st/last/mid/random element in the array
2) now after picking pivot place it in its correct position in the sorted array.
3) smaller on the left and larger numbers  on the right of the pivot.
4) This algorithm is basically a repetition of two simple steps that are the following:
    - Pick a pivot and place it in its correct place in the sorted array.
    - Shift smaller elements(i.e. Smaller than the pivot) on the left of the pivot and larger ones to the right.

- Now, let’s discuss the steps in detail considering the array {4,6,2,5,7,9,1,3}:

  - Step 1: The first thing is to choose the pivot. A pivot is basically a chosen element of the given array. The element or the pivot can be chosen by our choice. So, in an array a pivot can be any of the following:

    - The first element of the array
    - The last element of the array
    - Median of array
    - any Random element of the array
  - After choosing the pivot(i.e. the element), we should place it in its correct position(i.e. The place it should be after the array gets sorted) in the array. For example, if the given array is {4,6,2,5,7,9,1,3}, the correct position of 4 will be the 4th position.
    
  - Step 2: In step 2, we will shift the smaller elements(i.e. Smaller than the pivot) to the left of the pivot and the larger ones to the right of the pivot. In the example, if the chosen pivot is 4, after performing step 2 the array will look like: {3, 2, 1, 4, 6, 5, 7, 9}. 

  - From the explanation, we can see that after completing the steps, pivot 4 is in its correct position with the left and right subarray unsorted. Now we will apply these two steps on the left subarray and the right subarray recursively. And we will continue this process until the size of the unsorted part becomes 1(as an array with a single element is always sorted).

  - So, from the above intuition, we can get a clear idea that we are going to use recursion in this algorithm.To summarize, the main intention of this process is to place the pivot, after each recursion call, at its final position, where the pivot should be in the final sorted array.

**Approach:**

  - Now, let’s understand how we are going to implement the logic of the above steps. In the intuition, we have seen that the given array should be broken down into subarrays. But while implementing, we are not going to break down and create any new arrays. Instead, we will specify the range of the subarrays using two indices or pointers(i.e. low pointer and high pointer) each time while breaking down the array.

  - The algorithm steps are the following for the quickSort() function:

    - Initially, the low points to the first index and the high points to the last index(as the range is n i.e. the size of the array). 
    - After that, we will get the index(where the pivot should be placed after sorting) while shifting the smaller elements on the left and the larger ones on the right using a partition() function discussed later.Now, this index can be called the partition index as it creates a partition between the left and the right unsorted subarrays.
    - After placing the pivot in the partition index(within the partition() function specified), we need to call the function quickSort() for the left and the right subarray recursively. So, the range of the left subarray will be [low to (partition index - 1)] and the range of the right subarray will be [(partition index + 1) to high]. 
This is how the recursion will continue until the range becomes 1.

  ![image](https://github.com/user-attachments/assets/d09fdf3c-2602-43fe-8d08-dadd66f4d47a)

  - Now, let’s understand how to implement the partition() function to get the partition index.

      - Inside the function, we will first select the pivot(i.e. arr[low] in our case).
      - Now, we will again take two-pointers i and j. The i pointer points to low and the j points to high.
      - Now, the pointer i will move forward and find the first element that is greater than the pivot. Similarly, the pointer j will move backward and find the first element that is smaller than the pivot.
Here, we need to add some checks like i <= high-1 and j >= low+1. Because it might happen that i is standing at high and trying to proceed or j is standing at low and trying to exceed.
      - Once we find such elements i.e. arr[i] > pivot and arr[j] < pivot, and i < j, we will swap arr[i] and arr[j].
      - We will continue step 3 and step 4, until j becomes smaller than i.
Finally, we will swap the pivot element(i.e. arr[low]) with arr[j] and will return the index j i.e. the partition index.

![image](https://github.com/user-attachments/assets/6c4ead19-a2c0-4dd7-9de2-be91847884ff)

Note: In the function, we have kept the elements equal to the pivot on the left side. If you choose to place them on the right, check 1 will be arr[i] < pivot and check 2 will be arr[j] >= pivot.

**Time Complexity: O(N*logN)**, where N = size of the array.

  - Reason: At each step, we divide the whole array, for that logN and n steps are taken for the partition() function, so overall time complexity will be N*logN.

  - The following recurrence relation can be written for Quick sort : 

  - F(n) = F(k) + F(n-1-k) 

  - Here k is the number of elements smaller or equal to the pivot and n-1-k denotes elements greater than the pivot.

  - There can be 2 cases :

    - Worst Case – This case occurs when the pivot is the greatest or smallest element of the array. If the partition is done and the last element is the pivot, then the worst case would be either in the increasing order of the array or in the decreasing order of the array. 

      - Recurrence:F(n) = F(0)+F(n-1)  or  F(n) = F(n-1) + F(0) 

      - Worst Case Time complexity: O(n2) 

    - Best Case – This case occurs when the pivot is the middle element or near to middle element of the array.
        - Recurrence :F(n) = 2F(n/2)

Time Complexity for the best and average case: O(N*logN)

Space Complexity: O(1) + O(N) auxiliary stack space.

```
int partition(int arr[],int low,int high)
{
    int i=low;
    int j=high;
    int temp =0;
    int pivot = arr[low];
    while(i<j)
    {
        while(arr[i]<=pivot && i<=high)
        {
            i++;            
        }
        while(arr[j]>pivot && j>=low)
        {
            j--;
        }
        if(i<j)
        {
            temp = arr[j];
            arr[j]= arr[i];
            arr[i]= temp;
        }
    }
    temp = arr[j];
    arr[j] = arr[low];
    arr[low] = temp;
    return j;
}

void quick_sort(int arr[],int low,int high)
{
    if(low == high)
    {
        return  ;     
    }
    int partitionvalue = partition(arr,low,high);
    quick_sort(arr,low,partitionvalue);
    quick_sort(arr,partitionvalue+1,high);
    
}

int main() {

int arr[]={3,2,8,5,1,4,23};
int size = 7;
int low = 0;
int high = size -1;
printf("unsorted array\n");
for(int i=0;i<size;i++)
{
    printf("%d\t",arr[i]);
}
//calling merge sorting
quick_sort(arr,low, high);
printf("\nsorted array\n");
for(int i=0;i<size;i++)
{
    printf("%d\t",arr[i]);
}

    return 0;
}

```

# Find_the_Largest_element_in_an_array #
  - Their are 2 approches
      1) use sorting to sort array , the last element of an array will be the largest. Time complexity will be O(nlogn) if using merge or quick sort.
      2) using "max" variable. take 1st array index as "max value" and compare it will all the array elements if elemnt is "greater than the max value replace the max value" with that array element keep doing this till end of the array,at the end the max varibale will have largest value. This will have time complexity of O(n).

```

//finding largest element
int max = arr[0];
for(int i=1;i<n;i++)
{
    if(arr[i]>max)
    {
        max=arr[i];
    }
}

```

# Find_the_2nd_Largest_element_in_an_array #

  - Their are 2 approches
    - use sorting to sort array , the last2nd element of an array will be the 2nd largest. Time complexity will be O(nlogn) if using merge or quick sort.
    - using 2 varibles "large" and "2ndlarge"Time Complexity: O(N), Single-pass solution
and Space Complexity: O(1).Initially consider 2ndlarge element as -1 (if array contains only positive values) or "INT_MIN(defiend in <limits.h>)"if elments are negative. It is based on the logic that if a no. is greater than(NOTE: here dont take arr[current]as >=large just take arr[current]>large beacuse if you take = then we wont be able to find 2nd largest element) the no. stored in "large" then the no.stored in the "large" will go to "2ndlarge".
        - If the current element is larger than ‘large’ then update "2ndlarge" with "large" and "large" with current element. 
        - Else if the current element is larger than "2ndlarge" but lesser then the "large" then we update the variable 2ndlarge with current element.

```
#include <stdio.h>
#include <limits.h>

int main() {

int arr[] = {-13,-46,-24,-10,-20,-9,-1};
//int arr[] = {5};
int n = sizeof(arr)/sizeof(arr[0]);
//print sorted  array
printf("unsorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
printf("\n");
//finding largest element
int large = arr[0];
int secondlarge = INT_MIN;
for(int i=1;i<n;i++)
{
    if(arr[i]>large)
    {
        secondlarge = large;
        large=arr[i];
    }
    else
    {
        if(arr[i]<large && arr[i]>secondlarge)
        {
            secondlarge = arr[i];
        }
    }
}
    printf("2nd largest array element\n %d",secondlarge);
    return 0;
}
```

# Check_if_an_Array_is_Sorted #

**Logic**
  - if the given array is sorted in ascending order then "descending" flag will be set to false and ascending flag will be set to true.
  - if the given array is sorted in descending order then "ascending" flag will be set to false and descending flag will be set to true.
  - As we know that for a sorted array the previous of every element is smaller than or equal to its current element.
  - So, Through this, we can conclude that if the previous element is smaller than or equal to the current element then. Then we can say that the two elements are sorted. If the condition is true for the entire array then the array is sorted.
  - We will check every element with its previous element if the previous element is smaller than or equal to the current element then we will move to the next index.
  - If the whole array is traversed successfully or the size of the given array is zero or one (i.e N = 0 or N = 1). Then we will return True else return False.
  - Time Complexity: O(N)
  - Space Complexity: O(1)

```
// Online C compiler to run C program online
#include <stdio.h>
#include <limits.h>
#include <stdbool.h>

bool checkarray(int arr[],int n)
{
bool ascending = true;
bool descending = true;
    for(int i=1;i<n;i++)
    {
        if(arr[i]>=arr[i-1])
        {
            descending = false;
        }
        if(arr[i]<=arr[i-1])
        {
            ascending = false;
        }
    }
    if(ascending == true ||descending == true )
    {
        return true;
    }
    else
        return false;
}

int main() {

//int arr[] = {-13,-46,-24,-10,-20,-9,-1};
int arr[] = {5,4,3,2,1};
int n = sizeof(arr)/sizeof(arr[0]);

printf("given array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
printf("\n");

//array is sorted or not
bool status=checkarray(arr,n);
if(status == true)
{
    printf("array is sorted\n");
}
else
{
    printf("array is unsorted\n");
}
    return 0;
}
```
# Remove_Duplicates_in_place_from_Sorted_Array #
  - Use 2 pointer approach.
    
    - approach 1 : We can think of using two pointers ‘i’ and ‘j’, we move ‘i’ till we don't get a number arr[i-1] which is different from arr[i]. As we got a unique number we will update its arr[j] by arr[i-1] value and increase the j pointer 
      - Now when i reach the last element(i.e n-1 th element) at that time assign arr[i] value to  arr[j] to cover the last element as well.
        
    - approach 2 : Another approch can be We can think of using two pointers ‘i’ and ‘j’, we move ‘j’ till we don't get a number arr[j] which is different from arr[i]. As we got a unique number we will increase the i pointer and update its value by arr[j].
      - Take a variable i as 0;
      - Use a for loop by using a variable ‘j’ from 1 to length of the array.
      - If arr[j] != arr[i], increase ‘i’ and update arr[i] == arr[j].
      - After completion of the loop return i+1, i.e size of the array of unique elements.
        
    - Both approach will take Time Complexity: O(N) and Space Complexity: O(1).
```
\\Approach 1
int remove_duplicates(int arr[],int n)
{
    int i=1,j=0;
    while(i<n)
    {
        if(arr[i]!=arr[i-1])
        {
            arr[j]=arr[i-1];
            j++;
        }
        if(i==n-1)
        {
            arr[j]=arr[i];
        }
        i++;
    }
    return j;
}
int main() {

int arr[] = {1,1,2,2,2,3,4};
//int arr[] = {5};
int n = sizeof(arr)/sizeof(arr[0]);

printf("unsorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
//remove duplicates elemets
int index =remove_duplicates(arr,n);
printf("\nfinal array\n");
for(int i=0;i<=index;i++)
{
    printf("%d\t",arr[i]);
}

    return 0;
}
```
```
\\Approach 2

int removeDuplicates(int arr[], int n)
{
  int i = 0;
  for (int j = 1; j < n; j++) {
    if (arr[i] != arr[j]) {
      i++;
      arr[i] = arr[j];
    }
  }
  return i + 1;
}

```
# Left_Rotate_the_Array_by_One # 
  - At first, we have to shift the array towards the left so, we store the value of the first index in a variable (let it be temp).
  - Then we iterate the array from the 1st index less then the nth index
  - And then store the value present in the next index to the current index like this :arr[j] = arr[j-1]
  - At last, put the value of variable x in the last index of the array.
    ![image](https://github.com/user-attachments/assets/f0a041ae-21fa-4640-a330-bce7185f29d7)

  - Time Complexity: O(n), as we iterate through the array only once.
  - Space Complexity: O(1) as no extra space is used.
    
```
#include <stdio.h>

void rotate_array(int arr[],int n)
{
    int temp=arr[0],j=1;
    while(j<n)
    {
        arr[j-1]=arr[j];
            j++;
    }
    arr[j-1]=temp;
}
int main() {

//int arr[] = {1,2,3,4,5,6,7};
int arr[] = {5,1};
int n = sizeof(arr)/sizeof(arr[0]);

printf("unsorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
//remove duplicates elemets
rotate_array(arr,n);
printf("\nfinal array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}

    return 0;
}
```

# Rotate_array_by_K_elements #

  - **Approach 1 : Brute force**
      - Uses an in-place shifting mechanism without extra space.
      - It will be same as above mentioned logic for (rotate array left by 1).Just add 1 more while loop (i<=k) to rotate array by "k" times.
      - **Time Complexity: O(n*k)**
        - Each rotation takes O(n) time since it shifts all elements once.
        - Since we rotate k times, the total complexity is O(n * k)."n" is no. of array elments
        - **Space Complexity: O(1)**

  - **Approach 2 : Optimal Using "**Reversal Algorithm**"**
      - here we have to reverse the 1st k elements, then reverse the elemets form k+1 to n-1 and then reverse the entire array. this will give you the reverse array.
      -  **Time Complexity: O(n)**
        -  since we dont need to loop k times .reverse(arr,start,k-1) has time complexity of O(k),reverse(arr,k,n-1) has timecomplexity of O(n-k), reverse(arr,start,n-1) has timecomplexity of O(n). O(k+n-k+n)=O(2n) ~ O(n).
        - **Space Complexity: O(1)**
         - no extra array is needed.

    
```

// Approach1 brute force
#include <stdio.h>

void rotate_array(int arr[],int n)
{
    int i=1,k=3;
while(i<=k)
{
    int temp=arr[0],j=1;
    while(j<n)
    {
        arr[j-1]=arr[j];
            j++;
    }
    arr[j-1]=temp;
    i++;
}

}
int main() {

int arr[] = {1,2,3,4,5,6,7};
//int arr[] = {5,1};
int n = sizeof(arr)/sizeof(arr[0]);

printf("unsorted array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}
//remove duplicates elemets
rotate_array(arr,n);
printf("\nfinal array\n");
for(int i=0;i<n;i++)
{
    printf("%d\t",arr[i]);
}

    return 0;
}
```

```
// Approach2 REVERSE approach

#include <stdio.h>
void reverse (int arr[],int start,int end)
{
    while(start<end)
    {
    int temp = arr[start];
    arr[start] = arr[end];
    arr[end] = temp;
    start++;
    end--;
    }
}

void rotate_array(int arr[],int n,int k)
{
    int start = 0;
    reverse(arr,start,k-1); //time omp
    reverse(arr,k,n-1);
    reverse(arr,start,n-1);
}
int main() {
 int arr[]  = {1,3,8,7,6,10};
 int k;
 int n = sizeof(arr)/sizeof(arr[0]);
 printf("given array\n");
 for(int i=0;i<n;i++)
 {
     printf("%d\t",arr[i]);
 }
 printf("\nenter the value by which array need to be rotated\n");
 scanf("%d",&k);
 rotate_array(arr,n,k);
 printf("\nrotated array\n");
  for(int i=0;i<n;i++)
 {
     printf("%d\t",arr[i]);
 }
    return 0;
}

```
# single linked list  #

# Reverse_linked_list #
  1) Initialize Pointers
    - prev: Keeps track of the previous node. Initially, it's NULL because the first node will become the last one in the reversed list.
    - current: Points to the current node in the linked list. Starts at head.
    - next: A temporary pointer to store the next node while we modify the links.
  2) Traverse the Linked List
     ```
     while (current != NULL) {    // Traverse until the end
     ```
     - The loop runs until current becomes NULL, meaning we have processed all nodes.
  3)  ```
      next = current->next;    // Step 1: Store next node
      ```
      - next temporarily stores the next node in the original list.
      - Without this step, we'd lose track of the rest of the list when we reverse the pointer.
  4)  ```
      current->next = prev;    // Step 2: Reverse current node's pointer
      ```
      - We reverse the link of the current node by making it point to prev, which initially is NULL (for the first node)
        
  5) ```
     prev = current;          // Step 3: Move prev forward
     current = next;          // Step 4: Move current forward
     return prev;
     ```
     - Move prev forward to track the last processed node (the new head of the reversed list).
     - Move current forward to continue processing the next node.
     - Once the loop finishes, prev holds the new head of the reversed linked list

```

#include <stdio.h>
#include <stdlib.h>

struct node{
    
    int data;
    struct node *next;
};

//reverse linkled list
reference : https://www.youtube.com/watch?v=eB1G2QtcOyM
struct node* reversell(struct node *head1)
{
    struct node* curr = head1;
    struct node* prev = NULL;
    struct node* next = curr->next;
    
    while(curr!=NULL)
    {
        next= curr->next;
        curr->next = prev;
        prev=curr;
        curr=next;
    }
    head1 = prev;
    return head1;
}

//display linked list
void display(struct node*head1)
{
    struct node*p = head1;
    while(p!=NULL)
    {
        printf("%d\t",p->data);
        p=p->next;
    }
}

//crete node and add elements at the end of list
struct node* createnode1(struct node *head1)
{
    struct node *temp = head1;
    struct node *new_add = (struct node *)malloc(sizeof(struct node));
    printf("enter the value\n");
    scanf("%d",&new_add->data);
    new_add->next = NULL;
    if(head1==NULL)
    {
        head1 = new_add;
    }
    else
    {
        while(temp->next!=NULL)
        {
            temp = temp->next;
        }
        temp->next = new_add;
    }
    return head1;
}

int main() {

struct node *head1 = NULL;
//struct node *head2 = NULL;

//create node
for(int i=0;i<5;i++)
{
    head1 = createnode1(head1);
}

//print list1
printf("\nlist 1 data :");
display(head1);


//reverse the LL
head1 = reversell(head1);
printf("\nreverse list1 data :");

//print reverse ll
display(head1);
    return 0;
}
```
# Implementation_of_stack_using_array #

```
reference : https://www.youtube.com/watch?v=VmsTAVpz0xo&list=PLcFL7FQZfCUl-Qprn5QKv3YSsejh5NXT-&index=2
// Online C compiler to run C program online
#include <stdio.h>
#define N 5
int stack[N];
int top =-1;

void push()
{
    int num;
    printf("enter the element to push\n");
    scanf("%d",&num);
    if(top == N-1)
    {
        printf("stack overflow\n");
    }
    else
    {
        top++;
        stack[top] = num;
    }
}

void pop()
{
    if(top == -1)
    {
        printf("stack underflow\n");
    }
    else
    {
        printf("element poped from stack %d\n",stack[top]);
        top--;
    }
}

void peek()
{
    if(top == -1)
    {
        printf("no peak\n");
    }
    else
    {
        printf("peek: %d\n",stack[top]);
    }
}
 
void display()  
{
    if(top == -1)
    {
        printf("stack is empty\n");
    }
    else
    {
        for(int i =top;i>=0;i--)
        {
            printf("stack[%d] = %d\n",i,stack[i]);
        }
    }
}
int main() {
int choice;
while(1)
{
    printf("enter the choice : 1)push 2)pop 3)peek 4)display\n");
    scanf("%d",&choice);
    
    switch(choice)
    {
        case 1: push();
               break;
        case 2: pop();
               break;
        case 3: peek();
               break;
        case 4: display();
               break;
    }
}
    return 0;
}
```
# Implementation_of_stack_using_linked_list #

  - top in stack wil be the head of the linked list(top = head), so whenever we add a new node in the list it will be from the front not from the end.

![image](https://github.com/user-attachments/assets/543a1206-8ca8-4ec9-866b-26f381bab9b2)

```
reference : https://www.youtube.com/watch?v=T_UXDTy23DQ&list=PLcFL7FQZfCUl-Qprn5QKv3YSsejh5NXT-&index=3
// Online C compiler to run C program online
#include <stdio.h>
#include <stdlib.h>

struct node{
    int data;
    struct node *next;
};

struct node *top = NULL;

void push()
{
    //add elements at the front of linked list so that time complexity will be O(1) if it is at end then time complexity for push(),pop,peek will be O(N)
    int num;
    printf("enter the element to push\n");
    scanf("%d",&num);
    struct node *new_node = (struct node *)malloc(sizeof(struct node));
    new_node->data = num;
    new_node->next = top;
    top = new_node;
}

void pop()
{
    struct node *temp = top;
    if(top == NULL)
    {
        printf("no elements to pop\n");
    }
    else
    {
        printf("popped node = %d\n",top->data);
        top = top->next;
        free(temp);
    }
}

void peek()
{
    if(top == NULL)
    {
        printf("stack is emmpty\n");
    }
    else
    {
        printf("peek element = %d\n",top->data);
    }
}
 
void display(struct node *top)  
{
     struct node *temp = top;
    if(top == NULL)
    {
        printf("stack is empty no items to dispaly\n");
    }
    else
    {
        while(temp!=NULL)
        {
            printf("data = %d\n",temp->data);
            temp = temp->next;
        }
    }
}
int main() {
int choice;
while(1)
{
    printf("enter the choice : 1)push 2)pop 3)peek 4)display\n");
    scanf("%d",&choice);
    
    switch(choice)
    {
        case 1: push();
               break;
        case 2: pop();
               break;
        case 3: peek();
               break;
        case 4: display(top);
               break;
    }
}
    return 0;
}
```
# Implementation_of_stack_using_queue #

  - You’re implementing a stack (LIFO) using two queues (FIFO). This trick is common in interviews — and this code uses the approach where push() is costly to ensure pop() and peek() are fast.
  - here push() is costly to ensure pop() and peek() are fast.
  - Concept Recap
    - A stack works on Last In, First Out:
    - push(x) → adds to the top
    - pop() → removes from the top
    - peek() → looks at the top
    - But queues work on First In, First Out. So to simulate stack behavior using queues, we manipulate how and where we insert elements.
    - This solution makes push() costly by ensuring the newest element always ends up at the front of the main queue (q1), making pop() and peek() easy.

```
int q1[NUM], q2[NUM];
int front1 = -1, rear1 = -1;
int front2 = -1, rear2 = -1;

```
- q1 is the main queue that simulates the stack.
- q2 is a temporary queue used during push().
- front and rear pointers track where the queue starts and ends. A -1 means the queue is empty.

**push() Logic**

  - Step 1: Copy all elements from q1 to q2
    ```
      while (front1 != -1 && front1 <= rear1)
      {
        ...
        q2[++rear2] = q1[front1++];
      }
    ```
  - Step 2: Add new element to q1: We reset q1 and insert the new element first — because that’s how stacks work (new element is always on top).

    ```
      front1 = 0;
      rear1 = 0;
      q1[rear1] = num;
    ```
  - Step 3: Copy old elements back to q1: We move everything back from q2 to q1. Now the new element is at the front of the queue — perfect for pop().
    ```
      while (front2 != -1 && front2 <= rear2) 
      {
        q1[++rear1] = q2[front2++];
      }
    ```
  - Final step: Reset q2 for next use

**pop() Logic**
  ```
    if (front1 == -1 || front1 > rear1)
    //Checks if the queue is empty.  
      printf("popped element %d\n", q1[front1]);
      front1++;
  ```
  - Removes the element at the front (which is the top of the stack). Efficient: O(1).
If the stack becomes empty after popping, the condition resets both pointers to -1.


![image](https://github.com/user-attachments/assets/02093805-f675-4041-93bb-17f3e54862b4)








```
reference: https://www.youtube.com/watch?v=sFvP5Ois0CE
// Implementing stack using queueu
#include <stdio.h>
#include <stdlib.h>

#define NUM 6
int q1[NUM];
int q2[NUM];
int front1 = -1,rear1 = -1; 
int front2 = -1,rear2 = -1; 

void push()
{
    int num;
    printf("enter the element to push\n");
    scanf("%d",&num);
    //copy all q1 elemts to q2
    while(front1 !=-1 && front1<=rear1)
    {
        if(rear2 == NUM-1)
        {
            printf("q2 overflow\n");
            return;
        }
        if(front2 ==-1)
        {
            front2 =0;
        }
        q2[++rear2] = q1[front1++];
    }
    //enter elements at 0th index of q1
    if (rear1 == NUM - 1) 
    {
        printf("q1 Overflow\n");
        return;
    }

    front1 =0;
    rear1=0;
    q1[rear1] = num;
    //copy all q2 elemts to q1
    while(front2 !=-1 && front2<=rear2)
    {
        q1[++rear1] = q2[front2++];

    }
    //reset the q2
    rear2=front2=-1;
}

void pop()
{
    if(front1==-1 || front1>rear1)
    {
        printf("q1 is empty nothing to pop\n");
        front1=rear1=-1;
    }
    else
    {
        printf("poped element %d\n",q1[front1]);
        front1++;
    }

}

void peek()
{
    if(front1==-1 || front1>rear1)
    {
        printf("q1 is empty nothing to peek\n");
    }
    else
    {
        printf("peek element is : %d\n",q1[front1]);
    }
}
 
void display()  
{
    if(front1==-1 || front1>rear1)
    {
        printf("q1 is empty nothing to dispaly\n");
    }
    else
    {
        for(int i = front1;i<=rear1;i++)
        {
            printf("stack elemets are : %d\n",q1[i]);
        }
    }
}
int main() {
int choice;
while(1)
{
    printf("enter the choice : 1)push 2)pop 3)peek 4)display\n");
    scanf("%d",&choice);
    
    switch(choice)
    {
        case 1: push();
               break;
        case 2: pop();
               break;
        case 3: peek();
               break;
        case 4: display();
               break;
    }
}
    return 0;
}
```
# find_and_Remove_duplicates_from_string #

```


// find and Remove duplicates from string
#include <stdio.h>
#include <string.h>

void find_duplicates(char *str)
{
    int i=0;
    char count[256] = {0};
    while(str[i]!='\0')
    {
        count[str[i]]++;
        i++;
    }
    for(int j=0;j<256;j++)
    {
        if(count[j]>1)
        {
            printf("repeated characters are %c\n",j);
        }
    }
    
}
void remove_duplicates(char* str)
{
    int i=0,k=0;
    char count[256] = {0};
    while(str[i]!='\0')
    {
        if(count[str[i]]==0)
        {
            str[k]= str[i];
            count[str[i]]++;
            k++;
        }
        
        i++;
        
    }
    str[k]='\0';
}

int main() 
{
char str[] = "helloo";
printf("%s\n",str);
find_duplicates(str);
remove_duplicates(str);
printf("%s",str);
return 0;
}

```
# sort_array_of_strings_using_quick_sort #

- Space: O(1) (in-place)
- Time (average): O(n log n × m)
- Why m factor appears?
  - Each comparison between two strings is not O(1) like comparing integers.
  - Comparing two strings takes O(m) time in the worst case, because you may have to check all characters until you find a difference (or reach the end).
  - n = number of strings in the array
  - m = average length of each string
    
```
#include <stdio.h>

// Custom string compare: like strcmp, returns +ve, -ve or 0
int stringCompare(char *s1, char *s2) {
    while (*s1 && *s2) {
        if (*s1 != *s2) {
            return (*s1 - *s2);
        }
        s1++;
        s2++;
    }
    return (*s1 - *s2);
}

// Swap two string pointers
void swap(char **a, char **b) {
    char *temp = *a;
    *a = *b;
    *b = temp;
}

// Partition function using your logic
int partition(char *arr[], int low, int high) {
    int i = low;
    int j = high;
    char *pivot = arr[low];

    while (i < j) {
        while (stringCompare(arr[i], pivot) <= 0 && i <= high) {
            i++;
        }
        while (stringCompare(arr[j], pivot) > 0 && j >= low) {
            j--;
        }
        if (i < j) {
            swap(&arr[i], &arr[j]);
        }
    }

    swap(&arr[j], &arr[low]);  // Final pivot placement
    return j;
}

// Recursive quick sort
void quick_sort(char *arr[], int low, int high) {
    if (low < high) {
        int p = partition(arr, low, high);
        quick_sort(arr, low, p);
        quick_sort(arr, p + 1, high);
    }
}

int main() {
    char *arr[] = { "banana", "apple", "grape", "cherry", "orange" };
    int size = sizeof(arr) / sizeof(arr[0]);
    int low = 0;
    int high = size - 1;

    printf("Unsorted strings:\n");
    for (int i = 0; i < size; i++) {
        printf("%s\n", arr[i]);
    }

    quick_sort(arr, low, high);

    printf("\nSorted strings:\n");
    for (int i = 0; i < size; i++) {
        printf("%s\n", arr[i]);
    }

    return 0;
}


```
# insert_element_in_singlle_ll_front_position_end #
```

#include<stdio.h>
#include<stdlib.h>


struct node{
	int data;
	struct node *next;

};



void display(struct node **head)
{
	if(*head == NULL)
	{
		printf("linked list is empty\n");
		return;
	}
	else
	{
		struct node *temp = *head;
		printf("linked list elements : \n");
		while(temp!=NULL)
		{
			printf("%d\n",temp->data);
			temp = temp->next;
		}
	}


}

int free_list(struct node **head)
{
    struct node *current = *head;
    struct node *temp = NULL;
	if(*head == NULL)
	{
		printf("linked list is empty\n");
		return -1;
	}
    while(current!=NULL)
    {
        temp = current->next;
        free(current);
        current = temp;
    }
    *head = NULL;
    return 0;
}
int insert_at_front(struct node **head,int value)
{

	struct node *new_node = (struct node*)malloc(sizeof(struct node));
	if(new_node == NULL)
	{
	    printf("memory not allocated for new_node\n");
	    return -1;
	}
	new_node->data = value;
	new_node->next = NULL;

	new_node->next = *head;
	*head = new_node;


return 0;
}

int insert_at_position(struct node **head,int value,int position)
{
    struct node *new_node = (struct node*)malloc(sizeof(struct node));
	if(new_node == NULL)
	{
	    printf("memory not allocated for new_node\n");
	    return -1;
	}
	new_node->data = value;
	new_node->next = NULL;
    
    if(position < 0)
    {
        printf("position is negative\n");
        free(new_node);
        return -1;
    }
    if(position == 0)
    {
        new_node->next = *head;
        *head = new_node;
        return 0;
    }

     struct node *temp = *head;   
        for(int i=0;i<(position - 1) && (temp!=NULL);i++)
        {
            temp = temp->next;
        }
        if(temp == NULL)
        {
            printf("out of bound index\n");
            free(new_node);
            return -1;
        }
        new_node->next = temp->next;
        temp->next = new_node;
        
        return 0;
}

int insert_at_end(struct node **head,int value)
{

    struct node *new_node = (struct node*)malloc(sizeof(struct node));
	if(new_node == NULL)
	{
	    printf("memory not allocated for new_node\n");
	    return -1;
	}
	new_node->data = value;
	new_node->next = NULL;
	
	if(*head == NULL)
	{
	    *head=new_node;
	    return 0;
	}
	struct node *temp = *head;
	while(temp->next!=NULL)
	{
	    temp = temp->next;
	}
    temp->next = new_node;

return 0;
}

int main()
{
struct node *head = NULL;

//insert_at_front(&head,10);
//insert_at_front(&head,20);
//insert_at_front(&head,30);
//insert_at_front(&head,40);

//insert_at_position(&head,10,0);
//insert_at_position(&head,20,1);
//insert_at_position(&head,30,2);
//insert_at_position(&head,40,3);

//display(&head);
//insert_at_position(&head,50,4);
//display(&head);
//insert_at_position(&head,50,-1);

insert_at_end(&head,10);
insert_at_end(&head,20);
insert_at_end(&head,30);
insert_at_end(&head,40);
display(&head);
insert_at_end(&head,50);
display(&head);
free_list(&head);

return 0;
}
```
# Delete_element_in_single_ll_front_position_end #

```
//Delete_element_in_single_ll_front_position_end

#include<stdio.h>
#include<stdlib.h>


struct node{
	int data;
	struct node *next;

};

void display(struct node **head)
{
    if(*head == NULL)
    {
        printf("linked list is empty\n");
        return;
    }
    struct node *temp = *head;
    printf("linked list elements: \n");
    while(temp!=NULL)
    {
        printf("%d\n",temp->data);
        temp=temp->next;
    }

}

int free_list(struct node **head)
{
    if(*head == NULL)
    {
        printf("empty linked list\n");
        return 0;
    }
    struct node *current = *head;
    struct node *temp = NULL;
    while(current!=NULL)
    {
        temp = current->next;
        free(current);
        current = temp;
    }
    *head = NULL;
    return 0;
}
int delete_at_end(struct node **head)
{
    if(*head == NULL)
    {
        printf("empty linked list\n");
        return 0;
    }
    if((*head)->next == NULL)
    {
        printf("deleted element is : %d\n", (*head)->data); 
        free(*head);
        *head = NULL;
        return 0;
    }
    struct node *temp = *head;
    struct node *temp2 = NULL;
    while(temp->next->next!=NULL)
    {
        temp=temp->next;
    }
    temp2 = temp->next;
    printf("deleted element is : %d\n", temp2->data); 
    temp->next = temp2->next;
    free(temp2);
    return 0;
    
}
int delete_at_front(struct node **head)
{
    if(*head == NULL)
    {
        printf("empty linked list\n");
        return 0;
    }
    struct node *temp = *head;
    *head = temp->next;
    printf("deleted element is : %d\n",temp->data);
    free(temp);
    temp = NULL;
return 0;
}
int delete_at_position(struct node **head,int position)
{
    if(*head == NULL)
    {
        printf("empty linked list\n");
        return 0;
    }
    if(position<0)
    {
        printf("enter positive position avlue\n");
        return -1;
    }
    if(position == 0)
    {
         struct node *temp = *head;
         *head = temp->next;
         free(temp);
         temp = NULL;
         return 0;
    }
    struct node *temp = *head;
    struct node *temp2 = NULL;
    for(int i=0;i<(position-1)&&(temp!=NULL);i++)
    {
        temp = temp->next;
    }
    if((temp == NULL)||(temp->next == NULL))
    {
        printf("out of bound index\n");
        return -1;
    }
    temp2 = temp->next;
    printf("deleted element is : %d\n", temp2->data);  
    temp->next = temp->next->next;
    free(temp2);
    temp2 = NULL;
    return 0;
}

int insert_at_end(struct node **head,int value)
{

    struct node *new_node = (struct node*)malloc(sizeof(struct node));
	if(new_node == NULL)
	{
	    printf("memory not allocated for new_node\n");
	    return -1;
	}
	new_node->data = value;
	new_node->next = NULL;
	
	if(*head == NULL)
	{
	    *head=new_node;
	    return 0;
	}
	struct node *temp = *head;
	while(temp->next!=NULL)
	{
	    temp = temp->next;
	}
    temp->next = new_node;

return 0;
}

int main()
{
struct node *head = NULL;


insert_at_end(&head,10);
insert_at_end(&head,20);
insert_at_end(&head,30);
insert_at_end(&head,40);
insert_at_end(&head,50);
display(&head);
//delete_at_front(&head);
//delete_at_position(&head,4);
delete_at_end(&head);
delete_at_end(&head);
delete_at_end(&head);
delete_at_end(&head);
delete_at_end(&head);
display(&head);
free_list(&head);
}

```
# Implement_stack_using_array #

```
//Implement stack using array

#include<stdio.h>
#include<stdlib.h>

#define SIZE 5

int stack[SIZE];
int top =-1;

int is_full()
{
    return(top == SIZE -1);
}

int is_empty()
{
    return(top ==-1);
}

int push(int data)
{
   if(is_full())
   {
       printf("stack is full\n");
       return -1;
   }
   top++;
   stack[top]=data;
   //printf("in push %d %d\n",top,stack[top]);
   return 0;
}
int pop()
{
    if(is_empty())
    {
        printf("stack is empty\n");
        return -1;
    }
    printf("popped element is %d\n",stack[top]);
    top--;
    return 0;
    
}
int peek()
{
    if(is_empty())
    {
        printf("stack is empty\n");
        return -1;
    }
    printf("top element is %d\n",stack[top]);  
    return 0;
}
int display()
{
    if(is_empty())
    {
        printf("stack is empty\n");
        return -1;
    }
    printf("stack elements are :\n");
    for(int i = top;i>=0;i--)
    {
        printf("%d\n",stack[i]);
    }
    return 0;
}
int main()
{
    push(10);
    push(20);
    push(30);
    push(40);
    push(50);
    push(60);
    display();
    peek();
    pop();
    
    return 0;
}

```
# Implement_stack_using_linked_list #
```
//Implement_stack_using_linked_list

#include<stdio.h>
#include<stdlib.h>

struct node{
  int data;
  struct node *next;
    
};
// Push value onto stack (at front of linked list)
int push(struct node **head,int val)
{
    //add at front
    struct node *new_node = (struct node *)malloc(sizeof(struct node));
    if(new_node == NULL)
    {
        printf("memeory not allocated\n");
        return -1;
    }
    new_node->data = val;
    new_node->next = *head;
    *head = new_node;
    return 0;
}
// Pop value from stack (from front)
int pop(struct node **head,int *popvalue)
{
    //remove from front
    if(*head == NULL)
    {
        printf("stack is empty\n");
        return -1;
    }
    struct node *temp = *head;
    *popvalue = temp->data;
    *head = temp->next;
    free(temp);
    temp = NULL;
    return 0;
}
// Display stack elements from top to bottom
int display(struct node *head)
{
    if(head == NULL)
    {
        printf("stack is empty\n");
        return -1;
    }
    struct node *temp = head;
    printf("stack elements : \n");
    while(temp!=NULL)
    {
        printf("%d\n",temp->data);
        temp = temp->next;
    }
    return 0;
}

int free_stack(struct node **head)
{
    if(*head == NULL)
    {
        printf("stack is empty\n");
        return -1;
    }
    struct node *current = *head;
    struct node *temp = NULL;
    while(current!=NULL)
    {
        printf("freed element %d\n",current->data);
        temp = current->next;
        free(current);
        current = temp;
    }
    *head = NULL;
    return 0;
}
int main()
{
    int val;
    int popvalue;
    struct node *head = NULL;
    push(&head,10);
    push(&head,20);
    push(&head,30);
    push(&head,40);
    display(head);
    if (pop(&head, &popvalue) == 0)
        printf("Popped element is: %d\n", popvalue);
    if (pop(&head, &popvalue) == 0)
        printf("Popped element is: %d\n", popvalue);
    if (pop(&head, &popvalue) == 0)
        printf("Popped element is: %d\n", popvalue);
    display(head);
    free_stack(&head);
    
    return 0;
}

```
# Implement_linear_queue_using_array #
```
//Implement_linear_queue_using_array

#include<stdio.h>
#include<stdlib.h>
#define SIZE 5

int queue[SIZE];
int front = -1;
int rear = -1;

int is_empty()
{
    return(front==-1);
}

int is_full()
{
    return(rear==(SIZE-1));
}
int enqueue(int value)
{
    if(is_full())
    {
        printf("queue is full\n");
        return -1;
    }
    if(front == -1 && rear == -1)
    {
        front =0;
        rear =0;
    }
    else
    {
        rear++;
    }
    queue[rear]=value;
    return 0;

}
int dequeue(int *value)
{
    if(is_empty())
    {
        printf("queue is empty\n");
        return -1;
    }

    *value = queue[front];
    front++;
    if(front>rear)
    {
        front = -1;
        rear = -1;
    }
    return 0;
}

int display()
{
    if(is_empty())
    {
        printf("queue is empty\n");
        return 0;
    }
    printf("elements in queue are: \n");
    for(int i = front;i<=rear;i++)
    {
        printf("%d\n",queue[i]);
    }
    return 0;
}

int main()
{
    int value;
    enqueue(10);
    enqueue(20);
    enqueue(30);
    enqueue(40);
    enqueue(50);
    enqueue(60);
    display();
    if(dequeue(&value)==0)
    {
        printf("dequeued element is : %d\n",value);
    }
    
    if(dequeue(&value)==0)
    {
        printf("dequeued element is : %d\n",value);
    }
 
    return 0;
}

```
# Hashing(do later) #

**Theory**

 Let’s first try to understand the importance of hashing using an example
   - Given an array of integers: [1, 2, 1, 3, 2] and we are given some queries: [1, 3, 4, 2, 10]. For each query, we need to find out how many times the number appears in the array. For example, if the query is 1 our answer would be 2, and if the query is 4 the answer will be 0.
   -  Similarly, the following will be the answers to the given queries  
  ![image](https://github.com/user-attachments/assets/e2809d1b-e976-4270-9c02-50b80dc5f9e8)
   - **1) Brute Force approach**
        - As we have learned the ‘for loop’, the first approach that should come to our mind is to use it to solve this problem. For each query, we will iterate over the array using a loop. We will count the number of times the query number appears in that array i.e. increment the counter variable if the array element at that index equals the query number. In terms of function, it will look like the following
     ![image](https://github.com/user-attachments/assets/87ad13ce-97b6-49ea-8e2d-858e7541b909)
        - Now, for each query, we will call the function and it will return the number of times the given query appears in the array.
   - **Time Complexity analysis of the function**
        - We have learned how to compute the time complexity of any code. The above function contains a for loop that runs for N times. So, the time complexity of the function will be **O(N)** ignoring the other constant operations.
        - Now, for each query, we are calling this function. So, if the query contains 5 numbers and we call the function 5 times, the total time complexity will be O(5*N). If the number of queries is Q, the time complexity will be O(Q*N). 

        - Now, if the length of the query becomes large like 105 and the array size also becomes large like 105, the time complexity will be O(1010).

        - We know from our previous knowledge that 108 operations take 1 second to get executed. So, 1010 operations will take around 100 seconds(1010/108). We cannot say a code is good if it takes 100 seconds to get executed.
     
  - **2) Hashing approach**
      - Fast Data Access → Hashing enables **O(1) average time complexity** for searching, making it ideal for real-time applications


