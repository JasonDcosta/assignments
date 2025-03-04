# Task 1
The reason that insertion sort has a time complexity of O(N^2) is because it performs comparisons lkke 1 comparison for the second element, 2 for the third, etc. The formula is the summation of 1+2+3+...+(N-1) and this is O(N^2) time complexity.

# Task 2 
The worst case scenario is that it is reverse order and so each element is compared with every element before it. There are 20 total operations because there is 10 comparisons and 10 switches.
# Task 3
```c++
#include <iostream>
#include <vector>
using namespace std;
//Jason D'costa Code
/*bool containsX(string str) {
    bool findX = false;
    for(size_t i = 0; i < str.length(); i++) {
        if (str[i] == 'X') {
            findX = true;
        }
    }
    return findX;
}*/
bool containsX(string str) {
for (size_t i = 0; i < str.length(); i++) {
if (str[i] == 'X') {
return true;  // Stop immediately when "X" is found
}
}
return false;  // Return false if "X" is not found
}
int main() {
string a = "Hello World";
    cout << containsX(a);
    return 0;
}
```
