___
### **Arrays**

- Simplest form of data structure
- Consists of a same data type series
- Data is stored in consecutive memory addresses
- Complexity : $0(1)$
- Don't work very well with dynamic data
- Time seeking complexity : $0(n)$


### **Dynamic Arrays**

- More complex data structure than simple arrays
- Their size can be altered in runtime
- Access to data via index
- Seeking Complexity $0(1)$
- Data Insert Complexity (Worst Case Scenario) $0(n)$
- Data Insert Complexity (Amortized) $0(1)$


---
### Linked List

- Used to store consecutive data
- They are **NOT** stored in consecutive memory addresses
- Data is connected via indexes
- First node is named **Head**
- Last node is named __Tail__ (equals to **NULL**)
- Each node is tied to an index


### Supported Commands For Linked Lists

- $first()$ - returns the index from the first node
- $last()$ - return index from the last node
- $insertAfter(p,e)$ - inserts a new node with data $e$ after node $p$
- $insertBefore(p,e)$ - inserts a new node with data $e$ before node $p$
- $remove(p)$ - removes a node related with $p$ (for example the next node)
- Every command is of complexity $0(1)$


---
### Create A Node Inside Java

```java
public class SNode {
	private SNode next;         // Index for the next node
	private Object element;     // Stored Data
}
```


---
### Create A Linked List Inside Java

``` java
public class SinglyNodeList{
	protected int nofElements     // Amount of nodes
	protected SNode head, tail;   // Head & Tail
}

// Constructor
public SinglyNodeList() {
	nofElements = 0;
	head = null;
	tail = null;
}
```


___
### Insert a node after another node (with last node exception)

``` java
public SNode insertAfter(SNode, p , Object element){
	if (p == null){
		System.out.println("p is null");
		return null;
	}
	
	nofElemenbts++;
	
	SNode q = new SNode(p.getNext(), element);
	if (p.getNext() == null){          // Insert data as the last on the list
		tail = q;                     // Since returns that next one is "Head"
	}
	p.setNext(q);
	return q;
}
```


---
### Insert a Head Node

``` java
public SNode insertFirst(Object element){
	nofElements++;
	SNode q = new SNode(head, element);
	head = q
	if (nofElements == 1){          // The List Has The First Node
		tail = head;
	}
	return q;
}
```


---
### Delete a node after another node

``` java
public Object removeAfter(SNode p){
	if (p == tail){
		System.out.println("You're already at the end");
		return null;
	}
	
	nofElements--:
	
	SNode pNext = p.getNext();          // The next node that we will delete
	p.setNext(pNext.getNext());
	Object pElem = pNext.getElement();  // The element of the node we will delete
	if (pNext == tail){                 // If the tail has been deleted
		tail = p;                       // We update the tail
	}
	
	pNext.setNext(null);
	return pElem;
}
```


---
### List Merge

Steps : 
- Merge of the list $z$ and the list $s$ in a way that the nodes from $z$ go first in front of $s$
- if $z$ is empty then it it inherits the nodes from $s$
- the tail of $z$ becomes the tail of $s$
- We update the size of $z$

``` java
public void cetenate(SInglyNodeList s){
	if (s.isEmpty())
	{
		return;
	}
	
	if (tail == null){
		tail = s.first()
	}
	else {
		tail.setNext(s.first());
	}
	
	if (isEmpty()){
		head = tail;
	}
	
	tail = s.last();
	nofElements += s.size();
}
```


---
#### List vs Array

- List is a dynamic data structure
- Lists require more memory (to store indexes)
- Reorganization is not required upon changes (since data is not stored in consecutive memory addresses)
- Lists cannot be accessed directly
- We cannot access previous nodes (without an extra index)
- It requires more time to seek nodes since they are not stored consecutively


---
#### Double Linked Lists

- Each node has an index for the previous and for the next node
- It has an extra index for the previous node (compared the the simple list)
- The first and last node have no data

---
#### Node - Double Linked List in Java

``` java
public class DNode {
	private DNode prev, next; // Previous & Aftet Nodes
	private Object element; // The stored data
}

// Constructor
public DNode(DNode nodePrev, DNode nodeNext, Object nodeElement) {
	prev = nodePrev;
	next = nodeNext;
	element = nodeElement;
}
```


___
#### Double Linked List in Java

``` java
public class DoublyNodeList {
	protected int nofElements;
	protected DNode head, tail;

	
	public DoubleNodeList() {
		nofElements = 0;
		head = new DNode(null, null, null);
		tail = new DNode(null, null, null);
		head.setNext(tail); // We show the tail when initiating a new Double Linked List
	}
}
```


___
