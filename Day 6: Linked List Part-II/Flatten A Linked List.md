```java
/****************************************************************

       Following is the class structure of the Node class:

       class Node {
	int data;
	Node next;
	Node child;

	public Node(int data) {
		this.data = data;
		this.next = null;
		this.child = null;
	}
}

*****************************************************************/
/*
Merge the last 2 LL into 1 in each iteration using comparison method till theer is only 1 left
*/
public class Solution {
	public static Node merge(Node a,Node b){
		Node temp=new Node(0);
		Node res=temp;
		
		while(a!=null && b!=null){
			if(a.data<b.data){
				temp.child=a;
				temp=temp.child;
				a=a.child;
			}else{
				temp.child=b;
				temp=temp.child;
				b=b.child;
			}
		}
		
		if(a!=null)	temp.child=a;	//if a is not null put the remaining LL in bottom
		else	temp.child=b;	//else put the remaining LL of b in bottom
		
		return res.child;
	} 
	public static Node flattenLinkedList(Node root) {
		if(root==null || root.next==null)	return root;
		
		//start merging from last 2 LL
		root.next=flattenLinkedList(root.next);
		root=merge(root,root.next);
		
		return root;
	}
}
```
