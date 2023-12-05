### To implement a basic linked list (using a static array to allocate it) and display it :

```C++
#include <bits/stdc++.h>
using namespace std;

  

struct Node
{
    int data;
    struct Node *next;
} *first = NULL;

void display(struct Node *p)
{
    while (p != NULL)
    {
        cout << (p->data) << " ";
        p = p->next;
    }
}

void create(int A[], int n)

{
    int i;
    struct Node *t, *last;
    first = new Node;
    first->data = A[0];
    first->next = NULL;
    last = first;
  
    for (i = 1; i < n; i++)
    {
        t = new Node;
        t->data = A[i];
        t->next = NULL;
        last->next = t;
        last = t;
    }
}

int main()
{
    int A[] = {3, 5, 7, 10, 15};
    create(A, 5);
    display(first);
    return 0;
}
```

Note : the display and Create functions are important. Also the way the node structure is made. To use this with continuous input, just input and store in an array or use other methods.

### Recursive Display Function:

```C++
void display(struct Node *p)
{
    while (p != NULL)
    {
        cout << (p->data) << " ";
        display(p->next);
    }
}
```

Note : In the recursive display function, if we reverse the order of print and call, we can print the linked list in reverse. The below code shows just that.

```C++
void display(struct Node *p)
{
    while (p != NULL)
    {
        display(p->next);
        cout << (p->data) << " ";
    }
}
```

Traversal take O(n).

### Counting number of nodes in linked list.

```C++
int count(struct Node* p)
{
    int count = 0;
    while(p!=0)
    {
        count++;
        p=p->next;
    }
    return count;
}
```

Since in this too, one traversal of the linked list is required, so the time complexity is O(n). 

### count nodes in recursive method:

```C++
int Recursive_count(struct Node *p)
{
    int count=0;
    if(p==0)     //base case
    {
        return 0;
    }
    else
        return Recursive_count(p->next) + 1;  //recursive call.
}
```

In similar fashion, we can code the functions for finding sum of elements or maximum element out of the linked list.


### Searching in a linked list:

In linked list, we cannot directly get to the middle without traversing, unlike array. So, binary search becomes unpractical. Instead we use linear search.

In linear search, basically check if the t->data == key  print true or false.

A good linear search on linked list :

```C++
Node* search(Node* p, int key)
{
	Node* q = NULL;
	while(p!=Null)
	{
		if(key==p->data)
		{
			q->next = p->next;
			p->next = first;
		}
		q=p;
		p=p->next;
	}
}
```

### Insert new node:

insert x at position index in the linked list.
```C++ 
void Insert(struct node *p, int index, int x)
{   
	struct Node *t;
	if(index<0 || index>count(p))    //invalid insertion
		return 0;

	t=new Node;
	t->data = x;

	if(index == 0)
	{
		t->next=first;
		first = t;
	}
	else
	{
		for(i = 0; i<index-1; i++)
		{
			p=p->next;
		}
		t->next = p->next;
		p->next=t;
	}
}
```

#### Note : 
we can create a full linked list by inserting elements one by one at the last of the linked list. For doing this, traverse the list once and then take a pointer last at the last node and attach the new node to the last pointer. 
If called in a loop, while constantly inputting values, we can have this as the most elegant way to create the linked list.

This method : 
* First pointer is created(head), two other tracking pointers are created, namely first and last.  then both are made to point to the first one, as there is nothing else to point to.
* Then to add a new element insert is called on the last pointer, and it links the new node to the head. and last pointer is moved on to the newly inserted node.
* The only corner case is, to code the if statement separately for when the linked list is empty and the head itself has to be created.

PS : the first pointer will be global pointer (no issues), but to find the last pointer traverse it once and find the last pointer, or just make a function for it.

```C++

void insertLast(int x)
{
    Node *t = new Node;
    t->data = x;
    t->next = NULL; // new node is ready.

    if (first == NULL)
        first = last = t;

    else
    {
        last->next = t;
        last = t;
    }
}

```

### Inserting new node in sorted linked list :

Traverse the list with x(value to be inserted)and also two pointers : p and q(p is the pointer which finds the place of insertion, q is following p from one node behind and will be used to link the inserted node easily).
and find a place where x is smaller then the value in the list, then just link it using the p and q pointers, we need to insert in between p and q. so
q->next = t;
t->next = p;
and that's it, the linking is done.

```C++
void SortedInsert(int x)
{
    Node *t = new Node;
    t->data = x;
  
    Node *p = first;
    Node *q = NULL;

    while (p && p->data < x)
    {
        q = p;
        p = p->next;
    }
    t = new Node;
    t->data = x;
    t->next = q->next;
    q->next = t;
}
```

### Deleting a node from a linked list :

Has 2 major things:
* Deleting the first nide itself (replacing the head).
* Deleting other nodes.

```C++
void Delete(struct Node *p, int index)
{
    struct Node *q;
    int x = -1, i;
  
    if(index<1 || index>count(p)
        return -1;
    if(index==1)
    {
        q = first;
        x = first->data;
        first = first->next;
        delete q;
        return x;
    }
    else
    {
        for (i = 0; i < index - 1; i++)
        {
            q = p;
            p = p->next;
        }
        q->next = p->next;
        x = p->data;
        delete p;
    }
}
```

### Reversing the Linked list :

Two methods :
* Reversing the data elements.:
	* In this, we copy the elements in a temporary array and then copy them back to the linked list by accessing the array in reverse.
	* O(2n).

* Reversing the links of the linked list.(reversing using sliding pointers)
	* Take three sliding pointers : p, q, r.
	* p=first; q=NULL; r=NULL; (q behind p and r behind q).
	* while p is not null --- r=q; q=p; p=p->next; q->next = r; 
	* outside while - first=q;

Note; We use the sliding pointers method preferably, due to its ease of scaling and more elegant method.

### Concatenation of two linked lists:

```C++
// we have first, head of first LL.
// we have second, head of second LL.
  
void concat(first, second)
{
    Node* p =first;
    while(p->next!=NULL)
    {
        p=p->next;
    }
    p->next = second;
}
```

### Merging 2 sorted lists to one sorted list:

Process :
* Create a third linked list, take third as its head and last as its tail.
* then check which is smaller in the heads of the two.
* bring third and last both at that place.
* then check which is smaller and put third there and rearrange the links.

```C++
void Merge(struct Node *p, struct Node *q)
{
    struct Node *last;
    if (p->data < q->data)
    {
        third = last = p;
        p = p->next;
        third->next = NULL;
    }
    else
    {
        third = last = q;
        q = q->next;
        third->next = NULL;
    }
    while (p && q)
    {
        if (p->data < q->data)
        {
            last->next = p;
            last = p;
            p = p->next;
            last->next = NULL;
        }
        else
        {
            last->next = q;
            last = q;
            q = q->next;
            last->next = NULL;
        }
    }
    if (p)
        last->next = p;
    if (q)
        last->next = q;
}
```

### Check for Loop in LL:

```C++
int isLoop(struct Node *f) 
{ 
	struct Node *p,*q; 
	p=q=f; 
	do 
	{ 
		p=p->next; 
		q=q->next; 
		q=q?q->next:q; 
	}while(p && q && p!=q); 
	if(p==q) 
		return 1; 
	else 
		return 0; 
}
```

[[Circular Linked List]]
[[Doubly Linked List]]
[[Circular Doubly linked list]]