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

Now, the other way will be introduced, which is using recusive function.<br />
Recusive function is calling itself.<br />
Recusive function have to two factors; one is that it must have the stop point; the sencond is that the argument must be reduced.<br />    
v value is continuously reduce, and once it will be 0, return u value as greatest common divisor; otherwise, recusive function will call itself until v becomes 0.<br /> 

```java
int gcd_recursion(int u, int v) 
{
    if (v == 0) // it is the stop pointer 
        return u;
    else
        return gcd_recursion(v, u%v);
}
```

>**NOTE: recusive function can provide more conprehensive source code; however, it uses more cost to call function.**  

## Array ##
Array is collection of data of same type: (int, float, double, char), which uses contiguous storage in a memory, the fixed size, and it can approach to the memory with index (0, 1, 2, ..., n).<br />
How to project mulit-dimensions array like one-dimension array? 
<br />
We can write an array including three rows and three columns.
<br />
int array [3][3] = {
{
{ 1, 2, 3 },
{ 4, 5, 6 },
{ 7, 8, 9 }
};
<br />
or
<br />
int array[3][3] =
{ 1, 2, 3, 4, 5, 6, 7, 8, 9 };
<br />
Each elments of this array are stored like below in memory.
<br />
![Image]({{ site.globalurl }}/contents/img/array1.jpg)
<br />
Here is two-dimensions array: 

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

We can use two-dimensions array like one-dimentsion array: 

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

Multi-demensions array also has same way:

```java
int tri[3][4][2];
int func(int t[][4][2], int n1, int n2, int n3) 
{
    // .....
    sum += m[i][j][k]; // consider this part    
}
r = func(tri);
```

We can use it like one-dimension array:

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
The member variables of linked list are a data and a link that points to another node.<br />
The linked list is the data structure that is non-contiguous storage, has variable size, access the random pointer, can **reverse iteration**.<br />
Figure1 shows the arrangement of the linked list in memory and the conceptional arragement of it.<br />

### Figure1. Physical and Logical concept of linked list ###

![Image]({{ site.globalurl }}/contents/img/linkedlist1.jpg)

### simple linked list ###
The simple linked list is simple one way linked list, which has data and next pointer. The operations are initialization, destruction, insertNext, deleteNext, and iteration & retrieval. <br />

Simple list skeleton uses a class template, node struct to represent the node, includes the constructor, insert, and delete operation. <br />

|---|---|
|**In constructor**, the head node and tail node are created, <br />and connect with each other.|![Image]({{ site.globalurl }}/contents/img/simplelinkedlist1.jpg)|

**Insert function** receives the information of current node, and a new node will be inserted after the current node. The next of new node is assigned the information of current. The next of current information refers to the informaton of new node. <br />
![Image]({{ site.globalurl }}/contents/img/simplelinkedlist2.jpg)

|---|---|
|**Delete function** receives the information of current node, <br />and a new node will be deleted after the current node. <br />The next of current node refers to the next information of deleted node. The next of current information is disconnected.|![Image]({{ site.globalurl }}/contents/img/simplelinkedlist3.jpg)|

## Doubly Linked List ##

Doubly linked list is two way linked list, and each node has two fields for refering to the previous and to the next node information. As operation, there are initialization, destruction, insertNext, insertBefore, deleteAt, iteration & retrieval.<br />

|---|---|
|**In constructor**, the head node and tail node are created, <br />and the previous of head node refers to itself, the next refers <br />to the information of tail. The previous of tail node refers <br />to the information of head, and the next refers to itself.|![Image]({{ site.globalurl }}/contents/img/doublelinkedlist1.jpg)| 

InsertNext function is very similar to the simple linked list, which receives the information of current node, and a new node will be inserted after the current node. The next of new node assigns to the information of the next field of current. The next of current information refers to the informaton of new node. <br />

![Image]({{ site.globalurl }}/contents/img/doublelinkedlist2.jpg)

InsertBefore function receives the information of current node, and a new node will be inserted before the current node. The previous of new node assigns the information of the prevous field of current. The previous of current information refers to the informaton of new node. <br />

![Image]({{ site.globalurl }}/contents/img/doublelinkedlist3.jpg)

|---|---|
|**Delete function** receives the information of  current node, <br />and a new node will be deleted after  the current node. The <br />next of current node refers to the next information of deleted node. The next  of current information is disconnected.|![Image]({{ site.globalurl }}/contents/img/doublelinkedlist4.jpg)|

## Stack ##

>Stack is a data structure with the same entrance and exit, and block the bottom. Stack is "LAST IN-FIRST OUT" (LIFO), which mean that the fisrt input data will be poped in the last order. The operations are push and pop. <br />

To implement stack, there are a using array way (array stack) and a using list (list stack). The skeletone of array stack includes an exceptions, its constructor/destructor, helper functions, push/pop/getTop/removeAll functions, and some fields are needed to store data, to represent the insert/delete positions, and to represent the size of array. Also, the skeletone of list includes exceptions, its  constructor/destructor, helper functions, push/pop/getTop/removeAll functions, and a field is needed to store data.<br />
Note that actually, simplelist is stack itself!<br />

## Queue ##

Queue is a data structure with seperate entrance and exit, and open both entrance and exit. Stack is "FIRST IN FIRST OUT" (FIFO), which mean that the fisrt put data will be gotten in the first. The operations are put and get. <br />
To implement queque, there are a using array way (array queue) and a using list way (list queue). In terms of array queue, we have to use circular queue. Why is the circular queue is needed? While putting and getting queue in array queue, the position of queue will go to the end of array. Therefore, when it arrives at the end of array, we have to copy all elements to the beginning of array; on the other hand, the circular queue do not need to copy.<br />

### circular queue operation ###

In this figure, front points the position to get data, and rear points the empty space to put data. 

![Image]({{ site.globalurl }}/contents/img/queue1.jpg)

When the 'front' and 'rear' refer to the same index of array, we call it **'Empty condition'**, and whenever element value is assigned to array, the rear refers to the next index. If the rear is located the right before the front, we call it 'Full condition'. <br />

The skeletone of circular queue includes an exceptions, its constructor/destructor, helper functions, put/get/increase/decrease functions, and some fields are needed to store data, to represent the number of data, and to represent the size of array. Also, the skeletone of ListQueue includes exceptions, its constructor/destructor, helper functions, put/get functions, and a field is needed to store data.<br />

[DSA555](https://cathyatseneca.gitbooks.io/data-structures-and-algorithms/content/)

## Notation ##

Infix notation is that there is an operator between two operands (ex: A + B), and postfix potation is that there is operator after two operands (A B +); on the other hand, prefix notation is that there is an operator before two operands (+ A B). <br />

### Post notation ###
To change infix notation to postfix notation, 

1. use the precedence of operator: '(' : 0, +-: 1, */ : 2
2. If meeting '(', push operand from stack
3. If meeting ')', add element to the result until getting '(', and throw away '('
4. If meeting operator, pop and add the element to the result until getting lower operator, and throw away itself.
5. add operands
6. When all input is complete, pop the rest all operators and add them to the result.

![Image]({{ site.globalurl }}/contents/img/postfix1.jpg)

To calculate th postfix, 
1. push the operator from stack when meeting operand.
2. pop two times operator, operate two values, and push the result in stack.
3. Last one reamining in stack is the final result

![Image]({{ site.globalurl }}/contents/img/postfix2.jpg)

## Tree ##

> Tree is a nonlinear data structure, which is consisted of node (vertex) and link (edge). Node has data, and linke represents the relationship between two nodes. Tree has at least a root, which is the top level node. All nodes have a parent node except root, but node can have serveral children node. The path from a node to other is unique.

### Binary Tree ###

> All nodes have less than or equal two nodes: left child and right child. Parse three is used to fomular calculation, heap tree is used to sort, and binary search tree is for searching.<br />

Another categorization is: 

|Complete Binary Tree|Perfect Binary Tree|
|---|---|
|all level node is filled with <br />except the last node, and last <br />nodes are left node.|all level nodes are filled with|
|![Image]({{ site.globalurl }}/contents/img/binary1.jpg)|![Image]({{ site.globalurl }}/contents/img/binary2.jpg)|

There are two way to create binary tree: array and linkedlist. Array is effective in complete binary tree case, and is used heap sort algorithm. <br />

|---|---|
|To intialize the tree structure, we may use the start node <br />and the end node to use nodes between the start and end nodes with <br />the same logic.|![Image]({{ site.globalurl }}/contents/img/tree1.jpg)|

The root node is the left of the start node. All leaf nodes refer to the end node. Binary tree skeleton has node struct, start / end node, constructor / desctructor, removeAll function.
![Image]({{ site.globalurl }}/contents/img/tree2.jpg)
 
To visit all nodes, **tree traversal** is used, which are stack-based and queque-based traversal. Stack-based traversal has **'pre-order'**, **'post-order'**, and **'in-order'**, and queue-based traversal has '**level-order**'. 

Let's move to inplemenation of traversal. To visit all of nodes of the below tree,
![Image]({{ site.globalurl }}/contents/img/tree3.jpg)

|pre-order|in-order|post-order|level-order|
|1. visit to root, 2. visit to left subtree, 3. visit to right subtree.|1. visit to left subtree, 2. visit to root, 3. visit to right subtree.|1. visit to left subtree, 2. visit to right subtree, 3. visit to root|level-order traversal is to visit from top to bottom, and frm left to right.|
|![Image]({{ site.globalurl }}/contents/img/tree4.jpg)|![Image]({{ site.globalurl }}/contents/img/tree5.jpg)|![Image]({{ site.globalurl }}/contents/img/tree6.jpg)||
|A->B->D->G->H->E->C->F->I|G->D->H->B->E->A->C->I->F|G->H->D->E->B->I->F->C->A|A->B->C->D->E->F->G->H->I|

Generally, in pre-order traversal, recusive can be converted non-converted way using stack.

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
Level-order traversal shows how to visit all node with queue.

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
Now, you can demonstrate algotrithm of pre-order traversal and level-order traversal with stack and queue respectively.

|pre-order|level-order|
|---|---|
|![Image]({{ site.globalurl }}/contents/img/tree7.jpg)|![Image]({{ site.globalurl }}/contents/img/tree8.jpg)|

### Parse Tree ###
Parse tree is to consist a tree according to operation precedence. Operator is located in root, and operand is located on child. All operator is **non terminal**, and Operand is **terminal node**.

How do you make parse tree using post notation?

To make parse, first create operand node, and push it to stack. Also, create operator node. After that, pop a node from stack, and make it as right child, and pop another node from stack, and make it as left child. Loop from 1 and 2. The last node of stack becomes root.

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
Through the above logic, fomular ((A+B)*(C-D))/E+(F*G) will become the below parse three.

![Image]({{ site.globalurl }}/contents/img/tree9.jpg)

Let's demonstrate how the parse tree is created in stack.

|---|---|
|![Image]({{ site.globalurl }}/contents/img/tree10.jpg)|![Image]({{ site.globalurl }}/contents/img/tree11.jpg)|

Note that in parse tree:
1. in-order traverse can illustrate infix notaion.
2. pre-order traverse can illustrate prefix notation.
3. post-order traverse can inllustrate postfix notation.

## Recursion ##

Recursive Function calls itself and there are divide and conquer strategy in it. . One example is tree traversal.

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

Recusive function has to meet two needs: the problem becomes smaller and there is the exit condition. In factorial algorithm, line `if (n == 0)` is the exit condition, and line `n * factorial(n – 1)` makes the size of theproblem smaller.

```cpp
int factorial (int n) 
{
    if (n == 0) // exit condition
        return 1;
    else
        return n * factorial(n – 1); // the problem size become smaller
}
```

### Fibonacci ###
Fibonacci sequence is the series of the numbers, which defines that **"every number after the first two is the sum of the two preceding ones: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, .."** ([WIKIPIDA](https://en.wikipedia.org/wiki/Fibonacci_number)).
<br /><br />
The relation can be defined: F<sub>n</sub> = F<sub>n-1</sub> + F<sub>n-2</sub>, F<sub>1</sub> = F<sub>2</sub> =0
<br />

The source code example of fibonacci is :
```cpp
int fibonacci(int n) 
{
    if (n == 1 || n == 2)
        return 1;
    else
        return fibonacci(n – 1) + fibonacci(n – 2);
}
```

Figure recusive 1 shows how it can be demonstrated in a parse tree structure. To find the number of sequence 5th in fibonacci, input the value of 5 in ``int fibonacci(n)``. So, it calls ``fibonacci(5)``, and ``fibonacci(5)`` has two leaf nodes: ``fibonacci(4)`` and ``fibonacci(3)``. ``fibonacci(4)`` also has two leaf nodes: ``fibonacci(3)`` and ``fibonacci(2)``. Since we already deinfine the value of ``fibonacci(1)`` and ``fibonacci(2)`` as **'1'**, when adding all return values, the result is **'5'**.

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
This table shows the operating step of the above source code.
#### Table recusive 1. non-recusive function ####

|step|	a|	b|	r1|
|---|---|---|---|
|1	|1	|1	|2|
|2	|1	|r1	|3|
|3	|2	|r2	|5|






