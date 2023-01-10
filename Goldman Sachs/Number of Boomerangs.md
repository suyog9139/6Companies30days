
# Code
```
class Solution {
public:
    int numberOfBoomerangs(vector<vector<int>>& points) {
        int ans =0;
        for(int i=0; i<points.size(); i++){
            unordered_map<int,int>mp;
            for(int j=0; j<points.size(); j++){
                    int m = (points[i][0]-points[j][0])*(points[i][0]-points[j][0]) + (points[i][1]-points[j][1])*(points[i][1]-points[j][1]);
                    mp[m]++;
            }
            for(auto it: mp){
                ans+=it.second*(it.second-1);
            }
        }
        return ans;
    }
};
```
