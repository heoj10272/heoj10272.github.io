---
layout: post
title: 이진탐색 1
subtitle: 알고리즘
date: '2022-01-20 17:38:51 +0900'
categories: study
tags: algorithm
comments: true
published: true
---
## 이진탐색 1(떡볶이 떡 만들기)
출처 : (이코테 2021 강의 몰아보기) 5. 이진탐색 <br>
<a href="https://www.youtube.com/watch?v=94RC-DsGMLo">https://www.youtube.com/watch?v=94RC-DsGMLo</a><br>
<h2>문제</h2>
오늘은 떡볶이 떡을 만드는 날입니다. 떡볶이 떡은 재밌게도 떡볶이 떡의 길이가 일정하지 않습니다. 대신에 한 봉지 안에 들어가는 떡의 총 길이는 절단기로 잘라서 맞춰줍니다.<br>
절단기에 높이(H)를 지정하면 줄지어진 떡을 한 번에 절단합니다. 높이가 H보다 긴 덕은 H 위의 부분이 잘릴 것이고, 낮은 떡은 잘리지 않습니다.<br>
예를 들어 높이가 19, 14, 10, 17cm인 떡이 나란히 있고 절단기 높이를 15cm로 지정하면 자른 뒤 떡의 높이는 15, 14, 10, 15cm가 될 것이고 잘린 떡의 길이는 차례대로 4, 0, 0, 2cm입니다. 손님은 6cm만큼의 길이를 가져갑니다.<br>
손님이 왔을 때 요청한 총 길이가 M일 때 적어도 M만틈의 떡을 얻기 위해 절단기에 설정할 수 있는 높이의 최댓값을 구하는 프로그램을 작성하시오.<br>
<h2>코드</h2>
```py
#떡볶이 떡 만들기
n,m=map(int,input().split())
array=list(map(int,input().split()))
start=0
end=max(array)
result=0
while(start<=end):
    total=0
    mid=(start+end)//2
    for x in array:
        if x>mid:
            total+=x-mid
    if total<m:
        end=mid-1
    else:
        result=mid
        start=mid+1
print(result)
```


