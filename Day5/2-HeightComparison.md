## Problem Statement

You are given a line of N people, each with a certain height, represented by the array height. You are also given a number K, which indicates the number of people you can view at once as you move through the line from the front to the rear.

Your task is to find the tallest person among every group of K consecutive people as you slide the viewing window from the start of the line to the end. For each position of the viewing window, record the height of the tallest person visible.

## Input Format
 
- The first line of input contains two space-separated integers N and K, where N is the total number of people in the line and K is the number of people visible at one time.

- The second line of input contains N space-separated integers representing the array height[], where height[i] denotes the height of the ith person.

## Output Format

- Print a space-separated list of integers representing the tallest person in each group of K consecutive people as you move from the front to the rear of the line.


---

## Constraints
- **K ≤ N ≤ 10<sup>5</sup>**  
- **1 ≤ K ≤ N**  
- **1 ≤ height[i] ≤ 10<sup>8</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
8 3
1 3 1 2 5 3 6 7
```

**Output:**
```bash
3 3 5 5 6 7
```

### Explanation

The first group [1, 3, 1] has the tallest person 3.<br>
The second group [3, 1, 2] has the tallest person 3.<br>
The third group [1, 2, 5] has the tallest person, 5.<br>
The fourth group [2, 5, 3] has the tallest person, 5.<br>
The fifth group [5, 3, 6] has the tallest person, 6.<br>
The sixth group [3, 6, 7] has the tallest person, 7.<br>

Therefore, the output will be 3, 3, 5, 6, 7.

## Sample Testcase 1

**Input:**
```bash
5 2
4 2 7 1 8
```

**Output:**
```bash
4 7 7 8
```

### Explanation

The first group [4, 2] has the tallest person 4.<br>
The second group [2, 7] has the tallest person 7.<br>
The third group [7, 1] has the tallest person 7.<br>
The fourth group [1, 8] has the tallest person 8.<br>

Therefore, the output will be 4, 7, 7, 8.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

vector<int> find_tallest(int N, int K, vector<int> height) {
    vector<int> result;
    deque<int> dq;
    for(int i=0;i<N;i++){
        while(!dq.empty() && dq.front() <= i-K){
            dq.pop_front();
        }
        while(!dq.empty() && height[dq.back()] < height[i]){
            dq.pop_back();
        }
        dq.push_back(i);
        if(i >= K-1){
            result.push_back(height[dq.front()]);
        }

    }

    return result;
}

int main() {
    int N, K;
    cin >> N >> K;
    vector<int> height(N);
    for (int i = 0; i < N; i++) {
        cin >> height[i];
    }
    vector<int> result = find_tallest(N, K, height);
    for (int i = 0; i < result.size(); i++) {
        cout << result[i] << " ";
    }
    cout << endl;
    return 0;
}

```


Happy coding! 🚀
