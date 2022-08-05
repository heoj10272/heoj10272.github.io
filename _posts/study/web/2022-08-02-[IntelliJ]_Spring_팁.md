---
layout: post
title: "[IntelliJ] Spring 팁 목록"
subtitle: IntelliJ
date: '2022-8-2 03:00:00 +0900'
category: study
tags: web intellij spring
image:
  path: /assets/img/study_Web/2022-08-02-[IntelliJ]_Spring_팁/logo.png
---

IntelliJ에서의 Spring 팁 목록

<!--more-->

* this unordered seed list will be replaced by the toc
{:toc}

<br>
<hr/>
<hr/>

# 💡 팁
* * *

## ⚡ 주석에서 Spellchecker 미적용하기
---

`File` - `Settings`<br>
`Editor` - `Inspections` - `Proofreading` - `Typo`<br>
`Process comments` 체크 해제

> 코드에서도 미적용 시키려면 `Process code` 체크 해제<br>
> 리터럴에서도 미적용 시키려면 `Process literals` 체크 해제

## ⚡ 한글 변수 사용시 경고 해제
---

내 경우에는 주석 내부에서 한글에 노랑색 블럭 처리가 되는것을 없애기 위해 적용했다.

`File` - `Settings`<br>
`Editor` - `Inspections` - `Internationalization` - `Non-ASCII characters`<br>
`Options` - 
  - `Warn of non-ASCII characters in:` - `identifiers` 체크 해제
  - `Warn of mixed ASCII/non-ASCII characters in:` - `identifiers` 체크 해제
