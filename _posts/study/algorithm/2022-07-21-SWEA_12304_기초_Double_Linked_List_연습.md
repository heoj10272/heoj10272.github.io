---
layout: post
title: "[SWEA] 12304. 기초 Double Linked List 연습"
subtitle: Algorithm
date: '2022-07-20 23:50:00 +0900'
category: study
tags: algorithm samsung-dx swea
image:
  path: /assets/img/study_Algorithm/samsung_dx/logo.png
---

SW Expert Academy<br>
12304\. 기초 Double Linked List 연습

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
	Node* prev;
	Node* next;
};

Node node[MAX_NODE];
int nodeCnt;
Node* head;

Node* getNode(int data) {
	node[nodeCnt].data = data;
	node[nodeCnt].prev = nullptr;
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
	if (head->next == nullptr) {
		Node* node = getNode(data);
		node->prev = head;
		head->next = node;
	}
	else {
		Node* node = getNode(data);
		Node* next_ptr = head->next;
		next_ptr->prev = node;
		node->next = next_ptr;
		node->prev = head;
		head->next = node;
	}
}

void addNode2Tail(int data)
{
	Node* node = getNode(data);
	Node* prev_ptr = head;
	while (prev_ptr->next != nullptr) {
		prev_ptr = prev_ptr->next;
	}
	prev_ptr->next = node;
	node->prev = prev_ptr;
}

void addNode2Num(int data, int num)
{
	Node* prev_ptr = head;
	Node* node = getNode(data);
	for (int i = 1; i < num; i++) {
		prev_ptr = prev_ptr->next;
	}

	if (prev_ptr->next != nullptr) {
		node->next = prev_ptr->next;
		node->prev = prev_ptr;
		prev_ptr->next = node;
		prev_ptr = prev_ptr->next->next;
		prev_ptr->prev = node;
	}
	else {
		addNode2Tail(data);
	}
}

int findNode(int data)
{
	int cnt = 0;
	Node* prev_ptr = head;
	while (prev_ptr->next != nullptr) {
		prev_ptr = prev_ptr->next;
		cnt++;
		if (prev_ptr->data == data) {
			return cnt;
		}
	}
}

void removeNode(int data)
{
	Node* prev_ptr = head;
	while (prev_ptr->next != nullptr) {
		if (prev_ptr->next->data == data) {
			if (prev_ptr->next->next == nullptr) {
				prev_ptr->next = nullptr;
			}
			else {
				prev_ptr->next->next->prev = prev_ptr;
				prev_ptr->next = prev_ptr->next->next;
			}
			break;
		}
		prev_ptr = prev_ptr->next;
	}
}

int getList(int output[MAX_NODE])
{
	int cnt = 0;
	Node* prev_ptr = head;
	while (prev_ptr->next != nullptr) {
		prev_ptr = prev_ptr->next;
		output[cnt] = prev_ptr->data;
		cnt++;
	}
	return cnt;
}

int getReversedList(int output[MAX_NODE])
{
	int cnt = 0;
	Node* prev_ptr = head;
	while (prev_ptr->next != nullptr) {
		prev_ptr = prev_ptr->next;
		cnt++;
	}
	for (int i = 0; i < cnt; i++) {
		output[i] = prev_ptr->data;
		prev_ptr = prev_ptr->prev;
	}
	return cnt;
}
```

## 잡담

이전 [12303. 기초 Single Linked List 연습](https://heoj10272.github.io/study/SWEA_12303_%EA%B8%B0%EC%B4%88_Single_Linked_List_%EC%97%B0%EC%8A%B5.html) 문제와 매우 유사하지만 Double Linked List를 사용해서 기능을 구현하는 문제.

크게 어렵지 않게 작성할 수 있었으나 세세한 부분에서 미스가 있었다.<br>
`prev`와 `next`를 지정해 줄 때 간간이 잘못 지정하는 경우이다.<br>
아무래도 이런 문제는 머릿속으로만 생각하지 말고 그림을 그리면서 풀어야 실수가 적을 것 같다.<br>
다음번엔 귀찮아도 그리면서 해보자.

