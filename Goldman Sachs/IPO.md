# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    int findMaximizedCapital(int k, int w, vector<int>& profits, vector<int>& capital) {
        vector<pair<int,int>>v;
        for(int i=0; i<capital.size(); i++){
            v.push_back({capital[i],profits[i]});
        }
        sort(v.begin(),v.end());
        int i=0;
        priority_queue<int>pq;
        while(i<v.size() && k){
            if(w>=v[i].first) pq.push(v[i++].second);
            else{
                if(pq.empty()) return w;
                k--;
                w+=pq.top();
                pq.pop();
            }            
        }
        while(k-- && !pq.empty()){
            w+=pq.top();
            pq.pop();
        }
        return w;
    }
};
```
