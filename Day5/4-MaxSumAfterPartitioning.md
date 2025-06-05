## Problem Statement

You are given an integer array of size N. Your task is to partition this array into contiguous subarrays, where each subarray contains at most K elements. After partitioning, replace every element in each subarray with the largest value from that subarray.

Next, calculate the maximum possible sum of the transformed array. Let this maximum sum be M.

Finally, find and display the count of prime numbers that are less than or equal to M.

Test cases are generated such that the answer fits within a 32-bit integer.

## Input Format
 
- The first line contains an integer N, which represents the size of the array.
- The second line contains N space-separated integers representing the elements of the array.
- The third line contains an integer K, which is the maximum allowed size for each subarray.

## Output Format

- Print a single integer, representing the count of prime numbers less than or equal to M, where  M is the maximum sum after partitioning the array.


---

## Constraints
- **1 ≤ Arr.length ≤ 5*10<sup>2</sup>**  
- **0 ≤ Arr[i] ≤ 10<sup>6</sup>**  
- **1 ≤ K ≤ Arr.length**  

---

## Sample Testcase 0

**Input:**
```bash
7
1 15 7 9 2 5 10
3
```

**Output:**
```bash
23
```

### Explanation

Split the array [1, 15, 7, 9, 2, 5, 10] into contiguous subarrays of length up to 3.<br>
Subarray 1: [1, 15, 7] <br>
After transformation: [15, 15, 15]<br> 
Subarray 2: [2, 5, 10] <br>
After transformation: [10, 10, 10]<br>
Subarray 3: [9] <br>
After transformation: [9]<br>
Overall sum = 15+15+15+10+10+10+9 = 84<br>
Number of Primes less than equal to 84  = 23<br>

## Sample Testcase 1

**Input:**
```bash
1
1
1
```

**Output:**
```bash
0
```

### Explanation

The array contains only one element, so the maximum sum after partitioning is 1. The count of prime numbers less than or equal to 1 is 0, as there are no primes less than or equal to 1.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;
int max_sum_after_partitioning(vector<int>& arr, int k) {
    int n = arr.size();
    vector<int> dp(n,0);

    for(int i=0;i<n;i++){
        int currmax = 0;
        for(int j=1;j<=k && i-j+1 >= 0;j++){
            currmax = max(currmax,arr[i-j+1]);
            int rightSub = currmax * j;
            if(i-j < 0){
                dp[i] = max(dp[i],rightSub);
            }else{
                dp[i] = max(dp[i] , dp[i-j] + rightSub);
            }
        }
    }

    return dp[n-1];
}

int sieve_of_eratosthenes(int n) {
    vector<int> prime(n+1,true);
    int cnt = 0;
    prime[0] = prime[1] = false;
    for(int i=2;i*i<=n;i++){
        if(prime[i]){
            for(int j=i*i;j<=n;j+=i){
                prime[j] = false;
            }
        }
    }
    for(int i=2;i<=n;i++){
        if(prime[i])
            cnt++;
    }
    return cnt;
}

int main() {
    int n, k;
    cin >> n;
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    cin >> k;
    
    // Call user logic functions
    int max_sum = max_sum_after_partitioning(arr, k);
    int prime_count = sieve_of_eratosthenes(max_sum);
    
    // Print the result
    cout << prime_count << endl;
    return 0;
}

```


Happy coding! 🚀
