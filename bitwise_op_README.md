# clear bits from m to n position using bitwise operatpors(left and right position inclusive) #

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

# clear bits from left to right position using bitwise operatpors(left and right position inclusive) #

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
