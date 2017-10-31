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

```cpp
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

```
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

Now, the other way will be introduced, which is using recusive function.<br />
Recusive function is calling itself.<br />
Recusive function have to two factors; one is that it must have the stop point; the sencond is that the argument must be reduced.<br />    
v value is continuously reduce, and once it will be 0, return u value as greatest common divisor; otherwise, recusive function will call itself until v becomes 0.<br /> 

```
int gcd_recursion(int u, int v) 
{
    if (v == 0) // it is the stop pointer 
        return u;
    else
        return gcd_recursion(v, u%v);
}
```

>**NOTE: recusive function can provide more conprehensive source code; however, it uses more cost to call function.**  



