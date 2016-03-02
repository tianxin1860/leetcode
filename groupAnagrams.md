
* Title: LeetCode/49/Group Anagrams
* Author:TianXin
* 2016-03-02

#Question:

Given an array of strings, group anagrams together.

For example, given: ["eat", "tea", "tan", "ate", "nat", "bat"], 
	Return:

	[
	["ate", "eat","tea"],
	["nat","tan"],
	["bat"]
	]


```
class Solution {
	public:
		vector<vector<string>> groupAnagrams(vector<string>& strs) {
			vector< vector<string> > result;
			vector<string> tmp;
			unordered_map<string, vector<int> > map;
			for(int i=0; i<strs.size(); i++) {
				string key = strs[i];
				sort(key.begin(), key.end());
				map[key].push_back(i);
			}
			for(unordered_map<string, vector<int> >::iterator it = map.begin(); it!=map.end(); it++) {
				vector<int> index = (*it).second;
				for(vector<int>::iterator it = index.begin(); it!=index.end(); it++) {
					tmp.push_back(strs[*it]);
				}
				sort(tmp.begin(), tmp.end());
				result.push_back(tmp);
				tmp.clear();
			}
			return result;
		}
};
```

