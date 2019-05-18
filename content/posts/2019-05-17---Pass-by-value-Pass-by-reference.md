---
title: Pass by value Vs. Pass by Reference
date: "2019-05-17T22:40:32.169Z"
template: "post"
draft: false
slug: "/Pass-by-value-Pass-by-reference/"
category: "JavaScript"
tags:
  - "Java Script"
  - "TIL"
  - "Primitive value"
  - "기본타입"
  - "Reference value"
  - "참조타입"
  - "자료형"
description: "기본타입과 참조타입의 값이 복사될시에 차이점이 무엇이며 메모리에서 어떠한 현상이 일어나는지 알아보자"

---

## JavaScript Data Type

자바스크립트에서 자료형은 기본타입(Primitive Type)과 참조타입(Reference Type)으로 나뉜다.

- <b>기본타입</b>

기본타입은 string, number, null, undefined, boolean 그리고 ES6에서 새로이 추가된 symbol 로 구성된다. 

- <b>참조타입</b>

기본타입 이외의 모든 것들 예를 들어 object, array, 그리고 function은 참조타입이다. 

![js-data-type.jpg](/media/js-data-type.png)

## Memories (기본값 & 참조값)
기본값과 참조값은 구조적인 차이도 있지만 메모리상에서 저장되는 위치도 다르다. 기본값은 메모리의 스택(stack)에 저장이 되고 참조값은 힙(heap)에 저장이 된다.



## Reference
<a href="https://hackernoon.com/javascript-reference-and-copy-variables-b0103074fdf0" target="_blank">JavaScript Reference and Copy Variables</a>