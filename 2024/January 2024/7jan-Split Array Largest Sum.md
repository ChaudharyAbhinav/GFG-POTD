### [07Jan-Split Array Largest Sum](https://www.geeksforgeeks.org/problems/split-array-largest-sum--141634/1)

```

class Solution {
    static int splitArray(int[] arr , int N, int K) {
        // code here
        
        int low=Arrays.stream(arr).max().getAsInt();
        int high=Arrays.stream(arr).sum();
        int ans=0;
        while(low<=high){
            int mid=low+(high-low)/2;
            
            if(helper(mid,arr,K))
            {
                ans=mid;
                high=mid-1;
                //  high =mid;
            }else{
                low=mid+1;
            }
        }
        return ans;
    }
    
    
    static boolean helper(int mid,int[] arr,int K){
        
        int count=1;
        int sum=0;
        for(int i=0;i<arr.length;i++){
             sum +=arr[i];
            if(sum>mid){
                sum =arr[i];
                count++;                
            }
        }
        
        return count<=K;
        
    }

};
```

`TC:` O(nlogn)
`SC:` O(1)

