1. Imagine you were to take an empty binary search tree and insert the following sequence of numbers in this order: [1, 5, 9, 2, 4, 10, 6, 3, 8]. Draw a diagram showing what the binary search tree would look like. Remember, the numbers are being inserted in the order presented here. (2 points)
   <img width="770" alt="image" src="https://github.com/user-attachments/assets/da802738-5cfe-462e-b09b-d1132b1e039b" />

# 2 If a well-balanced binary search tree contains 1,000 values, what is the maximum number of steps it would take to search for a value within it? (1 point)
log2(1000) = 10
# 3 & 4 CODE
```c++
#include <iostream>
using namespace std;

struct Node {
    int value;
    Node* left;
    Node* right;

    Node(int val) : value(val), left(nullptr), right(nullptr) {}
};
Node* findMax(Node* root) {
    while (root->right != nullptr) {
        root = root->right;
    }
    return root;
}
Node* insert(Node* root, int value) {
    if (root == nullptr) {
        return new Node(value);
    }

    if (value < root->value) {
        root->left = insert(root->left, value);
    } else {
        root->right = insert(root->right, value);
    }

    return root;
}



int main() {
    int arr[] = {1, 5, 9, 2, 4, 10, 6, 3, 8};
    Node* root = nullptr;

    for (int val : arr) {
        root = insert(root, val);
    }

    return 0;
}
```
