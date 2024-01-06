### [05Jan-Count possible ways to construct buildings](https://www.geeksforgeeks.org/problems/count-possible-ways-to-construct-buildings5007/1)

```
class Solution
{
    public int TotalWays(int N)
    {
       long mod = 1000000007;
        if(N==1){
            return 4;
        }
        long first = 1;
        long second = 1;
        long prev_f = 0,prev_s = 0;
        for(int i=2;i<=N;i++){//normal fibonacci
            prev_f = second;
            second = (first + second)%mod ;
            
            first = prev_f;
            prev_s = second;
        }
        long ans =  ((prev_f + prev_s));
        return (int)((ans*ans)%mod);
    }
}
```

`TC:` O(n)
`SC:` O(n)

