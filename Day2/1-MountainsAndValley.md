## Problem Statement

Given a linked list, determine if it exhibits a continuous mountain and valley pattern.

A continuous mountain and valley pattern is characterized by a sequence of nodes where the values consistently alternate between increasing and decreasing.

Note: if only one node, then return 1.

## Input Format

- The first line contains an integer 'n' representing the number of nodes in the linked list.

- The second line contains 'n' space-separated integers representing the values of the nodes in the linked list.

## Output Format

- '1' indicates that the linked list follows a continuous mountain and valley pattern.

- '0' indicates the linked list does not follow the continuous mountain and valley pattern.

---

## Constraints
- **1 ≤ n ≤ 4*10<sup>3</sup>**  
- **0 ≤ elements of linkedlist ≤ 10<sup>4</sup>**  
---

## Sample Testcase 0

**Input:**
```bash
5
1 2 3 2 1
```

**Output:**
```bash
0
```

### Explanation

1 -> 2 -> 3 -> 2 -> 1 <br>
As 1 to 3 is increasing, that means values consistently do not alternate between increasing and decreasing. So the answer is 0.

## Sample Testcase 1

**Input:**
```bash
5
1 2 1 2 1   
```

**Output:**
```bash
1
```

### Explanation

1 -> 2 -> 1 -> 2 -> 1 <br>
As values consistently alternate between increasing and decreasing. So the answer is 1

---

## Solution (C++)

```cpp
#include <iostream>
#include <vector>

struct Node {
    int data;
    Node *next;
};

class LinkedList {
public:
    Node *head, *tail;
    LinkedList() : head(nullptr), tail(nullptr) {}
    void push(int data) {
        Node *new_node = new Node{data, nullptr};
        if (head == nullptr) {
            head = new_node;
            tail = new_node;
        } else {
            tail->next = new_node;
            tail = new_node;
        }
    }
};

int user_logic(LinkedList &list) {
    Node* p = list.head;
    if(p == nullptr || p->next == nullptr)
        return 1;
    Node* q = p->next;
    bool flag = (p->data - q->data >= 0) ? true : false;
    while(q != nullptr){
        bool check = (q->data - p->data >= 0) ? true : false;
        p=p->next;
        q=q->next;
        if(check == flag)
            return 0;
        flag = check;
    } 
    return 1;


    return 0;
}

int main() {
    int n;
    std::cin >> n;
    LinkedList ll;
    for (int i = 0; i < n; ++i) {
        int value;
        std::cin >> value;
        ll.push(value);
    }
    int result = user_logic(ll);
    std::cout << result << std::endl;
    return 0;
}
```


Happy coding! 🚀
