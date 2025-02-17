## Task 1 - How many steps would it take to perform a linear search for the number 8 in the ordered array, [2, 4, 6, 8, 10, 12, 13]? - 1 pt
It would take 4 steps to perform a linear search for the number 8 in the ordered array. This is because it starts on the first index - 2, then 4, then 6, then 8. That is four different steps since linear search starts from the first one.
## Task 2 - How many steps would binary search take for the previous example? - 1 pt
It would take a binary search 8 steps for the previous example because it starts in the middle. 
## Task 3 - What is the maximum number of steps it would take to perform a binary search on an array of size 100,000? - 1 pt
To find the maximum number of steps it would take to perform a binary search on an array of size 100,000 you would have to compute log2(100,000). This would return 16.6 but you would round and that would give you 17.
```c++
#include <iostream>
#include <vector>
using namespace std;
//Jason D'costa Code
int linearSearch(int arr[],int size, int target){
    int steps = 0;
    for (int i = 0; i < size; i++) {
        steps += 1;
        if (arr[i] == target) {
            cout << "Linear Search Steps: " << steps << endl;

            return i;
        }
    }
}
int binarySearch(int arr[],int size, int target) {
    int low = 0;
    int steps = 0;
    int high = size - 1;
    while (low <= high) {
        steps++;
        int mid = (low + high) / 2;
        if (arr[mid] == target) {
            cout << "Binary Search Steps: " << steps << endl;
            return mid;
        }
        else if (arr[mid] < target) {
            low = mid + 1;
        }
        else {
            high = mid - 1;
        }
    }
    cout << "Binary Search Steps: " << steps << endl;
}
int main() {
    int myArray[] = {2,4,6,8,10,12,13};
    int size = sizeof(myArray) / sizeof(myArray[0]);

    int index = linearSearch(myArray, size,8);
    binarySearch(myArray, size, 8);





    return 0;
}

```

