## [Find element occuring once when all other are present thrice](https://www.geeksforgeeks.org/problems/find-element-occuring-once-when-all-other-are-present-thrice/1)


```
class Solution {
    static int singleElement(int[] arr , int N) {
        // code here\
        
        int tn=-1,tn1=0,tn2=0;
        
        
        for(int i=0;i<N;i++){
            int ctn = tn & arr[i];
            int ctn1=tn1&arr[i];
            int ctn2=tn2&arr[i];
            
            tn = tn &(~ctn);
            tn1 = tn1&(~ctn1);
            tn2 = tn2&(~ctn2);
            
            
            tn = tn | ctn2;
            tn1=tn1| ctn;
            tn2=tn2| ctn1;
            
        }
        return tn1;
      
    }
}
```