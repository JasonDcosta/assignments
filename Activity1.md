<img width="770" alt="image" src="https://github.com/user-attachments/assets/116c03e4-777b-474f-baa6-1575d10b2af1" />

```c++
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

vector<int> adj[5];
bool visited[5];

void BFS(int s) {
    queue<int> q;
    visited[s] = true;
    q.push(s);
    cout << "BFS: ";
    while (!q.empty()) {
        int u = q.front(); q.pop();
        cout << char('A' + u) << ' ';
        for (int v : adj[u]) {
            if (!visited[v]) {
                visited[v] = true;
                q.push(v);
            }
        }
    }
    cout << "\n";
}

void DFS(int u) {
    visited[u] = true;
    cout << char('A' + u) << ' ';
    for (int v : adj[u]) {
        if (!visited[v]) DFS(v);
    }
}

int main() {
    adj[0] = {1,2};
    adj[1] = {0,2,3};
    adj[2] = {0,1,3,4};
    adj[3] = {1,2};
    adj[4] = {2};

    BFS(0);

    fill(begin(visited), end(visited), false);
    cout << "DFS: ";
    DFS(0);
    cout << "\n";

    return 0;
}
```
