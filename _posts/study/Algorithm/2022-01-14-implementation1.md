---
layout: post
title: 구현 1
subtitle: 알고리즘
date: '2022-01-14 12:41:51 +0900'
categories: study
tags: algorithm
comments: true
published: true
---
## 구현 1(상하좌우)
출처 : (이코테 2021 강의 몰아보기) 2. 그리디 & 구현 <br>
<a href="https://www.youtube.com/watch?v=2zjoKjt97vQ&list=PLRx0vPvlEmdAghTr5mXQxGpHjWqSz0dgC">https://www.youtube.com/watch?v=2zjoKjt97vQ&list=PLRx0vPvlEmdAghTr5mXQxGpHjWqSz0dgC</a><br>
<h2>문제</h2>
여행가 A는 N x N 크기의 정사각형 공간 위에 서 있습니다. 이 공간은 1 x 1 크기의 정사각형으로 나누어져 있습니다. 가장 왼쪽 위 좌표는 (1,1)이며, 가장 오른쪽 아래 좌표는 (N,N)에 해당합니다. 여행가 A는 상 하 좌 우 방향으로 이동할 수 있으며, 시작 좌표는 항상 (1,1)입니다. 우리 앞에는 여행가 A가 이동할 계획이 적힌 계획서가 놓여 있습니다<br>
계획서에는 하나의 줄에 띄어쓰기를 기준으로 하여 L R U D 중 하나의 문자가 반복적으로 적혀 있습니다.<br>
L : 왼쪽으로 한 칸 이동<br>
R : 오른쪽으로 한 칸 이동<br>
U : 위로로 한 칸 이동<br>
D : 아래로 한 칸 이동<br>
이때 여행가 A가 N X N 크기의 정사각형 공간을 벗어나는 움직임은 무시됩니다. 예를 들어 (1,1)의 위치에서 L 혹은 U를 만나면 무시됩니다. 
<h2>코드</h2>
```py
#상하좌우
n=int(input())
x,y=1,1
plans=input().split()
move_types=['L','R','U','D']
dx=[0,0,-1,1]
dy=[-1,1,0,0]
for i in plans:
    for j in range(len(move_types)):
        if i==move_types[j]:
            nx=x+dx[j]
            ny=y+dy[j]
    if nx<1 or ny<1 or nx>n or ny>n:
        continue
    x,y=nx,ny
print(x,y)
```


