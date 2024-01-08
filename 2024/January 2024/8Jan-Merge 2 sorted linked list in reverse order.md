## [Merge 2 sorted linked list in reverse order](https://www.geeksforgeeks.org/problems/merge-2-sorted-linked-list-in-reverse-order/1)

#### Code 1 : giving TlE
```
class GfG
{
    Node mergeResult(Node node1, Node node2)
    {
	     Node newHead=new Node(0);
	     Node tail = newHead;
	 
   //both have ele
	 while(node1!=null && node2!=null){
	     if(node1.data<node2.data){
	         tail.next=node1;
	         node1=node1.next;
	         tail=tail.next;
	     }
    }
    
    //only 1st have ele
    while(node1!=null){
        tail.next=node1;
        node1=node1.next;
        tail=tail.next;
    }
    
    //only 2nd have ele
    while(node2!=null){
        tail.next=node2;
        node2=node2.next;
        tail=tail.next;
    }
    return reverse(newHead.next);
    }  
    
    Node reverse(Node head){
        Node prev=null;
        Node curr=head;
        while(curr!=null){
            Node nxt=curr.next;
            curr.next=prev;
            prev=curr;
            curr=nxt;
        }
        return prev;
    }
}
```

#### code 2:
```
class GfG
{
    Node mergeResult(Node node1, Node node2)
    {
	     Node newHead=new Node(0);
	     Node tail = newHead;

      while(true){
          if(node1==null){
              tail.next=node2;
              // node1=node1.next;
              break;
          }
          if(node2==null){
              tail.next=node1;
              break;
          }
          if(node1.data<node2.data){
              tail.next=node1;
              node1=node1.next;
          }else{
              tail.next=node2;
              node2=node2.next;
          }
          tail=tail.next;
      }
      return reverse(newHead.next);
      }  

    Node reverse(Node head){
        Node prev=null;
        Node curr=head;
        while(curr!=null){
            Node nxt=curr.next;
            curr.next=prev;
            prev=curr;
            curr=nxt;
        }
        return prev;
    }
}
```

#### `TC` O(N+M)
#### `SC` O(1)


### Approach

1. Merge two sorted list <br/>
    a.both have ele <br/>
    b.node1 is empty <br/>
    c.node2 is empty <br/>
   
3. reverse merged list
