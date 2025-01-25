https://neetcode.io/problems/duplicate-integer

[CPP](CPP.md) solution with an [std unordered_set](std%20unordered_set.md)
```cpp
class Solution {

public:

    bool hasDuplicate(vector<int>& nums) {
        std::unordered_set<int> ns;
        for(int n : nums){
            if(ns.find(n) != ns.end()){
                return true;
            }
            ns.insert(n);
        }
        return false;
    }
};
```