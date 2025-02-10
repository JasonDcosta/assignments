# Assignment 1
## This is my assignment 1 code
```C++
#include <iostream>
using namespace std;
//Jason D'costa Code
int main() {
    // #1) How to create an array of 100 Elements
    int array[100];
    for (int i = 0; i < 100; i++) {
        array[i] = i;
    }
    // #2) How to find the size of each element of an array
    cout << "Bytes: " << sizeof(array[22]) << endl;
    //#5 How to find the memory address of an array
    cout << "Memory Address: " << &array << endl;



    return 0;
}

```
## Text explanations:
#3 For an array containing 100 elements, provide the number of steps the following operations would take: (theoretical) - 6 pts.Reading
Reading an element in array would take 1 step in both the best and worst case scenario, since the arrays are directly indexed.Searching, In the best case there would be 1 step, in the worst case there would be N steps, meaning if the element is in the last index or nonexistent. This is because you would have to check all N+1 elements if it is not in the array or it is the last one. If you insert at the end which is the best case there would be 1 step, but if you insert at the beginning which is the worst case there would be N+1 steps. This is because if you insert at the end of an array, you only add the new element to the next free location which takes one step. But if you insert at the beginning you have to move all the elements to make room for the new one. For N elements, you need to shift the elements plus another step to do the insertion which means it is N+1 steps. Deleting at the end, in the best case, would take 1 step. Deleting at the beginning which is the worst case would take N steps. This is because deleting at the end requires only one step since you dont have to shift anything. But deleting at the beginning means that you have to remove that element and then shift the other elements. Meaning that it would be 1 step for deletion + N - 1 for shifting.

#4 Counting all occurrences of a given value.

It would take 0(N) steps. This is because every element in the array has to be checked at least once. So because of that the operation would need to go through all of them meaning it would take 0(N) steps.
