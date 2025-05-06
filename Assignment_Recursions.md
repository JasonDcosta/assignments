```c++
#include <iostream>
#include <vector>
using namespace std;
//#3
int sum(int low, int high) {
  if (low > high) {
    return 0;
  }
  return high + sum(low, high - 1);
}
//#4
void print_all_numbers(const vector<vector<int>>& arr) {
  for (const auto& element : arr) {
    if (element.size() > 0) {
      for (int num : element) {
        cout << num << endl;
      }
    } else {
      cout << element[0] << endl;
    }
  }
}

int main() {
  cout << sum(1, 10) << endl;

  vector<vector<int>> array = {
    {1},
    {2},
    {3},
    {4, 5, 6},
    {7},
    {8, 9, 10, 11},
    {12, 13, 14},
    {15, 16, 17, 18, 19},
    {20, 21, 22},
    {23, 24, 25},
    {26, 27, 29},
    {30, 31, 32},
    {33}
  };

  print_all_numbers(array);

  return 0;
}
```
