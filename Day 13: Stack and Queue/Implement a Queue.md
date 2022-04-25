```java
public class Queue {
	int arr[];
	int front;
	int rear;
	int count;
    Queue() {
        arr=new int[5000];
		front=0;
		rear=0;
		count=0;
    }

    /*----------------- Public Functions of Queue -----------------*/

    boolean isEmpty() {
        return count==0 ? true : false;
    }

    void enqueue(int data) {
        arr[rear++]=data;
		count++;
    }

    int dequeue() {
		if(count>0){
			count--;
			return arr[front++];
		} 
		return -1;
    }

    int front() {
        return count>0 ? arr[front] : -1; 
    }

}
```
