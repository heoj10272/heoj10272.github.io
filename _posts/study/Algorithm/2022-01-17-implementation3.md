---
layout: post
title: 구현 3
subtitle: 알고리즘
date: '2022-01-17 10:52:51 +0900'
categories: study
tags: algorithm
comments: true
published: true
---
## 구현 3(왕실의 나이트)
출처 : (이코테 2021 강의 몰아보기) 2. 그리디 & 구현 <br>
<a href="https://www.youtube.com/watch?v=2zjoKjt97vQ&list=PLRx0vPvlEmdAghTr5mXQxGpHjWqSz0dgC">https://www.youtube.com/watch?v=2zjoKjt97vQ&list=PLRx0vPvlEmdAghTr5mXQxGpHjWqSz0dgC</a><br>
<h2>문제</h2>
왕국의 왕실 정원은 체스판과 같은 8x8 좌표 평면입니다. 왕실 정원의 특정한 한 칸에 나이트가 서 있습니다.<br>
나이트는 체스 나이트와 같이 L자 형태로만 이동할 수 있으며 정원 밖으로는 나갈 수 없습니다.<br>
8x8 좌표 평면상에서 나이트의 위치가 주어졌을 때 나이트가 이동할 수 있는 경우의 수를 출력하는 프로그램을 작성하세요. 왕실의 정원에서 행 위치를 표현할 때는 1부터 8로 포현하며, 열 위치를 표현할 때는 a부터 h로 표현합니다.<br>
c2에 있을 때 이동할 수 있는 경우의 수는 6가지입니다.<br>
<h2>코드</h2>
```py
#왕실의 나이트
a=input()
x=int(a[1])
y=int(ord(a[0]))-int(ord('a'))+1
cnt=0
#나이트가 이동할 수 있는 좌표
dx=[-2,-2,-1,1,-1,1,2,2]
dy=[-1,1,-2,-2,2,2,-1,1]
for i in range(8):
    nx=x+dx[i]
    ny=y+dy[i]
    if nx>=1 and nx<=8 and ny>=1 and ny<=8:
        cnt+=1
print(cnt)
```


