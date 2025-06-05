## Problem Statement

King Luther has an army with N soldiers, each with an ID between 1 and N. The king wants to know how many soldiers in his army are "brave."

A soldier is considered "brave" if their ID has exactly two factors (or Divisors) and is not a perfect square.

Since King Luther is busy with his duties, he needs your help to count the number of "brave" soldiers in his army.

Your task is to count how many soldiers have "brave" IDs according to the criteria.

## Input Format

- The input contains only one integer N denoting the number of soldiers in the army.

## Output Format

- Print the count of brave soldiers in the army.

---

## Constraints
- **1 ≤ N ≤ 10<sup>6</sup>**  
---

## Sample Testcase 0

**Input:**
```bash
20
```

**Output:**
```bash
8
```

### Explanation

Only 8 numbers from 1 to 20 follow the brave criteria those are : 


2, 3, 5, 7, 11, 13, 17, 19.


It can be shown no number other than these follows the brave criteria.

## Sample Testcase 1

**Input:**
```bash
100
```

**Output:**
```bash
25
```

### Explanation

Only 25 numbers from 1 to 100 follow the brave criteria those are : 


2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97. 

---


## Solution (C++)

```cpp
#include "bits/stdc++.h"
using namespace std;

int count_brave_soldiers(int n) {
    vector<bool> vec(n+1,true);
    vec[0] = vec[1] = false;
    for(int i=2;i<=n;i++){
        if(vec[i]){
            for(int j=2;j*i <= n;j++){
                vec[j*i] = false;
            }
        }
    }
    
    int cnt = 0;
    for(int i=0;i<=n;i++){
        if(vec[i])
            cnt++;
    }
    
    return cnt;
}

int main() {
    int n;
    cin >> n;
    int result = count_brave_soldiers(n);
    cout << result << endl;
    return 0;
}
```


Happy coding! 🚀
