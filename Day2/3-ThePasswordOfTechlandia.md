## Problem Statement

In the kingdom of Techlandia, a powerful sorcerer named Zael has hidden treasures in an enchanted vault, and the only way to open it is by entering a secret password. However, Zael has set two conditions for the password:

- Every number in the password must appear an even number of times.
- At least one number must appear exactly twice.

To solve the puzzle, adventurers must verify if the password meets these conditions and also identify the most frequent element in the password. If they succeed, the vault will open, revealing the treasures hidden inside. The fate of Techlandia’s treasures depends on solving this magical riddle!
## Input Format

- The first line contains an integer N, representing the number of elements in the password.

- The second line contains N space-separated integers, representing the elements of the password array.

## Output Format

- Print "VALID" if the password satisfies the conditions; otherwise, print "INVALID".

- In either case, also print the most frequent element in the password. If there are multiple elements with the same highest frequency, print the smallest one.

---

## Constraints

- **2 ≤ N ≤ 10<sup>6</sup>**  
- **1 ≤ Ai ≤ 10<sup>7</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
6
2 2 4 4 4 4
```

**Output:**
```bash
VALID
4
```

### Explanation

All elements appear an even number of times.<br>
The number 4 appears the most frequently (4 times).<br>
The number 2 appears exactly twice, satisfying the requirement of at least one element appearing exactly twice.

## Sample Testcase 1

**Input:**
```bash
5
1 1 2 2 3
```

**Output:**
```bash
INVALID
1
```

### Explanation

The frequencies of elements are 1:2, 2:2, and 3:1.<br>
The number 3 appears an odd number of times, violating the frequency condition.<br>
The most frequent element is 1 (or 2 since both appear twice, but the smallest is selected).

---

## Solution (C++)

```cpp
#include "bits/stdc++.h"
using namespace std;

void validate_password(const vector<int>& password, string& result, int& most_frequent_element) {
    map<int,int> umap;
    for(auto &x:password){
        umap[x]++;
    }
    int ele = umap.begin()->first;
    int freq = umap.begin()->second;
    bool hasOdd = false;
    bool eq2 = false;
    for(auto &x:umap){
        if(x.second & 1){
            hasOdd = true;
        }
        if(!eq2 && x.second == 2){
            eq2 = true;
        }
        if(freq < x.second){
            ele = x.first;
            freq = x.second;
        }
    }
    most_frequent_element = ele;
    if(!hasOdd && eq2) result = "VALID";
    else    result = "INVALID";

}

int main() {
    int N;
    cin >> N;
    vector<int> password(N);
    for (int i = 0; i < N; ++i) {
        cin >> password[i];
    }
    string validation_result;
    int most_frequent_element;
    validate_password(password, validation_result, most_frequent_element);
    cout << validation_result << '\n';
    cout << most_frequent_element << '\n';
    return 0;
}
```


Happy coding! 🚀
