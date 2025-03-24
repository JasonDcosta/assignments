# Task create a linked list code:
```c++
#include <iostream>
#include <vector>
using namespace std;
//Jason D'costa Code

#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void insertAtStart(Node*& head, int newData) {
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = head;
    head = newNode;
}

void deleteAtStart(Node*& head) {
    if (head == nullptr) {
        cout << "The list is empty." << endl;
        return;
    }
    Node* temp = head;
    head = head->next;
    delete temp;
}

void displayList(Node* head) {
    if (head == nullptr) {
        cout << "The list is empty." << endl;
        return;
    }
    Node* temp = head;
    while (temp != nullptr) {
        cout << temp->data << " -> ";
        temp = temp->next;
    }
    cout << "NULL" << endl;
}

int main() {
    Node* head = nullptr;

    insertAtStart(head, 10);
    insertAtStart(head, 20);
    insertAtStart(head, 30);
    insertAtStart(head, 40);

    cout << "linked List after inserting nodes at the start:" << endl;
    displayList(head);

    deleteAtStart(head);
    cout << "linked List after deleting the node at the start" << endl;
    displayList(head);

    return 0;
}

```
