---
layout: default
---
# Algorithm
---

> In computer science, algorithm is "an unambiguous specification to solve problems" ([WIKIPIDIA](https://en.wikipedia.org/wiki/Algorithm)), 
Also, data structure is an abstracted data type (ADT) to handle a algorithmatic way of data such as array, stack, and queue.<br />

## Euclidean algorithm ##
Euclidean algorithm is a way to find the **greatest common divisor** of two positive integers.

In function `int gcd(int u, int v)`, 

```
1. If v is greater than u, exchange u and v; otherwise, u is assigned the value u minus v. 
2. Until u value is 0, loop. 
3. If u becomes 0, then v is greatest common divisor.
```

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
But, when the between u and v is big, this case requires many loop for operating minus between u and v.<br /> 
What is the advance way? <br />

The answer is using the rest value of divide.<br />

In function `int gcd(int u, int v)`, 

```
1. If v is not 0, u is assigned the value u divide v.
2. Exchange u and v until v value is 0. 
3. v is 0, then the greatest common divisor is u.
```

```java
int gcd (int u, int v) 
{
    int t; // the temporary variable for exchange u and v
    while (v > 0) // loop while v is greater than 0  
    { 
        // u is assigned the value u divide v, and exchange u and v
        t = u % v;
        u = v;
        v = t;
    }
    // if v is 0, escape the loop, and return u value as greatest common divisor.    
    return u;
}
```

Table1 shows how many steps there are in two GCM algorithm. The later one has far less steps, and the more large the agument value is, the more steps there are.    

### Using Minus VS Modulo operator ###

|Using minus (-) operator|Using modulo (%) operator|
|---|---|
|  GCD(280,30)|GCD(280, 30)| 
|= GCD(250,30)|= GCD(30,280)|
|= GCD(220,30)|= GCD(280,30)|
|= GCD(190,30)|= GCD(10,30)|
|= GCD(160,30)|= GCD(30,10)|
|= GCD(130,30)|= GCD(0,10)|
|= GCD(100,30)|= GCD(10,0)|
|= GCD(70, 30)|= 10|
|= GCD(40, 30)||
|= GCD(10, 30)||
|= GCD(30, 10)||
|= GCD(20, 10)||
|= GCD(10, 10)||
|= GCD(0,  10)||
|= 10||

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

Postfix notation




