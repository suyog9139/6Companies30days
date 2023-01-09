

# Code
```
class Solution {
public:
    int dfs(vector<vector<int>>&adj, vector<int>&disFromBob, int u,int par,int depth,vector<int>&amount, int bob){
        int ret = 0;
        if(u==bob) disFromBob[u] = 0;
        else disFromBob[u] = amount.size();
        int maxChild = -INT_MAX;
        for(auto it:adj[u]){
            if(it==par)continue;
            maxChild = max(maxChild,dfs(adj,disFromBob,it,u,depth+1,amount, bob));
            disFromBob[u] = min(disFromBob[u],disFromBob[it]+1);
        }
        if(disFromBob[u]>depth)ret+=amount[u];
        else if(disFromBob[u]==depth)ret+=amount[u]/2;
        if(maxChild==-INT_MAX) return ret;
        else return ret+maxChild;
    }
    int mostProfitablePath(vector<vector<int>>& edges, int bob, vector<int>& amount) {
        int n = amount.size();
        vector<vector<int>>adj;
        adj.resize(n,vector<int>());
        vector<int>disFromBob(n);
        for(auto it:edges){
            adj[it[0]].push_back(it[1]);
            adj[it[1]].push_back(it[0]);
        }
        
        return dfs(adj,disFromBob,0,0,0,amount, bob);
    }
};
```
