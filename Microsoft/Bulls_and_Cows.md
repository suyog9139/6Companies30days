# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
Basic approach 
1. using for loop find bulls, hashmap all digits in secret
2. using second for loop find all same number and substract bulls from it for cow 


# Code
```
class Solution {
public:
    string getHint(string secret, string guess) {
        unordered_map<int,int>mp;
        int B=0;
        for(int i=0; i<secret.length(); i++){
            if(secret[i]==guess[i]) B++;
            mp[secret[i]]++;
        }
        int C=0;
        for(int i=0; i<secret.length(); i++){
            if(mp[guess[i]]>0){
                C++;
                mp[guess[i]]--;
            }
        }
        C=C-B;
        string ans= to_string(B)+"A"+to_string(C)+"B";
        return ans;
    }
};
```
