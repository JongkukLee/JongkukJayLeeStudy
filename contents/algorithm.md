---
layout: default
---
# Algorithm
---

> In computer science, algorithm is "an unambiguous specification to solve problems" ([WIKIPIDIA](https://en.wikipedia.org/wiki/Algorithm)), 
Also, data structure is an abstracted data type (ADT) to handle a algorithmatic way of data such as array, stack, and queue.<br />

## Euclidean algorithm ##
Euclidean algorithm is a way to find the **greatest common divisor** of two positive integers.

Here is a function gcd `int gcd(int u, int v)`, which receive two integers 'u' and 'v' as the passed parameters and return type also integer. if u value is greater than 0, then the while statement is looping. Inside the while statement, if v is greater than u, then exchange u and v; in this case, t is the temporary variable for exchange u and v; otherwise, u is assigned the value of u minus v. If u becomes 0, then the while statement is finished, and finally return v as greatest common divisor.

```java
int gcd(int u, int v) 
{

    int t; // the temporary variable for exchange u and v

    while (u > 0) // loop while u is greater than 0 
    { 
        if (u < v) // if u is greater than v,   
        { 
            t = u; u = v; v = t; // exchange u and v
        }
        // otherwise, u assigns u minus v 
        u = u – v;
    }
    // if u is 0, escape the loop, and return v value as greatest common divisor.  
    return v;
}
```
For example, give u is 4, and v is 2. First, ask if u is greater than 0, true because now u is 4, v is 2. Next, v is greater than u, false. So, u is assignee  4 - 2, and v is still 2. In next while loop, ask if u is greater than 0, true because now u is 2, v is 2. Next, v is greater than u, false. So, u is assigned 2 - 2, and v is still 2. In next while loop, ask if u is greater than 0, false. So cursor is move to return statement, and return value is 2. Therefore the greatest common divisor is 2.

|---|---|---|---|---|---|---|---|
|u=4,v=2<br>if u>0, true|if u<v, false|u=4-2|u=2,v=2<br>if u>0, true|if u<v, false|u=2-2|u=0,v=2<br>if u>0, false|return 2|

But, when the gap between u and v is big, it requires many loop for operating minus between u and v. 
So, what is the advance way? <br />

The answer is using remainder operation.<br />

In the same function gcd `int gcd(int u, int v)`, if v value is greater than 0, then the while statement is looping. Inside the while statement, u is assigned v and v is assigned the value of u remainder v, t is the temporary variable to store the remainder vlaue. If v becomes 0, then the while statement is finished, and finally return u as greatest common divisor.

```java
int gcd (int u, int v) 
{
    int t; // the temporary variable for exchange u and v
    while (v > 0) // loop while v is greater than 0  
    { 
        t = u % v;
        u = v; // u is assigned v 
        v = t; // v is assigned the value of u remainder v
    }
    // if v is 0, escape the loop, and return u value as greatest common divisor.    
    return u;
}
```

For example, give u is 4, and v is 2. First, ask if v is greater than 0, true because now u is 4, v is 2. So, u is 2, and v is assignee  4 % 2 . In next while loop, ask if v is greater than 0, false because now u is 2, v is 0. So cursor is move to return statement, and return value is 2. Therefore the greatest common divisor is 2.

|---|---|---|---|
|u=4,v=2<br>if v>0, true|v=4%2|u=2,v=0<br>if v>0, false|return 2|

Table1 shows how many steps there are in two GCM algorithm. When using minus (-) operation, the 15 steps are needed, while when using remainder (%) operation, only 4 steps are needed. In first way, the larger the gap between two parameters is, the more steps it needs.    

### Using Minus VS Modulo operator ###

|Step|Using minus (-) operator|Using modulo (%) operator|
|---|---          |---         |
|1  |  GCD(280,30)|GCD(280, 30)| 
|2  |= GCD(250,30)|= GCD(30,10)|
|3  |= GCD(220,30)|= GCD(10,0) |
|4  |= GCD(190,30)|= 10|
|5  |= GCD(160,30)||
|6  |= GCD(130,30)||
|7  |= GCD(100,30)||
|8  |= GCD(70, 30)||
|9  |= GCD(40, 30)||
|10 |= GCD(10, 30)||
|11 |= GCD(30, 10)||
|12 |= GCD(20, 10)||
|13 |= GCD(10, 10)||
|14 |= GCD(0,  10)||
|15 |= 10||

Now, the other way will be introduced, which is using recusive function. Recusive function is calling function itself. Recusive function has two conditions; one is that it must have the end point; the sencond is that the problem must be reduced.<br />

Here is a function gcd_recustion `int gcd_recursion(int u, int v)`, which receive two integers 'u' and 'v' as the passed parameters and return type also integer. In line 6th, v value is continuously reduced by asigning u % v, and once it will be 0, then return u as greatest common divisor; otherwise, the recusive function will call the function itself until v becomes 0.<br /> 

```java
int gcd_recursion(int u, int v) 
{
    if (v == 0) // it is the stop pointer 
        return u;
    else
        return gcd_recursion(v, u%v);
}
```
### Figure1. GCD recusive funtion in tree structure ###

![Image]({{ site.globalurl }}/contents/img/recusive2.jpg)

>**Note that the recusive function can provide more conprehensive source code; however, it uses more cost to call function.**  

Let's move to next topic, array.

## Array ##
Array is a data collection in same type, for example, int, float, double, char, which uses contiguous storage in a memory, and it has the fixed size, and it can approach to the memory with index (0, 1, 2, ..., n).<br />
Now I am talking aobut how to project mulit-dimensions array like one-dimension array? 
<br />
We can write an array with three rows and three columns. It can be written: 
<br />
```
int array [3][3] = {
    { 1, 2, 3 },
    { 4, 5, 6 },
    { 7, 8, 9 }
};
```
or, it can be used like one-dimension array:
```
int array[3][3] = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
```
<br />
Each elments of this array are contiguously stored in memory:
<br />
![Image]({{ site.globalurl }}/contents/img/array1.jpg)
<br />
The index 0 to 2 is the first row or first-dimension, the index 3 to 5 is the second row, and the index 6 to 8 is third row.<br />

Here there are two ways to approach the element of two-dimensions array.

In first source code snipet, we can access each element with row and column. It is very normal way.

```java
int average(int m[][], int n1, int n2) 
{
    int i, j;
    int sum = 0;
    for (i = 0; i < n1; i++)
        for (j = 0; j < n2; j++)
            sum += m[i][j]; // consider this part
    return sum/(3 * 3);
}
int array[3][3];
int average = average(array, 3, 3);
```

However, we can also access two-dimensions array like one-dimentsion array. Note the line 7 `sum += m[i * n2 + j];` of the second source code snipet.

```java
int average(int m[][], int n1, int n2) 
{
    int i, j;
    int sum = 0;
    for (i = 0; i < n1; i++)
        for (j = 0; j < n2; j++)
            sum += m[i * n2 + j]; // consider this part
    return sum/(n1 * n2);
}
int array[3][3];
int average = average(array, 3, 3);
```

Multi-demensions array also has same way; the way of accessing multi-dimensions array,

```java
int tri[3][4][2];
int func(int t[][4][2], int n1, int n2, int n3) 
{
    // .....
    sum += m[i][j][k]; // consider this part    
}
r = func(tri);
```

and the way of accessing one-dimension array.

```java
int tri[3][4][2];
int func(int m[][][], int n1, int n2, int n3) 
{
    // .....
    sum += m[i * n2 * n3 + j * n3 + k];  // consider this part
}
r = func(tri, 3, 4, 2);
```

## Linked List ##
The linked list is the data structure that is stored non-contiguous storage in memory, has variable size, access the random pointer, can **reverse iteration**.<br />
The member variables of linked list are a data and a link that points to next node.<br />

Figure1 shows the arrangement of the linked list in memory and the conceptional arragement of it.<br />

### Figure1. Physical and Logical concept of linked list ###

![Image]({{ site.globalurl }}/contents/img/linkedlist1.jpg)

Physically, there are not contiguous in the memory. In physical concept of lisked list, each node is located in different memory area. However, in logical concept of linked list, the start node refers to 'L' node, 'L' refers to 'I', and 'I' refers to 'N' and so on. all elements are connected in order. So, it has more advantage in a inserting operation than in a searching operation. 

### simple linked list ###
The simple linked list is one way linked list, which has data and next pointer. The operations are initialization, destruction, insertNext, deleteNext, and iteration & retrieval. <br />

Simple list skeleton uses a class template, node struct to represent the node, includes the constructor, insert, and delete operation. <br />

**In constructor**, the head node and tail node are created, and initialized by connecting with each other. The next ponter of the head node refers to the address of the tail node, and the next pointer of the tail node refers to the tail node itself. Now all member variables are initialized.

![Image]({{ site.globalurl }}/contents/img/simplelinkedlist1.jpg)

Let's insert new node.

**Insert function** receives the information of current node, and a new node will be inserted after the current node. The next pointer of new node refters to where the next pointer of current node indidates. That is the address of the next node. The next pointer of current node refers to the address of new node. Now, the new node is inserted. <br />
![Image]({{ site.globalurl }}/contents/img/simplelinkedlist2.jpg)

**Delete function** receives the information of current node, and the node after the current node will be deleted. The next pointer of current node refers to where the next pointer of deleted node indicates. That is the address of the next node. The next pointer of deleted ndoe will be disconnected. Now the deleted node has nothing connection with any nodes.

![Image]({{ site.globalurl }}/contents/img/simplelinkedlist3.jpg)

So far, we see about simple linked list. From now on, we will see double linked list.

## Doubly Linked List ##

Doubly linked list is two way linked list, and each node has two fields for refering to the address of the previous and the next node. As operation, there are initialization, destruction, insertNext, insertBefore, deleteAt, iteration & retrieval.<br />

**In constructor**, the head node and tail node are created, and the previous pointer of head node refers to head node itself, the next pointer refers to the address of tail node. The previous pointer of tail node refers to the address of head node, and the next pointer refers to the tail node itself. Now, all member variables are initialized.

![Image]({{ site.globalurl }}/contents/img/doublelinkedlist1.jpg) 

**InsertNext function** is very similar to the simple linked list, which receives the information of current node, and a new node will be inserted after the current node. The next pointer of new node refers to where the next pointer of current node indicates. That is the address of the next node. The previous pointer of the new node refers to the address of current node. The next pointer of current node refers to the address of new node. Now, the new node is inserted. <br />

![Image]({{ site.globalurl }}/contents/img/doublelinkedlist3.jpg)

**InsertBefore function** receives the information of current node, and a new node will be inserted before the current node. The previous pointer of new node refers to where the prevous pointer of current node indicates. That is the address of the previous node. The next pointer of previous node refers to the address of new node. The previous pointer of current node refers to the address of new node. The next pointer of the new node refers to the address of current node. Now, the new node is inserted. <br />

![Image]({{ site.globalurl }}/contents/img/doublelinkedlist2.jpg)

**Delete function** receives the information of  current node, and the node after the current node will be deleted. The next pointer of current node refers to where the next pointer of deleted node indicates. That is the address of next node. The previous pointer of where the pointer of the deleted node indicates, refers to the address of the current node. The previous pointer and next pointer of the delete node are disconnected. Now the deleted node has nothing connection with any nodes. 

![Image]({{ site.globalurl }}/contents/img/doublelinkedlist4.jpg)

Next, we are talking about another interesting topic: **Stack and Queue**.

## Stack ##

>Stack is a data structure with the same entrance and exit, and the bottom is blocked. Stack is "LAST IN-FIRST OUT" operation called 'LIFO', which means that the fisrt input data will be poped in the last order. The operations are push and pop functions. <br />

Figure stack.1 shows the conception of the Stack data structure and algorithm. In the left figure, there are five elements into a stack, and the cursor indicates the most top position. When 'PUSH X' occurs in the middle picture, the element 'X' must be located on the most top, and cursor will indicate to new top position. When poping from a stack in the right picture, the most top element must be poped, and the cursor will indicate new top position.    
### Figure stack1. the Conception of Stack ###
![Image]({{ site.globalurl }}/contents/img/stack1.JPG)

To implement stack, there are a using array stack and list stack. The skeletone of array stack includes an exceptions, its constructor/destructor, helper functions, push/pop/getTop/removeAll functions, and some fields are needed to store data, to represent the insert/delete positions, and to represent the size of array. Also, the skeletone of list stack includes exceptions, its  constructor/destructor, helper functions, push/pop/getTop/removeAll functions, and a field is needed to store data.<br />
Note that actually a simple linked list is a stack itself!<br />

## Queue ##

>Queue is a data structure, which has different positions in entrance and exit, and both entrance and exit are opened. Queue is "FIRST IN FIRST OUT" operation called 'FIFO', which mean that the fisrt put data will be gotten in the first. The operations are put and get functions.

Figure queue1 shows the conception of the Queue data structure and algorithm. In the left picture, there are five elements in a queue, and the front indicates the exit position, and the rear indicates the entrance position. When getting from a queue in the middle picture, the most front element must be exited, and the front pointer will indicate new front position. When 'PUT X' occurs int the last picture, the 'X' must be located on the rear position, and the rear will indicate to new entrance point.

### Figure queue1. the Conception of Queue ###
![Image]({{ site.globalurl }}/contents/img/queue2.JPG)

To implement queque, there are a using array queue and list queue. In terms of array queue, we have to use circular queue. Why is the circular queue needed? Figure queue2 and Figure queue3 show how to operate in general style queue and circular queue respectively. While putting and getting elements in array queue, the position of the front and rear will move toward the end of array. But, the array has the fixed size in memory, so we can't use the index beyond the size of array. Therefore, whenever it arrives at the end of array, we have to copy all elements to the beginning of the array; on the other hand, the circular queue do not need the copy logic to implement it.<br />

### Figure queue2. General Queue operation ###
![Image]({{ site.globalurl }}/contents/img/queue3.JPG)

Figure queue3 demonstrates the circular queue. The front indicates the exit position in the queue, and the rear indicates the entrance position in the queue. 

### Figure queue3. Circular Queue operation ###
![Image]({{ site.globalurl }}/contents/img/queue1.jpg)

When the 'the front' and 'the rear' refer to the same index of circluar array, we call it **'Empty condition'**, and whenever an element is put into the circluar array queue, the rear refers to the next index of the last element. If the rear indicates the right before the front, we call it **Full condition**. In the full conditon, if new element is tried to put, then an exception must be happened.<br />

The skeletone of a circular arrry queue includes an exceptions, its constructor/destructor, helper functions, put/get/increase/decrease functions, and some fields are needed to store data, to represent the number of data, and to represent the size of array. Also, the skeletone of the list queue includes exceptions, its constructor/destructor, helper functions, put/get functions, and a field is needed to store data.<br />

[DSA555](https://cathyatseneca.gitbooks.io/data-structures-and-algorithms/content/)

Next, we are talking about **'Notation'**.

## Notation ##
In data structure and algorithm, there are three kinds of notation: prefix notation, infix notation, and postfix notation. Prefix notation is that there is an operator before two operands (+ A B). Infix notation is that there is an operator between two operands (ex: A + B), and postfix notation is that there is operator after two operands (A B +). <br />

In human being perspective, infix notation is easy to calulate, but in computer, postifx notaion is calculated easier than infix one. So, now we will see how to change infix notation to postfix notation,

### Post notation ###
To change infix notation to postfix notation using a stack, 

1. Determine the precedence of operator: '(' : 0, '+' and '-': 1, '*' and '/' : 2
2. If meeting '(', push it into the stack
3. If meeting ')', pop elements and add them to the result until meeting '(', and throw away '(' and ')'.
4. If meeting operator, pop the elements and add them to the result until meeting upper level operator than itself, and push itself.
5. If meeting operand, add operand to the result.
6. When all input are completed, pop the rest all operators and add them to the result.

When we change this infix notation (2*(3+6/2)+2)/4+3 to the postfix notation, the result is like this: 2362/+*2+4/3+.

<!--![Image]({{ site.globalurl }}/contents/img/postfix1.jpg)-->

Next, to calculate the postfix notation using a stack, 
1. If meeting operand, push the operand into the stack.
2. If meeting operator, pop an operand from the stack, put it on the right of the operator, and pop it again from the stack, and put it on the left of the operator, and calulate them, and push only result into the stack, and throw away the operator and the poped two operands.
3. Repeat 1 and 2 util the last one is left.
4. The last one is the final result.

<!-- ![Image]({{ site.globalurl }}/contents/img/postfix2.jpg) -->

## Tree ##

> Tree is a nonlinear data structure, which is consisted of node (vertex) and link (edge). Node has data, and link represents the connection between two nodes. Tree has at least a root, which is the top level node. All nodes have a parent node except root, but node can have serveral children node. The path from a node to the other is unique.

![Image]({{ site.globalurl }}/contents/img/tree12.jpg)

Especially, the binary tree is the most useful and is utilized at many parts. So, now we will see about the binary tree.

### Binary Tree ###

> Binary tree is a tree data structure that all nodes have maximum two nodes: left child and right child. **Parse three** is used in calculating, **heap tree** is used in sorting, and **binary search tree** is used in searching.<br />

Another categorization is a complete binary tree and a perfect binary tree: 
Complete Binary Tree is all level node is filled except the last node.

![Image]({{ site.globalurl }}/contents/img/binary1.jpg)

Perfect Binary Tree is all level nodes are filled.

![Image]({{ site.globalurl }}/contents/img/binary2.jpg)

There are two way to create binary tree: array tree and linked list tree. Array tree must be used in only complete binary tree case and is used in heap sort algorithm. But, now **Here we will see about a linked list tree**.<br />

To intialize the tree structure, we may use the start node and the end node. the right and left pointers of the start node refer to the address of the end node, and the left and right pointer of the end node refer to the end node itself.

![Image]({{ site.globalurl }}/contents/img/tree1.jpg)

What if are there no start and end nodes here? We have to implement different logics according to node types: the root node and the leaf nodes.

To form the below diagram, the left pointer of the start node indicates to the address of the root node 'A'. All last leaf nodes refer to the address of the end node. Binary tree skeleton has exceptions, node struct, start / end node, constructor / desctructor, removeAll functions.
![Image]({{ site.globalurl }}/contents/img/tree2.jpg)
 
To visit all nodes, **tree traversal** is used, which has a stack-based and a queque-based traversal. Stack-based traversal has **'pre-order'**, **'in-order'**, and **'post-order'**, and queue-based traversal has '**level-order**'. 

|in pre-order|in in-order|in post-order|in level-order|
|1. visit to root, 2. visit to left subtree, 3. visit to right subtree.|1. visit to left subtree, 2. visit to root, 3. visit to right subtree.|1. visit to left subtree, 2. visit to right subtree, 3. visit to root|visit from top to bottom, and from left to right.|
|![Image]({{ site.globalurl }}/contents/img/tree4.jpg)|![Image]({{ site.globalurl }}/contents/img/tree5.jpg)|![Image]({{ site.globalurl }}/contents/img/tree6.jpg)||
|A->B->D->G->H->E->C->F->I|G->D->H->B->E->A->C->I->F|G->H->D->E->B->I->F->C->A|A->B->C->D->E->F->G->H->I|

Let's visit all of the below nodes. Assume that each node will print node's name when visiting.

![Image]({{ site.globalurl }}/contents/img/tree3.jpg)

First, in pre-order traversal, the order is the root - the left child node - the right child node. So, move to the root node and print A, then move to the left child node and print B, then move to  the left child node and print D, then move to  the left child and print G, G node has no child node, so move to  the right node and print H, in subroot B node perspect, all left nodes were visited, so move to  the right child node and print E. Now in the root A node perspect, all left nodes were visited, so move to the right node and print C, C has only right child node, so move to the right child node and print F, then move to the left child node and print I. Now all nodes are visited. So, the travesal path is A->B->D->G->H->E->C->F->I.

![Image]({{ site.globalurl }}/contents/img/tree3.jpg)

Second, in in-order traversal, the order is the left child node - the root - the right child node. The root node has  a left child node B, and B node has a left child node D, D has a left child node G, G has no child node. So, print G, then move to subroot D and print D, then move to right child node H and print H. In subroot B perspect, all left nodes are printed, so print B itself, then move to the right child node and print E. In root A perspect, all left noeds were printed, so print A itself, then mvoe to the right child node. C has no left node, so print C itself, then move to the right child F. Node F has the left node, so move to I, I has no child, so print I. In node F perspect, all left nodes are printed, so print F itself. Now, all nodes were visited. So, the traversal path is G->D->H->B->E->A->C->I->F.

![Image]({{ site.globalurl }}/contents/img/tree3.jpg)

Third, in the post-order traversal, the order is the left child node - the right child node - the root. The root A has left child node B, and B node has a left child node D, D has a left child nod G, G has no child node. So, print G, then subroot D also has the right child node H, so move to H and print H. In subroot D perspect, all child nodes were visited, so print D itself. In subroot B perspect, all left nodes were visited, so move to the right node and print E, then print B itself. In the root node A perspect, all left nodes were visited. So, move to the right node C. C has only F node, and F node has only I node. I node has no child node anymore. So, print I. F has no the right node, so print F itself. C has no left node and all right nodes were visited, so print C itselft. In root node A perspect, all left and right child nodes were visited. So, print A itself. Now all nodes were visited, So the traversal path is G->H->D->E->B->I->F->C->A.

![Image]({{ site.globalurl }}/contents/img/tree3.jpg)

Lastly, in level-order, it is visited by the order from top node to bottom node, from left node to right node. So, the traversal path is A->B->C->D->E->F->G->H->I.

Generally, a recusive function can be converted to a non-recusive function using a stack.

### Tree Source Code1. Non-Recusive Pre-Order Traverse Function.  

```cpp
void BinaryTree::PreOrderTraverse_Stack(Node *pNode) 
{
    ListStack<Node*> stack;
    stack.Push(pNode);
    while (!stack.IsEmpty()) 
    {
        pNode = stack.Pop();
        if (pNode != m_pNodeTail) 
        {
            Visit(pNode);
            stack.Push(pNode->pRight);
            stack.Push(pNode->pLeft);
        }
    }
}
```
![Image]({{ site.globalurl }}/contents/img/tree7.jpg)

We will demonstrate how to use the pre-order traversal of this tree in a stack.
According to Tree Source Code1, fisrt, push the root node A in the stack. In while statement, pop the root node A from the stack, print A and push the right child node C and the left child node B. Note that because we use a stack, we must push the right child node first. Then loop the while statement and pop the node B from the stack, print B and push the right child node E and the left child node D. Then, loop the while statement, pop the node D from the stack, print D and push the the node H and G. Then, loop the while statement, and pop the node G. G has no child nodes anymore. So, loop again, and pop the node H from the stack, print H. H has no child nodes anymore. So, loop, and pop the node E. E has no child nodes. So, loop, and pop the node C from the stack, print C and push the right node F. C is no left child node. So, loop, and pop the node F from the stack, print F and push I. F has no right child node. So, loop and pop the node I from the stack, print I. Now all nodes were printed. Compare the path with the pre-order traversal. It has the exact same path: A->B->D->G->H->E->C->F->I. 

Note that a recusive function can also be converted a non-recusive function in in-order and post-order traversal, but it is more complecated to demonstrate them. 

Now we will see that in level-order traversal, the recusive function can be converted to a non-recusive function. Remember that the level-order traversal uses the queue data structure. 

### Tree Source Code2. Non-Recusive Level-Order Traverse Function. 

```cpp
void BinaryTree::LevelOrderTraverse(Node *pNode) 
{
    ListQueue<Node*> queue;
    queue.Put(pNode);
    while (!queue.IsEmpty()) 
    {
        pNode = queue.Get();
        if (pNode != m_pNodeTail) 
        {
            Visit(pNode);
            queue.Put(pNode->pLeft);
            queue.Put(pNode->pRight);
        }
    }
}
```
![Image]({{ site.globalurl }}/contents/img/tree8.jpg)

According to Tree Source Code2, fisrt, put the root node A into the queue. In while statement, get the root node A from the queue, print A and put the left child node B and the right child node C. Note that because we use a queue, we must put the left child nod first (it is opposite to a stack). Then loop the while statement and get the node B from the queue, print B and put the left child node D and right child node E. Then loop the while statement, get the node C, print C and C has no left child node, so put the the right node F. Next, loop again, and get the node D, print D and put the node G and H. Then, loop again, get the node E and print E. E has no child nodes. So, loop again, and get the node F from the queue, print F. F has only left node I, so put the node I. Loop again, and get the node G and print G. G has no child node. So, loop, and get the node H and print H. H has no child nodes, so loop again, and get the node I and print I. I has no child node. So, now all nodes were printed. Compare the path with the level-order traversal. It has the exact same path: A->B->C->D->E->F->G->H->I.

### Parse Tree ###
Parse tree is to consist a tree according to operation precedence. The first order becomes leaf, and later order becomes the root. Therefore, operator is located in root, and operand is located on child. All operator is **non terminal**, and Operand is **terminal node**. Refer to figure parse tree1. The example of parse tree diagram. Fomular ((A+B) * (C-D)) / E + (F * G) will become the below parse tree.

### Figure parse tree1. The example of parse tree diagram ###
![Image]({{ site.globalurl }}/contents/img/tree9.jpg)

Note that in parse tree:
1. the in-order traverse can illustrate the infix notaion.
2. the pre-order traverse can illustrate the prefix notation.
3. the post-order traverse can illustrate the postfix notation.

How do you make a parse tree using the post notation? Let's demonstrate how the parse tree is created in a stack.
<br /><br />
To make parse tree in post notation, first, create operand nodes A and B, and push them into the stack. Also, create operator node +. After that, to create an operator node subtree, pop the node B from the stack, and make it as right child node of operator node +, and pop the node A from the stack, and make it as left child node of operator node +. Then, push the operator subtree into the stack, and repeat this process until the last subtree leaves in the stack, and the last subtree will be the root tree.

|---|---|
|![Image]({{ site.globalurl }}/contents/img/tree10.jpg)|![Image]({{ site.globalurl }}/contents/img/tree11.jpg)|

Why do we use the post notation to make parse tree? That is because computer most easy calculate it in the post notation.
<br /><br />
The below source code shows the algorithm to make parse tree in the post notation.

```cpp
//1. push operand node to stack
//2. create operator node
//    1. pop a node from stack, and make it as right child
//    2. pop another node from stack, and make it as left child
//    3. push operator Node to stack
//3. the last node of stack is root

void ParseTree::BuildParseTree(const String& strPostfix) 
{
    Node *pNode;
    int i = 0;
    ListStack<Node*> NodeStack;
    RemoveAll();
    while (strPostfix[i]) {
        while (strPostfix[i] == ' ')
            i++; // ignore space
        
        pNode = new Node;

        if (IsOperator(strPostfix[i])) 
        {
            pNode->data = strPostfix[i];
            i++;
            pNode->pRight = NodeStack.Pop();
            pNode->pLeft = NodeStack.Pop();
        }
        else 
        {
            do {
                pNode->data += strPostfix[i];
                i++;
            } while (strPostfix[i] != ' ' &&
                i < strPostfix.GetLength());
            
            pNode->pLeft = m_pNodeTail;
            pNode->pRight = m_pNodeTail;
        }
        NodeStack.Push(pNode);
    }
    m_pNodeHead->pLeft = NodeStack.Pop();
}
```

Let's move to more interesting topic, **Recusion**.

## Recursion ##

Recursive Function calls the function itself and there uses the divide and conquer strategy in it. One example is the tree traversal like below source code. In this source code, the function PreOrderTraverse calls PreOrderTraverse function itself to make the left and right child nodes.

```cpp
void BinaryTree::PreOrderTraverse(Node *pNode) 
{
    if (pNode != m_pNodeTail) 
    {
        Visit(pNode);
        PreOrderTraverse(pNode->pLeft);
        PreOrderTraverse(pNode->pRight);
    }
}
```

To implement a recusive function, there are two requirements: one is that the problem must be reduced and another is that it needs the end condition. In factorial function, line third `if (n == 0)` could be the end condition, and line sixth `n * factorial(n – 1)` makes the problem smaller. Finally, when the argument n becomes 0 and meet the exit condition, the function call is finished and return value 1.

```cpp
int factorial (int n) 
{
    if (n == 0) // exit condition
        return 1;
    else
        return n * factorial(n – 1); // the problem become smaller
}
```

Now, I will give you more complecated example, fibonacci.

### Fibonacci ###
Fibonacci sequence is the series of the numbers, which defines that **"every number after the first two is the sum of the two preceding ones: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ..."** ([WIKIPIDA](https://en.wikipedia.org/wiki/Fibonacci_number)).

For example, here is a group of number: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...
There is no two preceding numbers for the first number 0. There is no two preceding numbers for the second number 1. For third number 1, sum two preceding numbers: 0 plus 1; the answer is 1. For next number 2, sum two preceding numbers: 1 plus 1; the answer is 2. Next, 1 plus 2 is 3, and 2 + 3 is 5 and so on. 

The relation can be defined: F<sub>n</sub> = F<sub>n-1</sub> + F<sub>n-2</sub>, F<sub>1</sub> = F<sub>2</sub> = 1
<br />

The source code of the fibonacci is like this.
```cpp
int fibonacci(int n) 
{
    if (n == 1 || n == 2)
        return 1;
    else
        return fibonacci(n – 1) + fibonacci(n – 2);
}
```
As you can see, in fibonacci funtion, when parameter n is number 1 or 2, the function call is finished, and return nubmer 1; otherwise, the function calls itself repeatly.
<br />

Figure recusive 1 shows how it can be demonstrated in a parse tree structure. To find 5th number in fibonacci sequence, input the number 5 as the argument in line 5th ``int fibonacci(n)``. So, it calls ``fibonacci(5)``, and ``fibonacci(5)`` has two leaf nodes: ``fibonacci(4)`` and ``fibonacci(3)``. ``fibonacci(4)`` also has two leaf nodes: ``fibonacci(3)`` and ``fibonacci(2)``. Since we already deinfine the value of ``fibonacci(1)`` and ``fibonacci(2)`` is **'1'**, the last child nodes will return value 1. So, when adding all return values, the final result is **'5'**.

#### Figure recusive 1. recusive tree diagram for fibonacci ####
![Image]({{ site.globalurl }}/contents/img/recusive1.jpg)

Consider how we can write fibonacci as non-recusive function. 

```cpp
int fibonacci_nr(int n) 
{
    int r = 0;
    int a = 1;
    int b = 1;
    if (n == 1 || n == 2)
        return 1;
    while (n-- > 2) 
    {
        r = a + b;
        a = b;
        b = r;
    }
    return r;
}
```

The below table shows the operating steps of the above source code. When the argument value is 5, the step0 initializes the function. In the step1, r is a + b: 2, and a is assigned b: 1, b is assined r: 2, in the step2, r is 3, and a is assigned b: 2, b is assined r: 3, in the step3, r is 5, and a is assigned b: 3, b is assined r: 5, in step 4, n is not great than 2, so the loop is finished, and return r: 5, so the final result is 5. It is the same value to when using recusive fucntion.

#### Table recusive 1. non-recusive function ####

|step   |n > 2    |r      |a      |b      |
|-------|---------|-------|-------|-------|
|0	    |5        |0      |1	  |1	  |
|1	    |5>2,true |2      |1	  |2	  |
|2	    |4>2,true |3      |2	  |3	  |
|3	    |3>2,true |5      |3	  |5	  |
|4	    |2>2,false|5      |3	  |5	  |

When we compare between a recusive fibonacci function and a non-recusive fibonacci function, the soruce of the recusive function is simpler and readable. However, the recusive function should be spent more cost to call funtion itself repeatly. So, when not repeating to call function too much, use the recusive function; otherwise, use the non-recusive function.


## Sort ##

>Sort is to re-arrange data set in a certain order such as ascending and descending, which has two basic operations: a comparison and an exchange. For example, in a database system, there might be key fields and records. The key could be subject to comparison, and records could be subject to exchanging.

### Selection Sort ###

>Selection Sort is finding the smallest value in the unordered part of array and to puting it after the ordered part of array.

For example, there is data set: 1 3 4 5 10 8 6 7 9 11 12. 1 3 4 5 are already sorted by an ascending order, yet 10 8 6 7 9 11 12 are not ordered. So, first, find the smallest value by comparing the elements in the unorder part, that is 6, and exchange it with 10. As a result, the order part is 1 3 4 5 6, and the unordered part is 8 10 7 9 11 12. Repeat this logic until all elements are sorted.

#### Figure Sort1. Selection Sort ####

![Image]({{ site.globalurl }}/contents/img/selectionsort1.jpg)

#### Table Sort1. Comparision and Exchange in Selection Sort ####

|ordered part|unorder part|State      |
|------------|------------|-----------|
|1 3 4 5|10 8 6 7 9 11 12|Before comparision and exchange |
|1 3 4 5 6|8 10 7 9 11 12|After comparision and exchange |
|1 3 4 5 6 8 9 10 11 12||Complete of comparision and exchange |

### Insertion Sort ###

>Insertion Sort is inserting the elements of the unordered part into the proper place of the ordered part in an array.

For example, there is data set: A G L O R I T H M. A G L O R are already sorted by an ascending order, yet I T H M are not ordered. So, choose the first element of the unorder part, that is I, and insert it by comparing and exchanging ti with the elements in the ordered part. As a result, the order part is A G I L O R, and the unordered part is T H M. Repeat this logic until all elements are sorted.

#### Figure Sort2. Insertion Sort ####

![Image]({{ site.globalurl }}/contents/img/insertionsort1.jpg)

#### Table Sort2. Comparision and Exchange in Insertion Sort ####

|ordered part|unorder part|State      |
|------------|------------|-----------|
|A G L O R|I T H M|Before comparision and exchange |
|A G I L O R|T H M|After comparision and exchange |
|A G H I L M O R T||Complete of comparision and exchange |

### Bubble Sort ###

>Bubble Sort is sorting the elements through comparign and swapping the element with adjacent element from the begining element to the array size - 1.

For example, there is data set: A G L I O H M R T. R T are already sorted by an ascending order, yet A G L I O H M are not ordered. So, choose the first element of in the unorder part, that is A, compare it with adjacent element, that is G, and exchange each other, but in this case, G is greater than A, so there is no swapping. Next, G and L also no swapping, L and I needs the swapping, So, now the order is A G I L O H M R T. Next, L and O doesn't need the swapping. Next, O and H need the swapping. So, now the order is A G I L H O M R T. Next, O and M need the swapping. So, now the order is A G I L H M O R T. At this time, A G I L H M is the unordered part. O R T is the ordered part. Then, repeat this logic until all elements are sorted.

#### Figure Sort3. Bubble Sort ####

![Image]({{ site.globalurl }}/contents/img/bubblesort1.jpg)

#### Table Sort3. Comparision and Exchange in Bubble Sort ####

|ordered part|unorder part|State      |
|------------|------------|-----------|
|A G L I O H M|R T|Before comparision and exchange |
|A G I L H M |O R T|After comparision and exchange |
|A G H I L M O R T||Complete of comparision and exchange |


### Merge Sort ###

> Merge sort is sorting more than one sorted lists. 

The algorithm is: 

1. Compare the first element of each list.<br />
2. Pick the smaller of the two and copy the smaller to the result list.<br />
3. Increase the index of that list to the next element.<br />
4. Continue until one of the list is completely copied.<br />
5. Copy the remainder of the rest of the list.<br />

For example, there are two sorted lists; one is A E L N R, and another is O R S T.

|A  |E  |L  |N  |R  |
|O  |R  |S  |T  |   |
|   |   |   |   |   |   |   |   |   |

Compare the first elements of each list: A and O, and the smallest is A. So, copy A to the result list. Now, increase the index.

|E  |L  |N  |R  |
|O  |R  |S  |T  |   |
|A  |   |   |   |   |   |   |   |   |

Compare the first elements: E and O, and smallest is E. So, copy E to the result list. Now, increase the index.

|L  |N  |R  |
|O  |R  |S  |T  |   |
|A  |E  |   |   |   |   |   |   |   |

Repeat the logic until one list is consumed.

|N  |R  |
|O  |R  |S  |T  |   |
|A  |E  |L  |   |   |   |   |   |   |

|R  |
|O  |R  |S  |T  |   |
|A  |E  |L  |N  |   |   |   |   |   |

|R  |
|R  |S  |T  |   |
|A  |E  |L  |N  |O  |   |   |   |   |

|R  |
|S  |T  |   |
|A  |E  |L  |N  |O  |R  |   |   |   |

|   |
|S  |T  |   |
|A  |E  |L  |N  |O  |R  |R  |   |   |

When the one list is consumed, copy the rest part to the result list    .

|   |
|   |
|A  |E  |L  |N  |O  |R  |R  |S  |T  |

### Quick Sort ###
> Partition is to arrange the lower values than pivot value in the left side of pivot and to arrange the upper values than pivot value in right side of pivot. So, Quick Sort is to repeat to call the partition function. It is efficient because two nodes, which are away each other, are changed.

The algorithm of Quick Sort is like this:

1. Pick a value from the array as the pivot. Usually, it is the last element of array.
2. Let variable i as front, j as back.
3. Advance i until you find a value array[i] is greater than the pivot.
4. Move j towards front of array until array[j] is less than the pivot.
5. Swap these array[i] and array[j].
6. Repeat step 3 to 5 until i index is greater than j index.
7. Exchange array[i] and pivot value each other.
8. The i is used to break the array up into two pieces.
9. Repeat step 1 to 8 in these two new arrays util the number of array becomes 1.

For example, there is data set: A G O L I O T H M. Let's pick 'R' as pivot value. i is the front of this array, and j is the end of this array.

|i  |   |   |   |   |   |   |j  |pv |
|A  |L  |G  |O  |R  |I  |T  |H  |M  |

Advace i util finding array[i] is greater than pivot. Move j toward front until array[j] is less than the pivot, and swap the values. 

|   |   |   |i  |   |   |   |j  |   |
|A  |L  |G  |H  |R  |I  |T  |O  |M  |

Repeat these steps until i index is greater than j index.

|   |   |   |   |i  |j  |   |   |   |
|A  |L  |G  |H  |I  |R  |T  |O  |M  |

|   |   |   |   |j  |i  |   |   |   |
|A  |L  |G  |H  |I  |R  |T  |O  |M  |

Exchange array[i] and pivot value each other.

|   |   |   |   |j  |i  |   |   |   |
|A  |L  |G  |H  |I  |M  |T  |O  |R  |

we can break the array into two arrays; one is A L G H I; another is T O R.

|   |   |   |   |j  |i  |   |   |   |
|A  |L  |G  |H  |I  |M  |T  |O  |R  |

Move i to the first, and repeat the above step again in the left array.

|i  |   |   |j  |pv |   |   |   |   |
|A  |L  |G  |H  |I  |M  |T  |O  |R  |

|j  |i  |   |   |   |   |   |   |   |
|A  |G  |H  |I  |L  |M  |T  |O  |R  |

The left array is the same way to the right array.

|   |   |   |   |   |   |i  |j  |pv |
|A  |G  |H  |I  |L  |M  |T  |O  |R  |

|   |   |   |   |   |   |j  |i  |pv |
|A  |G  |H  |I  |L  |M  |O  |R  |T  |

Now quick sort for all elements is completed.

|A  |G  |H  |I  |L  |M  |O  |R  |T  |

### Heap Sort ###
>In computer science, a heap is a specialized tree-based data (**complete binary tree**) structure that satisfies the heap property, which is implementation of an abstract data type called a priority queue.[WIKIPIDA](https://en.wikipedia.org/wiki/Heap_(data_structure))

> Priority Queue can insert new data, and get the highest priority data. As the example of priority, there are Stack, Queue, and Heap.

Stack has Push and Pop operations and is “LAST IN-FIRST OUT” operation called ‘LIFO’. That is the first pushing date must be popped in the first. 
Queue has Put and Get operations and is “FIRST IN FIRST OUT” operation called ‘FIFO’. That is the fisrt puting data will be gotten in the first.
Heap has Insert and Remove operation and the highest value must be removed in the first.

In Heap date structure, the highest key value is the highest priority and the value of the parent node must be greater than two child nodes, so the value of the root node is the highest priority.

Let's see the insertion operation in the Heap. 

This example refers to [cathyatseneca.gitbooks.io](https://cathyatseneca.gitbooks.io/data-structures-and-algorithms/content/sorting/insertion_into_a_binary_heap.html)
Insert into a heap the following values in order: 10,6,20,5, 16, 17, 13,2
We will use smaller values has higher priority as our priority ordering.
An insertion node will be located the last poistion of complete binary tree and compare and exchange with the parent node. It is called **'UpHeap'**.

So, first, insert 10. Next, insert 6. 6 is the higher priority than 10, so exchange position each other. Next, insert 20 in the last position of the tree. 20 is not higher priotiy than 6, so no exchange here. Next, insert 5 in the last position of the tree. 5 is higher than 10, so exchange each other, and 5 is higher than 6, so exchange again. With the same manner, repeat the insertion operation until inserting the last data 2.

![Image]({{ site.globalurl }}/contents/img/heapsort1.jpg)

![Image]({{ site.globalurl }}/contents/img/heapsort2.jpg)

![Image]({{ site.globalurl }}/contents/img/heapsort3.jpg)

![Image]({{ site.globalurl }}/contents/img/heapsort4.jpg)

Another important operation is remove operation. To remove the node, remember that we need to remove the highest priority node and next priority node will be placed to the deleted position without violating the Heap Order Property. In heap data structure, the highest priority node means the **'Root'** node.

Next example refers to [cathyatseneca.gitbooks.io](https://cathyatseneca.gitbooks.io/data-structures-and-algorithms/content/sorting/delete_from_a_binary_heap.html)

First, remove the root node, and compare and exchange between nodes without violating the Heap Order Property.

In here, remove the root node 2, and compare two child nodes: 5 and 13. 5 is higher than 13. So, 5 becomes the parent. Next, compare 6 and 16. 6 is higher than 16. So, 6 becomes the parent. Now, complete binary tree is completed without violating the Heap Order Property.

![Image]({{ site.globalurl }}/contents/img/heapsort5.jpg)

We can see how to convert the heap data structure to an array. To convert, we will use level-order traversal trip, which is moving from the top to the bottom and from the left to the right.

![Image]({{ site.globalurl }}/contents/img/heapsort6.jpg)

In the array, we can find the relation between parent nodes and child nodes.
The parent node of J index node is J/2, and the left node of J index node is J*2, and the right node is J*2+1. Another important part is that there is the inner nodes until the half of N (N/2).

UpHeap/Insert Operation
![Image]({{ site.globalurl }}/contents/img/heapsort7.jpg)

```cpp
void UpHeap(TYPE a[], int k) 
{
    TYPE v;
    v = a[k];
    while (a[k/2] < v && k > 1) {
        // Find the insert position and insert
        a[k] = a[k/2];
        k /= 2;
    }
    a[k] = v;
}
void Insert(TYPE a[], int& n, TYPE v) 
{
    a[++n] = v; // Add node
    UpHeap(a, n); // UpHeap with the added node
}

```
DownHeap/Extract Operation
![Image]({{ site.globalurl }}/contents/img/heapsort7.jpg)
```cpp
void DownHeap(TYPE a[], int n, int k) 
{
    int i;
    TYPE v = a[k]; // Actually, a[k] is the root
    while (k <= n/2) { // Check if the inner node is
        i = k * 2; // i is the index of the left child node of a[k]
        if (i < n && a[i] < a[i+1]) i++; // Choose the node of the bigger value
        if (v >= a[i]) break; // Break when there is in the heap condition
        a[k] = a[i]; // Insert when not satisfied in the heap condition
        k = i;
    }
    a[k] = v; // k is the index of where the root value v need to insert.
}

TYPE Extract(TYPE a[], int& n) 
{
    TYPE v = a[1]; // Notice that the root value is the highest value of the tree.
    a[1] = a[n--]; // Replace the end node to the root
    DownHeap(a, n, 1); // DownHeap with the root. 
    return v;
}
```


