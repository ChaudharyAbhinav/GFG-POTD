## (Search Pattern (KMP-Algorithm))[]

```Java
class Solution
{
    ArrayList<Integer> search(String pat, String txt)
    {
        // your code here
        ArrayList<Integer> ans= new ArrayList<>();
        int patlen=pat.length();
        int txtlen=txt.length();
        int lps[]= ComputeLPS(pat);
        
        int i=0,j=0;
        
        while(i<txtlen){
            if(txt.charAt(i)==pat.charAt(j)){
                i+=1;j++;
            if(j==patlen){
                ans.add(i-j+1);
                j=lps[j-1];
            }
            }
            else if(pat.charAt(j)!=txt.charAt(i) && i<txtlen){
                if(j==0){
                    i++;
                }else{
                    j =lps[j-1];
                }
            }
        }
        if (ans.isEmpty()) {
            ans.add(-1);   
        }
        return ans;
    }
    
    public int[] ComputeLPS(String S){
                int[] lps= new int[S.length()];
        lps[0]=0;
        int i=0,j=1;
        while(j<S.length()){
            if(S.charAt(i)==S.charAt(j)){
                i++;
                lps[j]=i;
              j++;
            }else{
                if(i==0){
                    lps[j]=0;
                    j++;
                }else{
                    i=lps[i-1];
                }
            }
    }
    return lps;

}

}
```

#### `TC` : O(text) <br/>
#### `SC` : O(text)