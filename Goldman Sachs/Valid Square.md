# Intuition
just using distance formula to calculate distance of side and diagonal
as we know all side and all digonals are equal in square so 4 side have same length and 2 have same length

# Code
```
class Solution {
public:
    bool validSquare(vector<int>& p1, vector<int>& p2, vector<int>& p3, vector<int>& p4) {
        unordered_map<int,int>mp;
        int m;
        m= (p2[0]-p1[0])*(p2[0]-p1[0])+(p2[1]-p1[1])* (p2[1]-p1[1]);
        mp[abs(m)]++;
        m= (p3[0]-p1[0])*(p3[0]-p1[0])+(p3[1]-p1[1])* (p3[1]-p1[1]);
        mp[abs(m)]++;
        m= (p4[0]-p1[0])*(p4[0]-p1[0])+(p4[1]-p1[1])* (p4[1]-p1[1]);
        mp[abs(m)]++;
        m= (p3[0]-p2[0])*(p3[0]-p2[0])+(p3[1]-p2[1])* (p3[1]-p2[1]);
        mp[abs(m)]++;
        m= (p4[0]-p2[0])*(p4[0]-p2[0])+(p4[1]-p2[1])* (p4[1]-p2[1]);
        mp[abs(m)]++;
        m= (p4[0]-p3[0])*(p4[0]-p3[0])+(p4[1]-p3[1])* (p4[1]-p3[1]);
        mp[abs(m)]++;
        bool c=false;
        bool d = false;
        for(auto it: mp){
            if(it.second==2 && it.first!=0){
                c=true;
            }else if(it.second==4 && it.first!=0){
                d=true;
            }
        }
        if(c&d){
            return true;
        }else{
            return false;
        }
    }
};
```
