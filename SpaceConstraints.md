```c++
#include <vector>
// #3
void reverseInPlace(std::vector<int>& arr) {
    size_t left = 0, right = arr.size() - 1;
    while (left < right) {
        int temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
        ++left;
        --right;
    }
}

```
