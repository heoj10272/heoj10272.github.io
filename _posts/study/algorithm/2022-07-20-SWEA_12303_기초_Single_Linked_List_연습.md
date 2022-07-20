---
layout: post
title: "[SWEA] 12303. 기초 Single Linked List 연습"
subtitle: Algorithm
date: '2022-07-20 23:50:00 +0900'
category: study
tags: algorithm samsung-dx swea
image:
  path: /assets/img/study_Algorithm/samsung_dx/logo.png
---

SW Expert Academy<br>
12303\. 기초 Single Linked List 연습

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

## 코드

```cpp
#define MAX_NODE 10000

struct Node {
	int data;
	Node* next;
};

Node node[MAX_NODE];
int nodeCnt;
Node* head;

Node* getNode(int data) {
	node[nodeCnt].data = data;
	node[nodeCnt].next = nullptr;
	return &node[nodeCnt++];
}

void init()
{
	nodeCnt = 0;
	head = getNode(-1);
}

void addNode2Head(int data)
{
	Node* node = getNode(data);
	node->next = head->next;
	head->next = node;
}

void addNode2Tail(int data)
{
	Node* prev_ptr = head;
	while (prev_ptr->next != nullptr) {
		prev_ptr = prev_ptr->next;
	}
	Node* node = getNode(data);
	node->next = nullptr;
	prev_ptr->next = node;
}

void addNode2Num(int data, int num)
{
	Node* prev_ptr = head;
	for (int i = 1; i < num; i++) {
		prev_ptr = prev_ptr->next;
	}
	Node* node = getNode(data);
	node->next = prev_ptr->next;
	prev_ptr->next = node;
}

void removeNode(int data)
{
	Node* prev_ptr = head;
	while (prev_ptr->next != nullptr && prev_ptr->next->data != data) {
		prev_ptr = prev_ptr->next;
	}
	if (prev_ptr->next != nullptr) {
		prev_ptr->next = prev_ptr->next->next;
	}
}

int getList(int output[MAX_NODE])
{
	Node* prev_ptr = head;
	int cnt = 0;
	while (prev_ptr->next != nullptr) {
		output[cnt] = prev_ptr->next->data;
		prev_ptr = prev_ptr->next;
		cnt++;
	}
	return cnt;
}
```

## 잡담

연결리스트는 STL 뿐만 아니라 직접 구현도 해본 적이 있기 때문에 쉽게 풀 수 있을거라 생각했으나...
1. SWEA 제출 환경에 대한 혼란
2. 구조체 포인터에 대한 이해 부족
위 두 요인으로 인해 시간을 굉장히 굉장히 많이 잡아먹었다.

1번 요인의 경우 `BOJ`에서는 겪어보지 못한 유형의 제출이라 많이 헷갈렸다.<br>
알고보니 그냥 `User Code` 부분만 수정해서 제출하면 되는 것이었다.

2번 요인은 평소 잘 사용하지 않고, 사용하더라도 구조체 그 자체의 특징으로 BFS 문제를 풀 때 vector 자료형으로만 간간히 썼었는데 갑자기 포인터라 ...

결국 구글링으로 구조체에 대한 개념을 다시 잡고 나서야 풀 수 있었다.<br>
기본적인 개념은 까먹지 말자.

그 외에는 `init` 함수로 처음에 `head`를 어떻게 할당할 것인지에 애를 좀 먹었고, <br>
`addNode2Tail`함수를 구현하는데에 시간이 꽤 걸렸다.<br>
연결리스트는 `head`와 `tail`에서 삽입시 상수 시간복잡도 만큼이 소요되어야 하는데 ... 결국 그렇게 풀진 못하고 `prev_ptr`로 연결리스트의 `head`부터 `tail`까지 순차적으로 찾아가도록 짜서 풀었다. <br>


