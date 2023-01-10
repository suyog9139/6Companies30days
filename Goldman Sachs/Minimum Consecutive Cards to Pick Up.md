# Intuition
just store last occuraance of element into unordered map



# Code
```
class Solution {
public:
    int minimumCardPickup(vector<int>& cards) {
        unordered_map<int,int>mp;
        int ans=INT_MAX;
        for(int i=0; i<cards.size(); i++){
            if(mp.find(cards[i]) != mp.end()){
                int a = i-mp[cards[i]]+1;
                ans= min(ans,a);
            }
            mp[cards[i]]=i;

        }
        if(ans==INT_MAX){
            return -1;
        }
        return ans;

        
    }
};
```
