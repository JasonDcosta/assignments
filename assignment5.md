
```c++
#include <iostream>
#include <vector>
using namespace std;
//Jason D'costa Code
//#1
//With linear probing
const int TABLE_SIZE = 10;
int hashTable[TABLE_SIZE];

int hashFunction(int key) {
    return key % TABLE_SIZE;
}

void insert(int key) {
    int index = hashFunction(key);
    while (hashTable[index] != -1) {
        index = (index + 1) % TABLE_SIZE;
    }
    hashTable[index] = key;
}

bool search(int key) {
    int index = hashFunction(key);
    while (hashTable[index] != -1) {
        if (hashTable[index] == key) {
            return true;
        }
        index = (index + 1) % TABLE_SIZE;
    }
    return false;
}

//#2
int hashFunction(const string & str) {
    int hash = 0;
    for (char ch : str) {
        hash += ch;
    }
    return hash;
}

int main() {
    //#1
    for (int i = 0; i < TABLE_SIZE; i++) {
        hashTable[i] = -1;
    }

    int values[] = {200, 400, 100, 50, 350};

    for (int i = 0; i < 5; i++) {
        insert(values[i]);
    }

    int searchValue = 2;
    if (search(searchValue)) {
        cout << searchValue << " found!" << endl;
    } else {
        cout << searchValue << " not found." << endl;
    }

    //#2
    int hashValue = hashFunction("Jason");
    cout << hashValue << endl;
    return 0;


}
```
