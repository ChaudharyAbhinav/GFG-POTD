### [Largest Sum Subarray of Size at least K](https://www.geeksforgeeks.org/problems/largest-sum-subarray-of-size-at-least-k3121/1)

```
class Solution {
    
    public long maxSumWithK(long a[], long n, long k)
    {
        int N = (int)n;
        int K=(int)k;
        long maxSum[] = new long[N];
        maxSum[0] = a[0];
        long curr_sum= a[0];
        for(int i=1;i<N;i++){
            curr_sum= Math.max(a[i],a[i]+curr_sum);
            maxSum[i]=curr_sum;
        }
        long ans=0,sum=0;
        for(int i=0;i<K;i++){
            sum +=a[i];
        }
        ans=sum;
        for(int i=K;i<N;i++){
            sum += a[i] - a[i-K];
            ans = Math.max(ans,sum);
            ans= Math.max(ans,sum+maxSum[i-K]);
        }
        return ans;
    }
}
```