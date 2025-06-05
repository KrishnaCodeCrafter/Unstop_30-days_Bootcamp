## Problem Statement

In the ancient village of Aeloria, there was a mystical book known as the Codex of Frequencies, said to contain powerful knowledge hidden within the frequencies of letters. These letters had unique magical properties, with odd frequencies being especially potent. Elara, a young and talented apprentice, was tasked with deciphering the book’s secrets.

The key to unlocking the book's power lay in the odd frequencies of the letters. Elara needed to analyze the frequencies and apply a set of rules to determine their magical significance:

- If exactly three letters had odd frequencies, she would calculate the product of those frequencies to reveal a hidden spell.
- If there were more than three odd frequencies, she would select the three largest ones and find their product for a stronger magic.
- If there were fewer than three odd frequencies, Elara had to identify the smallest odd frequency, or return -1 if there were no odd frequencies at all.

As Elara carefully studied the letters, she realized the importance of sorting the frequencies in descending order. In case of a tie in frequency, she would need to break it by considering the alphabetical order of the letters.

## Input Format

- The first line of input contains a single string str consisting of lowercase English letters.


## Output Format

- If exactly three characters have odd frequencies, print each character and its frequency (sorted by frequency and then alphabetically), followed by their product.

- If more than three characters have odd frequencies, print the three largest odd frequencies (sorted by frequency and then alphabetically), followed by their product.

- If fewer than three odd frequencies exist, print the smallest odd frequency, or -1 if none exist.

---

## Constraints

- **2 <= |str| <= 10<sup>8</sup>**

---

## Sample Testcase 0

**Input:**
```bash
aabcccddd
```

**Output:**
```bash
c 3
d 3
b 1
9
```

### Explanation

The string aabcccddd has odd-frequency characters: b: 1, c: 3, d: 3. After sorting by descending frequency, the top 3 are:<br>
c 3 <br>
d 3 <br>
b 1 <br>
Their product is 3 × 3 × 1 = 9.

## Sample Testcase 1

**Input:**
```bash
mmoppqrr
```

**Output:**
```bash
o 1
```

### Explanation

The string mmoppqrr has odd-frequency characters: o: 1 and q: 1. Since there are fewer than 3 odd frequencies, the lexicographically smallest character (o) with the smallest odd frequency (1) is printed.

---

## Solution (C++)

```cpp

#include "bits/stdc++.h"
using namespace std;

bool comp(pair<int,char>& p1,pair<int,char> &p2){
    if(p1.first > p2.first) return true;
    if(p1.first == p2.first)    return p1.second < p2.second;
    return false;
}

bool comp2(pair<int,char>& p1,pair<int,char> &p2){
    if(p1.first < p2.first) return true;
    if(p1.first == p2.first)    return p1.second < p2.second;
    return false;
}

void user_logic(const string& s) {
    unordered_map<char,int> umap;
    for(int i=0;i<s.size();i++){
        umap[s[i]]++;
    }    

    vector<pair<int,char>> vec;
    for(auto &x:umap){
        if(x.second&1)
            vec.push_back({x.second,x.first});
    }
    if(vec.size() == 0){
        cout<<-1<<endl;
        return ;
    }
    if(vec.size() < 3){
        sort(vec.begin(),vec.end(),comp2);
        cout<<vec[0].second<<" "<<vec[0].first<<endl;
    }else{
        sort(vec.begin(),vec.end(),comp);
        long long pro = 1;
        for(int i=0;i<3;i++){
            cout<<vec[i].second<<" "<<vec[i].first<<endl;
            pro *= vec[i].first;
        }
        cout<<pro;
    }
}

int main() {
    string s;
    getline(cin, s);
    
    user_logic(s);
    
    return 0;
}

```


Happy coding! 🚀
