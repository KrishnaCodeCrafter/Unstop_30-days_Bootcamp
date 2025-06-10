## Problem Statement

In the city of Unstop, there are ( n ) citizens known as Unstoppables located at positions ( A[i] ) along a straight avenue. Additionally, there are ( m ) precious skill spells located at positions ( B[i] ) scattered along the same avenue.

Each Unstoppable must collect one skill spell and deliver it to the central museum located at position ( p ) on the avenue.

Each Unstoppable moves at a speed of one unit distance per second. If multiple Unstoppables reach a skill spell simultaneously, only one can claim it, and the others must find another skill spell.

Once a skill spell is taken, it cannot be claimed by another Unstoppable.

The goal is to determine the minimum time required for all ( n ) Unstoppables to deliver their collected skill spells to the museum.

## Input Format

- The first line contains three integers ( n ), ( m ), and ( p ), the number of Unstoppables, the number of skill spells, and the position of the museum, respectively.

- The second line contains ( n ) space-separated integers ( A[i] ) the positions of the Unstoppables.

- The third line contains ( m ) space-separated  integers ( B[i] ) the positions of the skill spells.

 

## Output Format

- Print a single integer the minimum time required for all ( n ) Unstoppables to deliver their skill spells to the museum.


---

## Constraints

- **1 <= n, m <= 10<sup>5</sup>**

- **1 <= A[i], B[i], p <= 10<sup>9</sup>**
---

## Sample Testcase 0

**Input:**
```bash
2 3 5
1 4
3 6 8
```

**Output:**
```bash 
4
```

### Explanation

Unstoppable at position 1 goes to skill spell at position 3 and then to the museum at position 5: Time = ( |1 - 3| + |3 - 5| = 2 + 2 = 4 )

Unstoppable at position 4 goes to skill spell at position 6 and then to the museum at position 5: Time = ( |4 - 6| + |6 - 5| = 2 + 1 = 3 )

Minimum time is the maximum of these times: ( max(4, 3) = 4 )

## Sample Testcase 1

**Input:**
```bash
3 3 10
1 5 7
3 6 8
```

**Output:**
```bash
9
```
### Explanation



Unstoppable at position 1 goes to skill spell at position 3 and then to the museum at position 10: Time = ( |1 - 3| + |3 - 10| = 2 + 7 = 9 )

Unstoppable at position 5 goes to skill spell at position 6 and then to the museum at position 10: Time = ( |5 - 6| + |6 - 10| = 1 + 4 = 5 )

Unstoppable at position 7 goes to skill spell at position 8 and then to the museum at position 10: Time = ( |7 - 8| + |8 - 10| = 1 + 2 = 3 )

Minimum time is the maximum of these times: ( max(9, 5, 3) = 9 )

---

## Solution (C++)

```cpp

#include <iostream>
#include <vector>
#include <algorithm>
#include <cmath>
using namespace std;

bool check(int n, int m, int p, vector<int>& unstoppables, vector<int>& spells,int mid){
    int j=0;
    for(int i=0;i<n;i++){
        if(abs(unstoppables[i] - spells[j]) + abs(spells[j] - p) > mid)
            return false;
        j++;
    }
    return true;
}

int min_delivery_time(int n, int m, int p, vector<int>& unstoppables, vector<int>& spells) {
    int low = 0;
    int res = -1;
    int high = 1e9;

    while(low <= high){
        int mid = low + (high - low)/2;
        if(check(n,m,p,unstoppables,spells,mid)){
            res = mid;
            high = mid-1;
        }else
            low = mid+1;
    }

    return res;  // Placeholder return statement
}

int main() {
    int n, m, p;
    cin >> n >> m >> p;
    
    vector<int> unstoppables(n);
    for(int i = 0; i < n; ++i) {
        cin >> unstoppables[i];
    }

    vector<int> spells(m);
    for(int i = 0; i < m; ++i) {
        cin >> spells[i];
    }
    
    int result = min_delivery_time(n, m, p, unstoppables, spells);
    cout << result << endl;

    return 0;
}


```


Happy coding! 🚀
