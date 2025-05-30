## Problem Statement

Alice is given an array of non-negative integers containing N elements. Your task is to return the total number of subarrays that contain only Tribonacci numbers.

Tribonacci numbers are defined by the Tribonacci Series:

- The first three numbers are 0,1,1.
- Each subsequent number is the sum of the previous three numbers, i.e., the Nth number is calculated as Tribonacci(N)=Tribonacci(N−1)+Tribonacci(N−2)+Tribonacci(N−3).

To avoid integer overflow, take the result modulo 10^9+7.

## Input Format

- The first line contains an integer N, representing the size of the array,

- The second line contains N space-separated integer, representing the array arr.

## Output Format

- Return the total number of subarrays that consist solely of Tribonacci numbers.

---

## Constraints
- **1 ≤ N ≤ 10<sup>5</sup>**  
- **1 ≤ arr[i] ≤ 10<sup>5</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
5
0 1 1 2 4
```

**Output:**
```bash
15
```

### Explanation

The total number of Tribonacci subarrays is 15: [0], [0,1], [0,1,1], [0,1,1,2], [0,1,1,2,4], [1], [1,1], [1,1,2], [1,1,2,4], [1], [1,2], [1,2,4], [2], [2,4], [4]

## Sample Testcase 1

**Input:**
```bash
5
0 1 1 105 3
```

**Output:**
```bash
6
```

### Explanation

The total number of Tribonacci subarrays is 6: [0], [0,1], [0,1,1], [1], [1,1], [1] (Note that numbers 105 and 3 are not Tribonacci numbers, so they break the valid subarrays)


---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;
int MOD = 1e9+7;

void calculate(unordered_set<int>& st){
    long long a=0,b=1,c=1;
    st.insert(a); 
    st.insert(b);
    while(true){
        long long temp = a+b+c;
        if(temp > 100001)   break;
        st.insert(temp);
        a = b;
        b = c;
        c = temp;
    } 
}

void count_tribonacci_subarrays(int n, const vector<int>& arr) {
    unordered_set<int> st;
    calculate(st);
    long long ans = 0;
    int l=0,r=0;
    while(r<n){
        if(st.find(arr[r]) != st.end()){
            ans = (ans+r-l+1)%MOD;
        }else{
            l=r+1;
        }
        r++;
    }
    cout<<ans<<endl;
}

int main() {
    int n;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; ++i) {
        cin >> arr[i];
    }
    count_tribonacci_subarrays(n, arr);
    return 0;
}



```


Happy coding! 🚀
