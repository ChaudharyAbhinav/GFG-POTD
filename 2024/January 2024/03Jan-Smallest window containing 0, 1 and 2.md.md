### [Smallest window containing 0, 1 and 2](https://www.geeksforgeeks.org/problems/smallest-window-containing-0-1-and-2--170637/1)

```
class Solution {
    public int smallestSubstring(String S) {
        // Code here
        
        int zero=-1,one=-1,two=-1;
        int ans=Integer.MAX_VALUE;
        
        for(int i=0;i<S.length();i++){
            if(S.charAt(i)=='0') zero=i;
            else if(S.charAt(i)=='1') one =i;
            else two =i;
            
            if(one!=-1 && two!=-1 && zero!=-1){
                ans = Math.min(ans,i+1-Math.min(zero,Math.min(one,two)));
            }
        }
        if(ans==Integer.MAX_VALUE) return -1;
        return ans;
    }
};
```