Solved

Given an array of strings `strs`, group all _anagrams_ together into sublists. You may return the output in **any order**.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example 1:**

```java
Input: strs = ["act","pots","tops","cat","stop","hat"]

Output: [["hat"],["act", "cat"],["stop", "pots", "tops"]]
```

**Example 2:**

```java
Input: strs = ["x"]

Output: [["x"]]
```

**Example 3:**

```java
Input: strs = [""]

Output: [[""]]
```

**Constraints:**

- `1 <= strs.length <= 1000`.
- `0 <= strs[i].length <= 100`
- `strs[i]` is made up of lowercase English letters.


## Solution

Use a hashmap to group by mapped chars to their occurence count.

```cpp
#include <set>
#include <vector>
#include <map>
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>> result;
        map<map<char,int>, vector<string>> waht;
        for(string str : strs){
            map<char, int> charmap;
            for (char c : str){
                if(charmap.find(c) == charmap.end()){
                    charmap[c] = 1;
                } else {
                    charmap[c] += 1;
                }
            }
            if(waht.find(charmap) == waht.end()){
                vector<string> temp;
                temp.push_back(str);
                waht[charmap] = temp;
            } else {
                waht[charmap].push_back(str);
            }
        }
        for(auto pair : waht){
            result.push_back(pair.second);
        }
        return result;
    }
};
```