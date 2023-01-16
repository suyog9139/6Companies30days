# Intuition
from centre find the length of all sides



# Code
```
class Solution {
public:
 
    bool check(pair<int,int>p, int n, int m){
        return (p.first>=0 && p.first<n && p.second >=0 && p.second<m);
    }
    vector<int> getBiggestThree(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
        set<int,std::greater<int>>s;
        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                s.insert(grid[i][j]);
            }
        }
        int total=0;
        for(int l=1; l<=50; l++){
            for(int i=0; i<n; i++){
                for(int j=0; j<m; j++){
                    pair<int,int>a = {i-l,j};
                    pair<int,int>b = {i,j-l};
                    pair<int,int>c = {i+l,j};
                    pair<int,int>d = {i,j+l};
                    if(check(a,n, m)&&check(b,n, m)&&check(c,n, m)&&check(d,n, m)){
                        total = grid[i-l][j]+grid[i][j-l]+grid[i+l][j]+grid[i][j+l];
                        for(int k=1;k<=l-1; k++) total+=grid[i+k][j-l+k];
                        for(int k=1;k<=l-1; k++) total+=grid[i+k][j+l-k];
                        for(int k=1;k<=l-1; k++) total+=grid[i-k][j-l+k];
                        for(int k=1;k<=l-1; k++) total+=grid[i-k][j+l-k];
                        s.insert(total);
                    }
                }
            }
        }
        vector<int>res;
        int c=0;
        for(auto it: s){
            if(c==3) break;
            c++;
            res.push_back(it);
        }
        return res;
    }
};
```
