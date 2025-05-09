# link #


# 383. Ransom Note #

  - All 3 testcase got passed
    
```
bool canConstruct(char* ransomNote, char* magazine) 
{
    int i=0,j=0,count=0,index=-1;
    while(*(ransomNote+i)!='\0')
    {
        if(index==j)
        {
            j++;
        }
        
        else
        {
            j=0;
        }
        while(*(magazine+j)!='\0')
        {
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
