# Shortest-path

Shortest path

#define M 101

#define LIM 20000000


int g[M][M],d[M],fd[2][M][M],gt[M][M],set[M];

inline void init(int d[M],int n,int s){  //初始化图

	int i;
  
	for(i=1;i<=n;i++)	d[i]=LIM;
  
  
	d[s]=0;
  
}


inline void relax(int d[M],int u,int v,int duv){

	if(d[v]>d[u]+duv)	d[v]=d[u]+duv;
  
}

void dijkstra(int g[M][M],int d[M],int n,int s){ //n is |V| && s is the source

	init(d,n,s);
  
	int q[M],ql=1,qf=1; //队列
  
	int i;
  
	for(i=1;i<=n;i++) q[ql++]=i;
  
	while(qf!=ql){
  
		int min=qf;
    
		for(i=qf;i<ql;i++) if(d[q[i]]<d[q[min]]) min=i; 
    
		swap(q[qf],q[min]); //q[qf] is the min
    
		int u=q[qf++];
    
		for(i=1;i<=n;i++){
    
			if(g[u][i]!=0) relax(d,u,i,g[u][i]);
      
		}
    
	}
  
}
