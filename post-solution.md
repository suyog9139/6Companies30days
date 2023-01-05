# Code
```
class Solution {
public:
   bool dfs(int node,vector<int> adj[],  vector<bool>&vis, vector<bool>&vis1){
       if(vis[node]==true) return true;
       vis[node] = true;
       vis1[node] = true;
       bool flag = false;
       for(auto it: adj[node]){
           if(!vis[it]){
               flag = dfs(it,adj,vis,vis1);
               if(flag==true) return true;
           }
           else if(vis1[it]==true) return true;
       }
       vis1[node]=false;
       return false;
   }


    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        int V = numCourses;
        vector<int>adj[V];
        for(auto it: prerequisites){
            adj[it[0]].push_back(it[1]);
        }
        vector<bool>vis(V,false),vis1(V,false);
        bool flag = false;
        for(int i=0; i<V; i++){
            if(!vis[i]){
                flag= dfs(i,adj,vis,vis1);
                if(flag==true) return false;
            }
            vis[i]=false;
        }
        return true;

    }
};
```
