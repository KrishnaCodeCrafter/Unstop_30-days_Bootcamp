## Problem Statement

In the serene village of Blossomville, two dedicated gardeners, Lily and Rose, took pride in their flourishing gardens. Lily's garden was adorned with vibrant flowers, while Rose's garden was filled with aromatic herbs. On a beautiful sunny day, they decided to have a friendly competition to determine whose garden attracted more bees.

Lily created a list1 of N1 elements of the types of flowers she had and their quantities. Rose did the same with her herbs and created a list2 of N2 elements. They then compared their lists.

For each type of flower in Lily's garden, they compared its quantity with the quantity of the same type of herb in Rose's garden. If Lily had more of a particular flower than Rose had herbs, Lily noted down that flower in her notebook.

Lily ensured that her final list of flowers maintained the same order as they bloomed in her garden, showcasing her beautiful array of flowers.

Given two lists of integers representing the flower quantities in Lily's garden and the herb quantities in Rose's garden, you need to determine which flowers Lily should note down in her notebook based on the above criteria.

## Input Format

- The first line contains an integer N1, the number of flowers in Lily's garden.

- The second line contains N1 space-separated integers representing the quantities of each flower in Lily's garden.

- The third line contains an integer N2, the number of herbs in Rose's garden.

- The fourth line contains N2 space-separated integers representing the quantities of each herb in Rose's garden.

## Output Format

- Print the list of space-separated flowers that Lily should note down in her notebook, preserving the order as they appear in Lily's garden.

- If there are no such flowers, print -1.
---

## Constraints
- **1 ≤ N1 ≤ 10<sup>3</sup>**  
- **1 <= elementsoflist1 <= 10<sup>4</sup>**  
- **1 ≤ N2 ≤ 10<sup>3</sup>**  
- **1 <= elementsoflist2 <= 10<sup>4</sup>**  

---

## Sample Testcase 0

**Input:**
```bash
5
1 2 3 2 1
5
2 3 4 3 2
```

**Output:**
```bash
1 1
```

### Explanation

Flower 1 appears twice in Lily's garden but not at all in Rose's garden. Soit is included.<br>
Flower 2 appears twice in Lily's garden and twice in Rose's garden, so it is not included.<br>
Flower 3 appears once in Lily's garden and twice in Rose's garden, so it is not included.<br>
Flower 1 appears twice in Lily's garden but not at all in Rose's garden. Soit is included.<br>
The final list of flowers maintained the same order as they bloomed in Lily's garden

## Sample Testcase 1

**Input:**
```bash
3
4 5 6
3
1 2 3
```

**Output:**
```bash
4 5 6
```

### Explanation

All flowers in Lily's garden are more frequent than any herb in Rose's garden.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

vector<int> user_logic(int n1, vector<int>& flowers, int n2, vector<int>& herbs) {
    vector<int> vec;
    unordered_map<int,int> lily,rose;
    for(auto &x:flowers){
        lily[x]++;
    }
    for(auto &x:herbs){
        rose[x]++;
    }
    for(auto &x:flowers){
        if(lily[x] > rose[x]){
            vec.push_back(x);
        }
    }
    if(vec.size() == 0)
        vec.push_back(-1);
    return vec;
}

int main() {
    int n1, n2;
    cin >> n1;
    vector<int> flowers(n1);
    for (int i = 0; i < n1; ++i) {
        cin >> flowers[i];
    }
    cin >> n2;
    vector<int> herbs(n2);
    for (int i = 0; i < n2; ++i) {
        cin >> herbs[i];
    }

    vector<int> result = user_logic(n1, flowers, n2, herbs);

    if (result.size() == 1 && result[0] == -1) {
        cout << -1 << endl;
    } else {
        for (int i = 0; i < result.size(); ++i) {
            cout << result[i] << " ";
        }
        cout << endl;
    }
    return 0;
}

```


Happy coding! 🚀
