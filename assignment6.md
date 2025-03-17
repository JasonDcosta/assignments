## Question 1
Starting with an empty stack S[1..6], doing PUSH(S,4) makes it S = [4,blank,blank,blank,blank,blank], then doing PUSH(S,1) gives [4,1,blank,blank,blank,blank], PUSH(S,3) gives [4,1,3,blank,blank,blank], these add the numbers to the tail of the stack. POP(S) would remove the top element making the stack [4,1,blank,blank,blank,blank]

## Question 2 

Starting with an empty queue Q[1..6] doing ENQUEUE(Q,R) adds 4 to the tail so it becomes [4,blank,blank,blank,blank,blank], ENQUEUE(Q,1) adds 1 to the tail so it becomes [4,1,blank,blank,blank,blank], ENQUEUE(Q,#) adds 3 to the tail so it becomes [4,1,3,blank,blank,blank]. Then DEQUEUE removes the front element so DEQUEUE(Q) gives [blank,1,3,blank,blank,blank]. ENQUEUE(Q,8) gives [blank,1,3,8,blank,blank]. Then DEQUEUE(Q) removes the front element so it becomes [blank,blank,3,8,blank,blank]
The head would be 3 and the tail would be 4 for the indexes.

## Question 3

For overflow I would just add
```c++
if (Q.tail == Q.length) {
std::cout << "Queue Overflow";
return;
```

For underflow I would check if the queue is empty and if it is I would then return an underflow error
```c++
if (Q.head == tail){
std::cout << "Queue Underflow";
return;
```

## Question 4

## Pseudo Code
```c++
#include <iostream>
#include <vector>
using namespace std;
//Jason D'costa Code

#Inserting at the front 
if (front == 1) front = Q.length - 1;
else front--;
Q[front] = element.

##Inserting at the back
if (back = Q.length - 1) back = 0;
else back++;
Q[back] = element;

#Deleting frmo the front
if (front ==0) front = Q.length -1;
else front++;

#Deleting from the back
if (back == 0) back = Q.length -1;
else back--;
int main() {
}

```
