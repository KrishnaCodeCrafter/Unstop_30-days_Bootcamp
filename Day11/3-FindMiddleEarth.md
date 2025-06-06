## Problem Statement

You are given two sorted arrays a1 and a2 of size m and n respectively. Now we combine the values of these two arrays to make a mega array. The resulting mega array is also sorted in nature.

Your task is to find the median of this mega array.

## Input Format

- Each Input has three lines, containing space-separated integers.
- The first line contains 2 values m and n respectively.
- The second line contains m numbers that signify nums1.
- The third line contains n numbers that signify nums2.

## Output Format

- Return a Double data type number which is the median of two arrays.

---

## Constraints

- **nums1.length == m**
- **nums2.length == n**
- **0 <= m <= 10^6**
- **0 <= n <= 10^6**

---

## Sample Testcase 0

**Input:**
```bash
2 1
1 3
2
```

**Output:**
```bash
2.0
```

### Explanation

Resulting array:- [1,2,3]<br>
Median of this array is 2.00000.

## Sample Testcase 1

**Input:**
```bash
2 2
1 3
2 4
```

**Output:**
```bash
2.5
```
### Explanation

Resulting array:- [1,2,3,4]<br>
Median of this array is ((2+3)/2) = 2.50000.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

double find_middle_earth(const vector<int>& nums1, const vector<int>& nums2) {
    int n = nums1.size();
    int m = nums2.size();
    if(n > m){
        return find_middle_earth(nums2,nums1);
    }

    int low = 0;
    int high = n;
    while(low <= high){
        int Px = low + (high-low)/2;
        int Py = (n+m+1)/2 - Px;

        int x1 = (Px == 0)? INT_MIN : nums1[Px-1];
        int x2 = (Py == 0)? INT_MIN : nums2[Py-1];
        int x3 = (Px == n)? INT_MAX : nums1[Px];
        int x4 = (Py == m)? INT_MAX : nums2[Py];
    
        if(x1 <= x4 && x2 <= x3){
            if((n+m)&1){
                return max(x1,x2);
            }return (max(x1,x2)+min(x3,x4))/2.0;
        }

        if(x1 > x4){
            high = Px-1;
        }else
            low = Px+1;
    }
    return -1;
}

int main() {
    int m, n;
    cin >> m >> n;
    vector<int> nums1(m);
    vector<int> nums2(n);
    for (int i = 0; i < m; ++i) {
        cin >> nums1[i];
    }
    for (int i = 0; i < n; ++i) {
        cin >> nums2[i];
    }
    cout<<fixed<<setprecision(1)<<find_middle_earth(nums1, nums2);
    return 0;
}

```


Happy coding! 🚀
