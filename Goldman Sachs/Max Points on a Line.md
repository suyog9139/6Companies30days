# Intuition
handle seperately edge cases like x1-x2==0 and y1-y2==0;
use slope approch  for double varible  
y2-y1/x2-x1
use map to store slope and refresh it after one is check

# Complexity
- Time complexity:
O(n^2)

- Space complexity:
O(n)

# Code
```
class Solution {
public:
    int maxPoints(vector<vector<int>>& points) {
        
        int ans =0;
        int c=0;
        int p2 =0;
        for(int i=0; i<points.size()-1; i++){
            unordered_map<double,int>mp;
            for(int j=i+1;j<points.size(); j++){
                
                if(points[j][0]-points[i][0]==0) {
                    mp[0]++;
                } 
                else if(points[i][1]-points[j][1]!=0 ){
                    double a1 = points[j][0]-points[i][0];
                    double a2 = points[j][1]-points[i][1];
                    double m = a2/a1;
                    mp[m]++;
                }
                else{
                    mp[100]++;
                }
            }
            for(auto  it: mp){
               ans = max(ans, it.second);
            }


        }
        return ans+1;

    }
};
```
