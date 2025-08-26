# clear bits from m to n position using bitwise operatpors #

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
