---
title: "1013 武陵水上樂園"
date: 2023-09-19T21:24:18+08:00
draft: false
summary: WLOJ 1013
---
## code：

```
#include <bits/stdc++.h>
using namespace std;
int n,m,ch=1,skip=0; 
int main(){
    cin >> n >> m;
    int ground[n+2][m+2];
    int scan[n+2][m+2];
    memset(ground,0,sizeof(ground));
    memset(scan,1,sizeof(scan));
    for(int a=1; a<n+1; a++){
        for(int b=1; b<m+1; b++){
            cin >> ground[a][b];
            if(ground[a][b]==0){
                for(int c=-1; c<2; c++){
                    for(int d=-1; d<2; d++){
                        scan[a+c][b+d]=0;
                    }
                }
            }
        }
    }
while(ch!=0){
    ch = 0;
    for(int a=1; a<n+1; a++){
        for(int b=1; b<m+1; b++){
            if(scan[a][b]==0){
                continue;
            }
            for(int c=-1; c<2; c++){
                for(int d=-1; d<2; d++){
                    if(ground[a+c][b+d]<ground[a][b]){
                        skip = 1;
                        break;
                    }
                }
                if(skip == 1){
                    break;
                }
            }
            if(skip == 1){
                skip = 0;
                continue;
            }
        ground[a][b]++;
        ch++;
        }
    }
}
    for(int a=1; a<n+1; a++){
        for(int b=1; b<m+1; b++){
            cout << ground[a][b];
            if(b != m){
                cout << ' ';
            }
        }
        cout << endl;
     }
}
```
