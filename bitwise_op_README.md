# clear bits from left to right position using bitwise operatpors(left and right position inclusive) #

```
//clear bits between left and right position using bitwise operator
#include <stdio.h>

int main() {

int num,left,right;
printf("enter the number\n");
scanf("%d",&num);

printf("enter the right position\n");
scanf("%d",&right);

printf("enter the left position \n");
scanf("%d",&left);


 //This mask will have all ones from left+1 to  31st bit and zeros from 0th to left bit
    unsigned int left_mask = (~0)<< (left + 1);

 //This mask will have all ones from 0th bit to right -1 and zeros from right to 31st bit
    unsigned int right_mask = (1<<right) -1;

//Combine left and right masks
    unsigned int mask = left_mask | right_mask;

//Clear bits in range [left, right]
    unsigned int output = num & mask;

printf("output number %d\n",output);    
    return 0;



}
```

# set bits from left to right position using bitwise operatpors(left and right position inclusive) #

```
//set bits between left and right position using bitwise operator
/*
logic : 
1) (left - right + 1)-> This will give the length of the block we need with all 1's .
2) (1U << (left - right + 1))-> this will give a "point" before which all bits will be 1 after doing "-1"
3) (1U << (left - right + 1))-1 -> this will make allthe bits before "point" as 1 and "point"bit =0;
4) now you got the band of 1's with the length you need .
5) shift the band leftside with "right" value
*/
#include <stdio.h>

int main() {

int num,left,right;
printf("enter the number\n");
scanf("%d",&num);

printf("enter the right position\n");
scanf("%d",&right);

printf("enter the left position \n");
scanf("%d",&left);


//Combine left and right masks
    unsigned int mask = ((1<<((left-right)+1))-1)<<right;

//Clear bits in range [left, right]
    unsigned int output = num | mask;

printf("output number %d\n",output);    
    return 0;



}

```

# swap even and odd bits of num using bitwise #

```
logic:

Mask out even bits → using 0xAAAAAAAA

In binary (32-bit): 101010...10

This picks up bits at odd positions (since we start from LSB=0).

Mask out odd bits → using 0x55555555

In binary: 010101...01

This picks up bits at even positions.

Shift them:

Right shift odd-positioned bits → even_bits >> 1

Left shift even-positioned bits → odd_bits << 1

Combine (OR) → final swapped number.


int main() {
    unsigned int num;
    printf("Enter a number: ");
    scanf("%u", &num);

    unsigned int mask_even_bits = num & 0xAAAAAAAA; // mask even bits and get the odd position bits
    unsigned int mask_odd_bits  = num & 0x55555555; // mask odd bits and get the even position bits

    mask_even_bits >>= 1; // shift odd-positioned bits to even
    mask_odd_bits  <<= 1; // shift even-positioned bits to odd

    result = mask_even_bits | mask_odd_bits ;
    printf("After swapping even and odd bits: %u\n", result);

    return 0;
}
```
