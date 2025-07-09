## Problem Statement

On the occasion of Independence Day, students lined up in the form of a linked list for a prayer at school. However, the teacher wants them to rearrange themselves in non-decreasing order of their heights to present a better appearance.

Determine the number of students who need to change their positions to achieve the teacher's desired arrangement.

## Input Format

- The first line of input contains an integer N, representing the size of the LinkedList.

- The second line of input contains N space-separated integers,representing the heights of the students in the LinkedList.

## Output Format

- Display the minimum number of changes they must make to make the LinkedList in non-decreasing order.

---

## Constraints

- **1 ≤  N ≤ 10<sup>6</sup>**

- **1 ≤  Node.val ≤10<sup>6</sup>**

---

## Sample Testcase 0

**Input:**
```bash
5
2 3 4 5 6
```

**Output:**
```bash 
0
```

### Explanation

The values are already in the correct position, so the count is 0.

## Sample Testcase 1

**Input:**
```bash
5
1 8 27 2 3
```

**Output:**
```bash
4
```
### Explanation

The correct formation should be <br>
1 2 3 8 27<br>
So, in 4 positions, the values are different.

---

## Solution (C++)

```cpp
#include "bits/stdc++.h"
using namespace std;

struct Node {
    int val;
    Node* next;
    Node(int x) : val(x), next(nullptr) {}
};

int minChanges(Node* head, int n) {
    vector<int> vec(n,0);
    Node* curr = head;
    for(int i=0;i<n;i++){
        vec[i] = curr->val;
        curr = curr->next;
    }
    sort(vec.begin(),vec.end());
    int res = 0;
    curr = head;
    for(int i=0;i<n;i++){
        if(vec[i] != curr->val){
            res++;
        }
        curr = curr->next;
    }

    return res;
}

int main() {
    int n;
    cin >> n;
    vector<int> values(n);
    for (int i = 0; i < n; ++i) {
        cin >> values[i];
    }
    
    Node* head = new Node(values[0]);
    Node* temp = head;
    for (int i = 1; i < n; ++i) {
        temp->next = new Node(values[i]);
        temp = temp->next;
    }
    
    int result = minChanges(head, n);
    cout << result << endl;
    
    while (head != nullptr) {
        Node* next = head->next;
        delete head;
        head = next;
    }
    
    return 0;
}

```


Happy coding! 🚀
