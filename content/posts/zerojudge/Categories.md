---
title: "zerojudge_g276"
date: 2023-07-05T06:50:07+08:00
draft: false
---

## code:

```#include<bits/stdc++.h>
using namespace std;
int n,m,k,keep=0,recheck=0,sum=0;
int main(){
	cin >> n >> m >> k; 
	int check[n][m];
	memset(check , 0 ,sizeof(check));
	int boss[k][5];
	for(int a=0;a<k;a++){
		cin >> boss[a][0] >> boss[a][1] >> boss[a][2] >> boss[a][3]; // r c s t
		boss[a][4] = 1; //魔王自身是否存活
	}
	while(1){
		keep = 0;
		recheck = 0;
		for(int a=0;a<k;a++){
			if(boss[a][4]!=0){
				keep=1; //判斷是否有魔王活著
			}
		}
		if(keep==1){ //如果有魔王活著，繼續判斷
			for(int a=0;a<k;a++){
				if(boss[a][0]<0 || (boss[a][0])>n){ //越界預防
					(boss[a][0])=n;
				}
				if(boss[a][1]<0 || (boss[a][1])>m){
					(boss[a][1])=m;
				}
				if(check[(boss[a][0])][(boss[a][1])]!=-1 && boss[a][4]==1){ //boss放炸彈
					check[(boss[a][0])][(boss[a][1])]+=-1;
				}
				boss[a][0]+=boss[a][2]; //boss移動
				boss[a][1]+=boss[a][3];
				
				if(boss[a][4]==1 && (boss[a][1]>=m || boss[a][1]<0 || boss[a][0]>=n || boss[a][0]<0)){ //超出棋盤
					boss[a][4]=0; //越界死亡
				}
			}
		
	
			for(int x=0;x<n;x++){
			
				for(int y=0;y<m;y++){ 
					if(check[x][y]<0){ //判斷魔王是否在炸彈上
						for(int p=0;p<k;p++){
							if(boss[p][0]==x && boss[p][1]==y && boss[p][4]==1){
								boss[p][4]=0;
								recheck=1;
							}
						}
					if(recheck==1){ //清空當格炸彈
						check[x][y]=0;
						recheck=0;
					}
				}
			}
		}
	}
		if(keep==0){
			break;}	
	}	
		for(int x=0;x<n;x++){
		for(int y=0;y<m;y++){ //加總剩餘炸彈總數
			sum += check[x][y];
		
		}
	}
	cout << -sum;
	return 0;
}
```