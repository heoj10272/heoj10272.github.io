---
layout: post
title: 구현 4
subtitle: 알고리즘
date: '2022-01-17 11:04:51 +0900'
categories: study
tags: algorithm
comments: true
published: true
---
## 구현 4(문자열 재정렬)
출처 : (이코테 2021 강의 몰아보기) 2. 그리디 & 구현 <br>
<a href="https://www.youtube.com/watch?v=2zjoKjt97vQ&list=PLRx0vPvlEmdAghTr5mXQxGpHjWqSz0dgC">https://www.youtube.com/watch?v=2zjoKjt97vQ&list=PLRx0vPvlEmdAghTr5mXQxGpHjWqSz0dgC</a><br>
<h2>문제</h2>
알파벳 대문자와 숫자(0~9)로만 구성된 문자열이 입력으로 주어집니다. 이때 모든 알파벳을 오름차순으로 정렬하여 이어서 출력한 뒤에, 그 뒤에 모든 숫자를 더한 값을 이어서 출력합니다.<br>
예를 들어 K1KA5CB7이라는 값이 들어오면 ABCKK13을 출력합니다.<br>
<h2>코드</h2>
```py
#문자열 재정렬
S=input()
alpha=[]
value=0
for i in S:
    if i.isalpha():
        alpha.append(i)
    else:
        value+=int(i)
alpha.sort()
if value!=0:
    alpha.append(str(value))
print(''.join(alpha))
```


