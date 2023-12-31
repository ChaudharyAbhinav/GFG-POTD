
//Array Pair Sum Divisibility Problem

//Link : https://www.geeksforgeeks.org/problems/array-pair-sum-divisibility-problem3257/1


```
class Solution {
    public boolean canPair(int[] nums, int k) {
        // Code here
        if(nums.length%2!=0)return false;
        
        HashMap<Integer,Integer> hm=new HashMap<>();
        
        for(int i=0;i<nums.length;i++){
            int rem=k-(nums[i]%k);
            if(hm.containsKey(rem)){
                if(hm.get(rem)==1){
                    hm.remove(rem);
                }else{
                    hm.put(rem,hm.get(rem)-1);
                }
            }else{
                hm.put(nums[i]%k,hm.getOrDefault(nums[i]%k,0)+1);
            }
        }
        
        if(hm.size()==0 || (hm.size()==1 && hm.containsKey(0))) return true;
        else return false;
    }
}                     


// alternate solution
class Solution2 {
    
    public boolean canPair(int[] nums, int k) {
    
        HashMap<Integer,Integer>map=new HashMap<>();
    
        for(int num:nums){
            int rem=num%k;
            map.put(rem,map.getOrDefault(rem,0)+1);
        }

        for(int key:map.keySet()){
            if(key==0){
                if(map.get(key)%2!=0)
                  return false;
            }
            else
            {
                if(!map.containsKey(k-key)||map.get(key)!=map.get(k-key)){
                    return false;
                }
            }
        }

        return true;

    }
}


```