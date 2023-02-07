# tomatoes
# c
첫 줄에는 상자의 크기를 나타내는 두 정수 M,N이 주어진다. M은 가로수 N은 세로 수를 나타낸다. 둘째 줄은 토마토들의 정보가 주어진다. 정수 1은 익은 토마토, 정수 0은 익지 않은 토마토, 정수 -1은 토마토가 들어있지 않은 칸을 나타낸다. 위,아래,왼쪽,오른쪽으로 익은 토마토가 영향을 미친다. 며칠이 지나면 토마토들이 모두 익는지, 그 최소 일수를 구하는 프로그램을 작성해보자!

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int box[100][100];
int tomato[100][100]={0};
int q[100][2];
int dx[4]={-1,1,0,0};
int dy[4]={0,0,-1,1};
int start=0,end=0;
int main(){
	int m,n,i,j,day,cnt;
	scanf("%d %d",&m,&n);
	
	
	for(i=0;i<=n+1;i++){
		for(j=0;j<=m+1;j++){
			box[i][j]=-1;
			tomato[i][j]=0;}}
			
			
	for(i=1;i<=n;i++){
		for(j=1;j<=m;j++){
			scanf("%d",&box[i][j]);
			if(box[i][j]==1){
				q[end][0]=i;
				q[end][1]=j;
				end++;}}}
				
				
	while(start<end){
		int x,y;
		x=q[start][0];
		y=q[start][1];
		start++;
		for(i=0;i<4;i++){
		    if(x + dx[i] <= n && y + dy[i] <= m && x + dx[i] >= 1 && y + dy[i] >= 1 && box[x + dx[i]][y + dy[i]] == 0){
			    box[x+dx[i]][y+dy[i]]=1;
			    tomato[x+dx[i]][y+dy[i]]=tomato[x][y]+1;
			    q[end][0]=x+dx[i];
			    q[end][1]=y+dy[i];
			    end++;}}}
	
	
	for(i=1;i<=n;i++){
		for(j=1;j<=m;j++){
			if(day<tomato[i][j]){
				day=tomato[i][j];}
			if(box[i][j]==0){
				cnt=1;}}}
				
				
	if (cnt == 1) printf("모두익지 못함 -1\n");
  else printf("토마토가 모두 익을때까지의 최소 날짜: %d\n", day);
	return 0;
}
