---
layout: post
title: 구현 2
subtitle: 알고리즘
date: '2022-01-17 10:49:51 +0900'
categories: study
tags: algorithm
comments: true
published: true
---
## 구현 2(시각)
출처 : (이코테 2021 강의 몰아보기) 2. 그리디 & 구현 <br>
<a href="https://www.youtube.com/watch?v=2zjoKjt97vQ&list=PLRx0vPvlEmdAghTr5mXQxGpHjWqSz0dgC">https://www.youtube.com/watch?v=2zjoKjt97vQ&list=PLRx0vPvlEmdAghTr5mXQxGpHjWqSz0dgC</a><br>
<h2>문제</h2>
정수 N이 입력되면 00시 00분 00초부터 N시 59분 59초까지의 모든 시각 중에서 3이 하나라도 포함되는 모든 경우의 수를 구하는 프로그램을 작성하시오<br>
예를 들어 1을 입력했을 때 00시 00분 03초, 00시 13분 30초는 3이 하나라도 포함되어 있으므로 세어야 하는 시각입니다.<br>
반면에 00시 02분 55초, 01시 27분 45초는 3이 하나도 포함되어 있지 않으므로 세면 안 되는 시각입니다.
<h2>코드</h2>
```py
#시각
N=int(input())
cnt=0
for i in range(N+1):
    for j in range(60):
        for k in range(60):
            if '3' in str(i)+str(j)+str(k):
                cnt+=1
print(cnt)
```


