
# Code
```
class Solution {
public:
    int numberOfSubstrings(string s) {
        int count =0; 
        int n = s.size();
        int i=0; int j=0;
        // int a = 0;
        unordered_map<char,int>mp;
        while(j<n){
            mp[s[j]]++;
            while(mp['a']>0 && mp['b']>0 && mp['c']>0){
                count+=(n-j);
                mp[s[i]]--;
                i++;
            }
            j++;
        }
        // if(mp['a']==0 && mp['b']>0 && mp['c']>0){
        //     while(mp['a']>0 && mp['b']>0 && mp['c']>0){
        //         mp[s[i]]--;
        //         i++;
        //     }
        //     count+=i-1;
        // }
        // if(count<0) return 0;
        
        
        return count;
    }
};
```
