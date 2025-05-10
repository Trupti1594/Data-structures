# link #


# 383. Ransom Note #
https://leetcode.com/problems/ransom-note/?envType=study-plan-v2&envId=top-interview-150
  - few test case are not getting passed try WITHOUT HASHING in free time
    
** WITHOUT HASHING ** 

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
