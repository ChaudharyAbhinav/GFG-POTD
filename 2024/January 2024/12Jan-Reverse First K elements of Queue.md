## [https://www.geeksforgeeks.org/problems/reverse-first-k-elements-of-queue/1](Reverse First K elements of Queue)

```java
class GfG {
    // Function to reverse first k elements of a queue.
    public Queue<Integer> modifyQueue(Queue<Integer> q, int k) {
        // add code here.
        
        Stack<Integer> helper=new Stack<>();
        
        for(int i=0;i<k;i++){
            helper.push(q.remove());
        }
        
        while(!helper.isEmpty()){
            q.add(helper.pop());
        }
        
        for(int i=0;i<q.size()-k;i++){
            q.add(q.remove());
        }
        return q;
    }
}
```

#### `TC` O(n)
#### `SC` O(k)
