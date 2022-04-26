# Graph_cycle
The code is to detect a cycle in an undirected graph


#include<bits/stdc++.h>
using namespace std;

const int N=1e5+10;

bool vis[N];
vector<int> g[N];

bool cycle(int vertex,int par){
	bool c=false;
	vis[vertex]=true;
	for(int child:g[vertex]){
		if(vis[child] && child==par)
			continue;
		if(vis[child])
			return true;

		c|=cycle(child,vertex);
	}
	return c;
}

int main(){
	int v,e;
	cin>>v>>e;
	for(int i=0;i<e;i++){
		int v1,v2;
		cin>>v1>>v2;
		g[v1].push_back(v2);
		g[v2].push_back(v1);
	}
	bool loopexist=false;
	for(int i=1;i<=v;i++){
		if(vis[i])
			continue;
		if(cycle(i,0)){
			loopexist=true;
			break;
		}
	}
	cout<<loopexist<<endl;
	return 0;
}
