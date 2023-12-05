In this architecture,  every linked list has a link to both the next and the previous node

### Differences with Regular Linked List - 

* Regular Linked list -
> ![[Doubly Linked List 2023-08-14 21.02.50.excalidraw]]
* Doubly linked list - 
> ![[Doubly Linked List 2023-08-14 21.04.55.excalidraw]]
-> Can be traversed Bidirectionally.
-> Takes more memory (1.5x more).
-> Node structure
	![[Doubly Linked List 2023-08-14 21.16.51.excalidraw]]

### Node Struct -
```cpp
struct Node
{
	struct Node* prev;
	int data;
	struct Node* next;
};
```

### Create function from a static array passed as parameter - 

```cpp
void create(int A[], int n)
{
    struct Node *t, *last;
    int i;
    
    first = new Node;
    first->data = A[0];
    first->prev = first->next = NULL;
    last = first;

    for (i = 1; i < n; i++)
    {
        t = new Node;
        t->data = A[i];
        t->next = last->next;
        t->prev = last;
        last->next = t;
        last = t;
    }
}
```

### Display function - 

```cpp
void Display(struct Node *p)
{
    while (p)
    {
        cout << (p->data);
        p = p->next;
    }
    cout << endl;
}
```

### Length function - 

```cpp
int Length(struct Node *p)
{
    int len = 0;
    while (p)
    {
        len++;
        p = p->next;
    }
    return len;
}
```

### Insert in a doubly LL -

Two major cases - 
* Insert before first node.
* insert at any given index.

```cpp
void Insert(struct Node *p, int index, int x)
{
    struct Node *t;
    int i;
    
    if(index<0 || index>Length(p))
    {
        return;
    }
    if(index==0)
    {
        t=new Node;
        t->data = x;
        t->prev=NULL;
        t->next=first;
        first->prev=t;
        first=t;
    }
    
    else
    {
        for(i=0; i<index-1; i++)
            p=p->next;
        t=new Node;
        t->data=x;

        t->prev=p;
        t->next=p->next;
        if(p->next)
        {
            p->next->prev=t;
        }
        p->next=t;
    }
}
```

### Delete node -

```cpp
void Delete(struct Node *p, int index)
{
    struct Node *q;
    int x=-1, i;

    if(index<1 || index>length(p))
        return -1;
    if(index==1)
    {
        first=first->next;
        if(first)first->prev=NULL;

        x=p->data;
        free(p);
    }
    else{
        for(i=0; i<index-1; i++)
            p=p->next;
            
        p->prev->next=p->next;
        if(p->next)
            p->next->prev=p->prev;
        x=p->data;
        free(p);    
    }

}
```

### Reverse a doubly linked list - 

```cpp
void Reverse(struct Node *p)
{
    struct Node *temp;
    
    while(p!=NULL)
    {
        temp=p->next;
        p->next=p->prev;
        p->prev=temp;
        p=p->prev;
        if(p->next==NULL)
            first=p;
    }
}
```

