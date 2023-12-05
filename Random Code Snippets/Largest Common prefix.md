#### Question-
**Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string `""`.

**Example 1:**

**Input:** strs = ["flower","flow","flight"]
**Output:** "fl"

**Example 2:**

**Input:** strs = ["dog","racecar","car"]
**Output:** ""
**Explanation:** There is no common prefix among the input strings.

**Constraints:**

- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` consists of only lowercase English letters.**


### Answer-

This code implements the longestCommonPrefix function that takes a list of strings v as input and returns the longest common prefix of all the strings. Here is an explanation of how the code works:

1. Initialize an empty string ans to store the common prefix.
2. Sort the input list v lexicographically. This step is necessary because the common prefix should be common to all the strings, so we need to find the common prefix of the first and last string in the sorted list.
3. Iterate through the characters of the first and last string in the sorted list, stopping at the length of the shorter string.
4. If the current character of the first string is not equal to the current character of the last string, return the common prefix found so far.
5. Otherwise, append the current character to the ans string.
6. Return the ans string containing the longest common prefix.

Note that the code assumes that the input list v is non-empty, and that all the strings in v have at least one character. If either of these assumptions is not true, the code may fail.

```C++
class Solution {
public:
    string longestCommonPrefix(vector<string>& v) {
        string ans="";
        sort(v.begin(),v.end());
        int n=v.size();
        string first=v[0],last=v[n-1];
        for(int i=0;i<min(first.size(),last.size());i++){
            if(first[i]!=last[i]){
                return ans;
            }
            ans+=first[i];
        }
        return ans;
    }
};
```

