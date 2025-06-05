## Problem Statement

Alice’s mom bought n bags of chocolates numbered from 1 to N. The ith bag (1 <= i<= N) has ai chocolates.

Alice wants to share some of the chocolate bags with Bob such that both of them get an equal number of chocolates, but she is not able to divide them in such a way. Now, she wonders if it is even possible to do so.
Help Alice find out if the bags can be divided between her and Bob such that both of them get an equal number of chocolates.

Remember you cannot divide the chocolate inside the bags. 
## Input Format
 
- The first line of the input contains a single integer N denoting the number of bags that Alice’s mom bought.
- The second line contains N space-separated integers A1, A2, …, An – the number of chocolates in each bag.

## Output Format

- If it is possible to divided the chocolate bags in two parts with equal chocolates, print “YES” (without quotes). Otherwise, print “NO” (without quotes).

---

## Constraints
- **1 ≤ N ≤ 5*10<sup>2</sup>**  
- **1 ≤ A<sub>i</sub> ≤ 10<sup>2</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
4
1 2 3 3
```

**Output:**
```bash
NO
```

### Explanation

It is not possible to divid the chocolate bags in two parts with equal chocolates.

## Sample Testcase 1

**Input:**
```bash
4
1 2 3 4 
```

**Output:**
```bash
YES
```

### Explanation

The total number of chocolates is 1 + 2 + 3 + 4 = 10 <br>
Since 10 is even, it's possible to divide the chocolates equally.<br>
One possible division is:<br>
Alice: 1,4 (total = 5).<br>
Bob: 2,3 (total = 5).

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

void can_partition_chocolates(int n, vector<int>& chocolates) {
    long long total = 0;
    for(auto &x:chocolates){
        total += x;
    }

    if(total&1){
        cout<<"NO"<<endl;
        return ;
    }
    int target = total/2;
    vector<bool> dp(target+1,0);
    dp[0] = true;
    for(int i=0;i<n;i++){
        for(int j=target;j>=chocolates[i];j--){
            dp[j] = dp[j] || dp[j-chocolates[i]];
        }
    }
    cout<<(dp[target] ? "YES" : "NO")<<endl;
}

int main() {
    int n;
    cin >> n;
    vector<int> chocolates(n);
    for (int i = 0; i < n; ++i) {
        cin >> chocolates[i];
    }
    can_partition_chocolates(n, chocolates);
    return 0;
}

```


Happy coding! 🚀
