

# Code
```
#define ll long long
class Solution {
public:
    int countPaths(int n, vector<vector<int>>& roads) {
        vector<pair<int,int>>adj[n];
        for(auto it: roads){
             adj[it[0]].push_back({it[1],it[2]});
             adj[it[1]].push_back({it[0],it[2]});
        }

        priority_queue<pair<ll,int>,vector<pair<ll,int>>, greater<pair<ll,int>>> pq;
        vector<ll>dist(n,LONG_MAX), ways(n,0);
        dist[0]=0;
        ways[0] = 1;
        int mod = 1e9+7;
        pq.push({0,0});
        while(!pq.empty()){
            ll dis = pq.top().first;
            int node = pq.top().second;
            pq.pop();

            for(auto it: adj[node]){
                int adjNode = it.first;
                int adW = it.second;
                if(dis+adW < dist[adjNode]){
                    dist[adjNode] = (dis+ adW);
                    pq.push({dis+adW, adjNode});
                    ways[adjNode] = ways[node]%mod;
                }else if(dis+adW == dist[adjNode]){
                    ways[adjNode] =  (ways[adjNode]+ways[node])%mod;
                }
            }
        }
        return ways[n-1]%mod;
    }
};
```
