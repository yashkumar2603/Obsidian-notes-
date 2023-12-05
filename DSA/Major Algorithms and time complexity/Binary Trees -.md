A binary tree is made from nodes which have either o, 1 or 2 children. 
So, the generl binary tree node class is - 

```C++
template <typename T>  //used so that we can input all datatypes in the tree.

class BinaryTreeNode
{
    public:
    T data;
    BinaryTreeNode* Left;
    BinaryTreeNode* right;

    BinaryTreeNode(T data){         //Constructor function
        this->data = data;
        left = NULL;
        right = NULL;
    }

    ~BinaryTreeNode() {            //destructor function
        delete left;                //even if the
        delete right;
    }
}
```

## Basic manual node create and print - 

```C++
#include <iostream>
#include "BinaryTreeNode.h"
using namespace std;

int main()
{
    BinaryTreeNode<int> *root = new BinaryTreeNode<int>(1);
    BinaryTreeNode<int> *Node1 = new BinaryTreeNode<int>(2);
    BinaryTreeNode<int> *Node2 = new BinaryTreeNode<int>(3);
    root->left = Node1;
    root->right = Node2;

    cout << root->data << endl;
    cout << root->left->data << endl;
    cout << root->right->data << endl;
}
```

## Wanted Output from print function -

root : L left_child , R right_child

recursive application will print without all this.

so we will use this - 
```C++
void printTree(BinaryTreeNode<int> *root)
{
    if (root == NULL)
    {
        return;
    }
    cout << root->data << ":";
    if (root->left)  //not null
    {
        cout << "L" << root->left->data;
    }

    if (root->right)
    {
        cout << "R" << root->right->data;
    }
    cout << endl;
    printTree(root->left);
    printTree(root->right);
}
```

## Now creating the  Input Function - 

```C++
BinaryTreeNode<int>* takeInput()
{
    int rootData;
    cout<< "Enter Data" <<endl;
    cin>>rootData;
    if (rootData == -1)
    { 
// input -1 means the node is empty.(no data)
        return NULL;
    }

    BinaryTreeNode<int>* root = new BinaryTreeNode<int>(rootData);
    BinaryTreeNode<int>* leftChild = takeInput(); 
    BinaryTreeNode<int>* rightChild = takeInput(); 

    root->left = leftChild; 
    root->right = rightChild; 
    return root;
}
```

## Take Input Level Wise - 

We will use the same queue approach used in the Generic trees case.

```C++
BinaryTreeNode<int>* takeInputLevelWise() {
    int rootData;
    cout << "Enter root data" << endl;
    cin >> rootData;
    if (rootData == -1) {
        return NULL;
    }

    BinaryTreeNode<int>* root = new BinaryTreeNode<int>(rootData);
    
    queue<BinaryTreeNode<int>*> pendingNodes;
    pendingNodes.push(root);
    while (pendingNodes.size() != 0) {
        BinaryTreeNode<int>* front = pendingNodes.front();
        pendingNodes.pop();
        cout << "Enter left child of " << front->data << endl;
        int leftChildData;
        cin >> leftChildData;

        if (leftChildData != -1) {
            BinaryTreeNode<int>* child = new BinaryTreeNode<int>(leftChildData);
            front->left = child;
            pendingNodes.push(child);   //ask now for child's children too.
        }

        cout << "Enter right child of " << front->data << endl;
        int rightChildData;

        cin >> rightChildData;
        if (rightChildData != -1) {
            BinaryTreeNode<int>* child = new BinaryTreeNode<int>(rightChildData);
            front->right = child;
            pendingNodes.push(child);
        }
    }
    return root;
}
```

## Number of Nodes :

```C++
int numnodes(BinaryTreeNode<int>* root) {
    if(root == NULL){
        return 0;
    }
    return 1 + numNodes(root->left) + numNodes(root->right);
}
```


## Pre -Order and Post-Order :

*Pre-Order* Means the root says,  print me then my children. 
( Order : node->left->right)
*Post-Order* Means the root says, print my children then me.
(Order: left->right->node)
*In-Order* (Specific to binary trees) Basically print from left to right of the visual depiction of the tree. (Order: left->node->right)

```C++
void inorder(BinaryTreeNode<int>* root)
{
	if(root ==NULL){
		return;
	}
	inorder(root->left);
	cout<< root->data << " ";
	inorder(root->right);
}
```

#### Look into this problem
**The elements might be given as in-order or post-order or pre-order arrays (u will be given 2 orders, otherwise we wont be able to make unique tree out of it), build the binary tree from it.**

"C:\Users\WELCOME\Documents\Interview Preparation with C++\23. Lecture 16 - Binary Trees\14. Construct Tree From Preorder and Inorder.mp4"

check this out, and code this.

### Height of the binary tree - 

```C++
/* Compute the "height" of a tree -- the number of
nodes along the longest path from the root node
down to the farthest leaf node.*/
int height(node* node)
{
	if (node == NULL)
		return 0;
	else {
		/* compute the height of each subtree */
		int lheight = height(node->left);
		int rheight = height(node->right);

		/* use the larger one */
		if (lheight > rheight) {
			return (lheight + 1);
		}
		else {
			return (rheight + 1);
		}
	}
}
```

### Print level wise -

```C++
/* Function prototypes */
void printCurrentLevel(node* root, int level);
int height(node* node);
node* newNode(int data);

/* Print nodes at a given level */
void printGivenLevel(struct node* root, int level)
{
	if (root == NULL)
		return;
	if (level == 1)
		printf("%d ", root->data);
	else if (level > 1) {
		printGivenLevel(root->left, level - 1);
		printGivenLevel(root->right, level - 1);
	}
}

void printLevelOrder(struct node* root)
{
	int h = height(root);
	int i;
	for (i = 1; i <= h; i++) {
		printGivenLevel(root, i);
		printf("\n");
	}
}
```


## Diameter of a binary tree - 

**Diameter of  a binary tree is the maximum distance between 2 nodes in a binary tree. The distance is counted in terms of the number of connections crossed to reach from one of them to another.**
(might not pass thru the root, we can have the maximum diameter on only one side from the root)

```C++ 
int diameter(BimnaryTreeNode<int>* root)
{
	if(root == NULL)
	{
		return 0;
	}
	int option1 = height(root->left) + height(root->right);
	int option2 = diameter(root->left);
	int option3 = diameter(root->right);
	return max(option1, max(option2, option3));
}
```

*This has the same time complexity schema as the merge sort.**

Time Complexity for this is O(nlogn) for a normal binary tree with left and right sides.
And O(n^2) for a binary tree which is in the form of a chain, hence has a big height.

Now, from maths we have that in the first type of trees, the height is logn.
and in the second case, height is n.

*so we can say that the diameter time complexity is O(n x height).*

---

*Finally, the approach we discussed previously called for the height and diameter both on a node's right and left, leading to the higher time complexity of O(nlogn). We would want the time complexity to be O(n), as is the case with most of the binary tree things.*

```C++
pair<int, int> heightDiameter(BinaryTreeNode<int>* root) {
    if (root == NULL) {
        pair<int, int> p;
        p.first = 0;
        p.second = 0;
        return p;
    }
    pair<int, int> leftAns = heightDiameter(root->left);
    pair<int,int> rightAns = heightDiameter(root->right);
    int ld = leftAns.second;
    int lh = leftAns.first;
    int rd = rightAns.second;
    int rh = rightAns.first;

    int height = 1 + max(lh, rh);
    int diameter = max(lh + rh, max(ld, rd));
    pair<int, int> p;

    p.first = height;
    p.second = diameter;

    return p;
}
```

**Unique Approach and use of pair makes this very important to study**.

---
