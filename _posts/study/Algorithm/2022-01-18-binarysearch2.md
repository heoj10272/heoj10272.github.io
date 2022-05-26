---
layout: post
title: 이진탐색 2
subtitle: 알고리즘
date: '2022-01-20 17:53:51 +0900'
categories: study
tags: algorithm
comments: true
published: true
---
## 이진탐색 2(정렬된 배열에서 특정 수의 개수 구하기)
출처 : (이코테 2021 강의 몰아보기) 5. 이진탐색 <br>
<a href="https://www.youtube.com/watch?v=94RC-DsGMLo">https://www.youtube.com/watch?v=94RC-DsGMLo</a><br>
<h2>문제</h2>
N개의 원소를 포함하고 있는 수열이 오름차순으로 정렬되어 있습니다. 이때 이 수열에서 x가 등장하는 횟수를 계산하세요.<br>
예를 들어 수열{1,1,2,2,2,2,3}이 있을 때 x=2라면, 현재 수열에서 값이 2인 원소가 4개이므로 4를 출력합니다.<br>
단, 이문제는 시간 복잡도 O(log N)으로 알고리즘을 설계하지 않으면 시간초과 판정을 받습니다.<br>
<h2>코드</h2>
```py
#정렬된 배열에서 특정 수의 개수 구하기
from bisect import bisect_left, bisect_right
def count_by_range(array, left_value, right_value):
    right_index=bisect_right(array,right_value)
    left_index=bisect_left(array,left_value)
    return right_index-left_index

n,x=map(int,input().split())
array=list(map(int,input().split()))

count=count_by_range(array,x,x)

if count==0:
    print(-1)
else:
    print(count)
```


