## Problem Statement

In a bustling city, a delivery drone was assigned a special task to navigate through a sequence of n+1 points on its route. The drone's journey began at point 0, where its altitude was precisely 0 meters above sea level.

As the drone traveled, it experienced changes in altitude due to urban landscapes, weather conditions, and delivery tasks. For every segment between points i and i+1, where 0 ≤ i < n, the change in altitude was represented by an integer array called change, of length n. The value change[i] denoted the net change in altitude between points i and i+1. A positive value represented an ascent, while a negative value indicated a descent.

However, the drone's battery and design imposed a unique constraint: if the altitude at any point along the journey became negative, the drone would activate its emergency hover mode, resetting the altitude to 0 meters at that point before continuing its journey.

The drone's mission is to determine the maximum altitude it reached during its journey, considering this unique altitude-resetting mechanism.

## Input Format

- The first line contains an integer N, representing the number of elements in the array change.

- The second line contains N space-separated integers, the elements of the array change, where change[i] denotes the net change in altitude between points i and i+1. 

## Output Format

- Print a single integer, the maximum altitude the drone reached during its journey.

---

## Constraints

- **1 <= N <= 10<sup>7</sup>**

- **-10<sup>8</sup> <= change[i] <= 10<sup>8</sup>**

---

## Sample Testcase 0

**Input:**
```bash
5
-4 2 3 -5 6
```

**Output:**
```bash 
6
```

### Explanation

The journey begins at altitude 0.<br>
After the first segment: Altitude = 0 + (-4) = -4 → resets to 0 due to hover mode.<br>
After the second segment: Altitude = 0 + 2 = 2.<br>
After the third segment: Altitude = 2 + 3 = 5.<br>
After the fourth segment: Altitude = 5 + (-5) = 0 (no reset needed, already 0).<br>
After the fifth segment: Altitude = 0 + 6 = 6.<br>
The maximum altitude reached is 6.


## Sample Testcase 1

**Input:**
```bash
6
3 -2 4 -8 5 2
```

**Output:**
```bash
7
```
### Explanation

The journey begins at altitude 0.<br>
After the first segment: Altitude = 0 + 3 = 3.<br>
After the second segment: Altitude = 3 + (−2) = 1.<br>
After the third segment: Altitude = 1 + 4 = 5.<br>
After the fourth segment: Altitude = 5 + (−8) = −3→resets to 0 due to hover mode.<br>
After the fifth segment: Altitude = 0 + 5 = 5.<br>
After the sixth segment: Altitude = 5 + 2 = 7.<br>
The maximum altitude reached is 7.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

long long maximum_altitude(const vector<int>& change) {
    long long sum = 0;
    long long mxsum = 0;
    for(auto& x:change){
        sum += x;
        if(sum < 0)
            sum = 0;
        mxsum = max(sum,mxsum);
    }
    return mxsum;
}

int main() {
    int n;
    cin >> n;
    vector<int> change(n);
    for (int i = 0; i < n; ++i) {
        cin >> change[i];
    }
    
    long long result = maximum_altitude(change);
    cout << result << endl;
    return 0;
}

```


Happy coding! 🚀
