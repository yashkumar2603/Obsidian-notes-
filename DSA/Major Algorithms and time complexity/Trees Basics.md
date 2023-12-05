#### Basic architecture of trees  - 

> ![[Trees Basics 2023-08-14 23.52.17.excalidraw]]

### Number of binary trees possible from n nodes:

* Draw all possible connection shapes, mirror images are counted as separate.
* For Example, for n=3 number of nodes: 
> ![[Trees Basics 2023-08-15 13.50.49.excalidraw]]
*  Similarly, we can make for any number of nodes.
* Maximum height of tree created from n nodes is given by:
	* $$2^{n-1}$$
* No. of tree setups for n number of nodes is given by(Combinatorics formula)
	* $$\frac{{2n \choose n}}{n+1}$$
* The above formula is known as Catalan number.
Also, Catalan Number can be written as,(Recursive formula)
$$ T(n) = \sum_{i=1}^n T(i-1)T(n-i) $$

##### Binary tree :
no node has >2 child. 
##### N-ary tree:
any node has any number of child.

 We have the pointer to the tree root, it has the pointers to its children and then they have pointrs to their children and so on.

## Struct / Class used to make the tree data structure nodes :

We will use a vector to store the addresses of the children of any node.

We don't use and array  or a linked list because 
* Array has an issue of static size while declaring, while we want to keep creating new nodes in runtime and all.
* In linked list, to access the nodes after cretion we will have to traverse the whole list to reach to the desired address, which is computationally expensive.

So, we need vector<TreeNode * >

And, we make a file with only the class TreeNode and then include it wherever i want. 
We do this by not making a .cpp file, but rather a .h file (header file).
The header file has the following code in it.

```cpp
#include <vector>
using namespace std;

template <typename T>

class TreeNode {
    public:
    T data;
    vector<TreeNode*> children;

	// making a constructor to save lines of code in the .cpp file.
    TreeNode(T data)
    {
        this->data = data;
    }
}
```

Now, in general case we need too declare the type of variable in the vector, but here it is not needed. So now, if the data is of int, the vector will use the int pointer type by default.
Basically the vector assumes the same datatype as that of T.  

#### Creating a tree manually - 
```cpp
int main()
{
    TreeNode<int> *root = new TreeNode<int>(1);
    TreeNode<int> *node1 = new TreeNode<int>(2);
    TreeNode<int> *node2 = new TreeNode<int>(3);
    root->children.push_back(node1);
    root->children.push_back(node2);
    return 0;
}
```

#### Printing a tree once created - 

*So, to print a tree after its creation, we take the root and then all the branches coming out of it are taken as being roots for their own small sub-trees and then we can use recursion to easily access and traverse the tree.*

```cpp
void printTree(TreeNode<int> *root)
{
    if(root == NULL) {    //edge case, tree empty.
        return;
    }
    cout << root->data << ":";                    
    for (int i = 0; i < root->children.size(); i++)
    {
        cout<<root->children[i]->data << ",";
    }
    cout<<endl;
    for(int i=0; i<root->children.size(); i++)
    {
        printTree(root->children[i]);
    }
}
```

### Function for taking input from user -

```cpp
TreeNode<int>* takeInput() {
    int rootData;
    cout << "Enter data" << endl;
    cin >> rootData;
    TreeNode<int>* root = new TreeNode<int>(rootData);
    int n;
    cout << "Enter num of children of " << rootData << endl;
    cin >> n;
    for(int i=0; i<n; i++){
        TreeNode<int>* child = takeInput();
        root->children.push_back(child);
    }
    return root;
}
```

## Take input level wise - 

What we want to do is take input of 1 level at a time rather than going by the childrens of the nodes one by one.

*To achieve this we will use a queue, we will keep all the elements in a queue, using the inbuilt queue. We will be keeping the pointer to all the nodes we have in the queue.*

**We get the data and make the node and then add the node to the queue and then we find the front of the queue after adding all the children nodes to the queue (and adding the children nodes to the parent's child list). Then the new front is the first child of the parent, now we take  the input of all the children of the first child through the for loop and remove the first child from the queue. Now take input for the children of the second child, and so on. Hence we manage to take the input in a level-wise fashion.**

```C++
TreeNode<int> *takeInputLevelWise()
{
    int rootData;
    cout << "Enter the root data" << endl;
    cin >> rootData;                  // Get the root data
    TreeNode<int> *root = new TreeNode<int>(rootData); // Put root data into newly created root node.

    queue<TreeNode<int> *> pendingNodes; // declare the queue.
    
    pendingNodes.push(root);    // push the root in the queue.
    
    while (pendingNodes.size() != 0) // continue till the pendingNodes queue becomes empty.
    {
        TreeNode<int> *front = pendingNodes.front(); // Get the front node pointer by getting the front elemnt of the queue
        
        pendingNodes.pop();                          // Pop the element already taken in the front node for tree.
        
        cout << "Enter number of children of " << front->data << endl;
        int numChild;
        cin >> numChild; // Take input about the number of children.
        for (int i = 0; i < numChild; i++)
        {
            int childData;
            cout << "Enter" << i << "th child of " << front->data << endl;
            cin >> childData;
            TreeNode<int> *child = new TreeNode<int>(childData); // Create the child node.
            front->children.push_back(&child);                   // Push the child node in the parent child list.
            pendingNodes.push(child);    
        }
    }
}
```

### Count no. of nodes - 

Count the number of nodes for the head and Use recursion for the rest subtrees.

```C++
int numNodes(TreeNode<int>* root)
{
    int ans = 1;
    for(int i = 0; i< root->children.size(); i++)
    {
        ans += numNodes(root -> children[i]);   //Recursive call to get the number of nodes on the subtrees.
    }
    reurn ans;
}
```

## Height of a tree - 

**Could not Solve, come back to this.**
**Solution not given**.

## Depth of node - 

it is defined as the distance of a node from the root of the tree.

This too will be done using recursion. 

### Find the number of leaf nodes - 

The leaf nodes are those which dont have any childs after them.

```C++
int LeafNodes(TreeNode<int> *root)
{
    int counter = 0;
    if (root != NULL)
    {
        if (root->children.size() == 0)
        {
            counter++;
        }
        for (int i = 0; i < root->children.size(); i++)
        {
            LeafNodes(root->children[i]);
        }
    }
    return counter;
}
```

> **Code written by me, not in the course.**


### PostOrder Traversal - 

First Print the children of a node and then print its parent, this leads to the main root being printed last.

## Delete a created tree - 

We cannot directly delete the root, then we will lose access to all its children, so we need to first delete the deepest child first and then delete the root after all the children are gone.

```C++
void deleteTree(TreeNode<int>* root)
{
	for(int i=0; i<root->children.size(); i++)
	{
		deleteTree(root->children[i]);
	}
	delete root;
}
```

[[Binary Trees -]]
