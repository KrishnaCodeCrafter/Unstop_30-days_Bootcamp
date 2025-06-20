## Problem Statement

Imagine you are running a small restaurant, and you want to evaluate the beauty of each group of customers who dine together at your restaurant.

Each group of customers can be represented as an array of integers, where each integer represents the amount of money each customer spent on their meal. The size of the array represents the number of customers in the group.

The beauty of a group can be defined as the Xth smallest amount of money spent by a customer in the group if it is negative. If there are fewer than X negative amounts, the beauty is 0.

For example, if a group of four customers spent $10, $-5, $20, and $-8, respectively, and we want to find the beauty of the subarray of size 3, we would first consider all subarrays of size 3 within this group:

$10, $-5, $20: the smallest negative value is $-5, so the beauty is $-5.

$-5, $20, $-8: the smallest negative value is $-8, so the beauty is $-8.

Therefore, the beauty of this group for subarrays of size 3 would be [$-5, $-8].

## Input Format
 
- The third line contains the value of N, which is an integer representing the number of customers.

- The fourth line contains a vector of N space-separted integers nums, representing the amount of money each customer spent on their meal.

## Output Format

- Print a numeric array of space-separted N - k + 1 numbers that represent the beauty of the subarrays in the array.

---

## Constraints
- **N == nums.length**  
- **1 ≤ N ≤ 10<sup>5</sup>**  
- **1 ≤ k ≤ N**  
- **1 ≤ x ≤ k**  
- **-50 ≤ nums[i] ≤ 50**  

---

## Sample Testcase 0

**Input:**
```bash
2
2
5
-1 -2 -3 -4 -5
```

**Output:**
```bash
-1 -2 -3 -4
```

### Explanation

With k = 2, there are 4 subarrays.


The second smallest negative number for [-1, -2] is -1.


The second smallest negative number for [-2, -3] is -2.


The second smallest negative number for [-3, -4] is -3.


The second smallest negative number for [-4, -5] is -4. 

## Sample Testcase 1

**Input:**
```bash
2
1
6
-3 1 2 -3 0 -3
```

**Output:**
```bash
-3 0 -3 -3 -3
```

### Explanation

5 subarrays of size k = 2 are present.


The first smallest negative number for the range [-3, 1] is -3.


There is no negative integer for [1, 2]; hence the beauty is 0.


The first smallest negative number for [2, -3] is -3.


The first smallest negative integer for [-3, 0] is -3.


The first smallest negative integer for the range [0, -3] is -3.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

vector<int> get_subarray_beauty(const vector<int>& nums, int k, int x) {
    int n = nums.size();
    multiset<int> st;
    vector<int> arr(n-k+1,0);
    int arrInd = 0;    
    int i=0,j=0;
    while(j<n){
        if(nums[j] < 0){
            st.insert(nums[j]);
        }
        if(j-i+1 == k){
            if(st.size() >= x){
                auto it = st.begin();
                advance(it,x-1);
                arr[arrInd] = *it;
            }arrInd++;
            if(nums[i] < 0){
                st.erase(st.find(nums[i]));
            }
            i++;
        }
        j++;
    }
    return arr;
}

int main() {
    int k, x, n;
    cin >> k >> x >> n;
    vector<int> nums(n);
    for (int i = 0; i < n; ++i) {
        cin >> nums[i];
    }
    vector<int> result = get_subarray_beauty(nums, k, x);
    for (const auto& val : result) {
        cout << val << " ";
    }
    return 0;
}

```


Happy coding! 🚀
