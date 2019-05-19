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
description: "기본타입과 참조타입의 값이 복사될때 서로의 차이점은 무엇이며 메모리에서는 어떠한 현상이 일어날까?"

---
Pass by value 와 Pass by reference을 이해하기 위해서는 자료형과 스택, 힙에 관한 메모리 지식이 필요하다. 프로그래머가 작성한 기본타입과 참조타입의 데이터가 하드웨어에서 어떻게 돌아가고 그것이 소프트웨어에서 어떻게 반영되는지 알아보자.

## JavaScript Data Type
자바스크립트에서 자료형은 기본타입(Primitive Type)과 참조타입(Reference Type)으로 나뉜다.

<b>[ 기본타입 Primitive Type ]</b>
<br>기본타입은 string, number, null, undefined, boolean 그리고 ES6에서 새로이 추가된 symbol로 구성되어 있다.

<b>[ 참조타입 Reference Type ]</b>
<br>기본타입 이외의 모든 것들 예를 들어 object, array, 그리고 function은 참조타입이다. 

![js-data-type.jpg](/media/js-data-type.png)
<br>

## Memories
![ram.png](/media/ram.png)
프로그래머가 선언한 변수는 메모리(RAM)에 저장된다. 메모리는 byte(8 bit)단위로 엑세스 된다. 기본값이 들어있는 기본변수와 참조값이 들어있는 참조변수는 구조적인 차이도 있지만 메모리상에서 저장되는 위치도 다르다. 메모리의 저장공간은 크게 코드, 데이터, 스택, 그리고 힙 영역으로 나뉜다. 
기본변수는 메모리의 <b>스택(stack)</b>에 저장이 되고 참조변수는 <b>힙(heap)</b>에 저장이 된다.<br>

<b>[ 스택 Stack ]</b><br>
기본값을 저장하고 있는 변수들은 스택에 차곡차곡 쌓이게 된다. 스택은 input과 output이 한쪽 끝에서만 이루어지는 메모리 구조다. 스택은 LIFO(Last In First Out)의 특징을 갖고 있는데 제일 마지막으로 들어간 데이터가 메모리에서 제일 먼저 제거된다. 추상적이게만 느껴진다면 스택을 책상위에 쌓인 책이라고 생각해보자. 보통의 경우, 차례대로 책을 쌓아두고 위에서 부터 책을 집어드는 것처럼 스택이라는 자료구조 또한 한쪽에서 데이터가 입력(push)되고 제거(pop)된다.
![stack.jpg](/media/stack.jpg)

<b>[ 힙 Heap ]</b><br>
스택에 차곡차곡 가지런히 저장되어 있는 기본변수와는 달리 참조변수는 정해진 순서없이 힙이라는 메모리공간에 패턴없이 저장되게 된다. 그리하여 힙에 저장되어 있는 데이터를 찾을때의 속도가 스택보다는 느리다. 그렇다면 규칙없이 이곳 저곳 저장되어버린 참조변수를 어떻게 찾아낼 것인가?
![heap.jpg](/media/heap.png)
방법은 포인터(pointer)에 있다. 포인터는 메모리의 주소를 담고 있다. 즉, 참조변수의 값을 가지고 있는 것이 아니라 '참조변수가 들고있는 값의 주소'를 담고 있다는 의미다. Pointer라는 단어를 살펴본다면 '특정 주소를 pointing(👈🏾)한다'는 뜻이 내포되어있다는 것을 알 수 있다. 정리하자면 포인터는 특정 주소를 지니고 있는 변수이다.
<center> ** <u>포인터는 스택</u>에 저장되고 포인터가 가리키는 <u>참조변수는 힙</u>에 저장된다 ** </center>


## Copying values
기본값이 복사될 때와 참조값이 복사될 때 두 가지 경우를 비교해보자. 

- #### Copying primitive values
서로 다른 주유소의 브랜드(mobil, arco, shell, chevron) 가 있다. mobil의 휘발류 가격은 \$3.97이고 shell의 가격은 \$4.19 이다. 대입연산자를 사용하여 shell 에 mobil가격을, chevron에 arco가격을 복사하였다.

<div class="colorscripter-code" style="color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#272727; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #4f4f4f"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#aaa; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:120%"><div style="line-height:120%">1</div><div style="line-height:120%">2</div><div style="line-height:120%">3</div><div style="line-height:120%">4</div><div style="line-height:120%">5</div><div style="line-height:120%">6</div><div style="line-height:120%">7</div><div style="line-height:120%">8</div><div style="line-height:120%">9</div><div style="line-height:120%">10</div><div style="line-height:120%">11</div><div style="line-height:120%">12</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:120%"><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#999999">//&nbsp;Copying&nbsp;value&nbsp;(Primitive)</font></div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#999999">//&nbsp;Gas&nbsp;Price&nbsp;example</font></div><div style="padding:0 6px; white-space:pre; line-height:120%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;mobil&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;<font color="#c10aff">3.</font><font color="#c10aff">97</font>;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;arco&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;<font color="#c10aff">3.</font><font color="#c10aff">99</font>;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;shell&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;<font color="#c10aff">4.</font><font color="#c10aff">19</font>;</div><div style="padding:0 6px; white-space:pre; line-height:120%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:120%">shell&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;mobil;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#4be6fa">console</font>.log(<font color="#ffd500">"shell:&nbsp;"</font>&nbsp;<font color="#0086b3"></font><font color="#ff3399">+</font>&nbsp;shell);&nbsp;<font color="#999999">//&nbsp;shell:&nbsp;3.97</font></div><div style="padding:0 6px; white-space:pre; line-height:120%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;chevron&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;arco;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#4be6fa">console</font>.log(<font color="#ffd500">"chevron:&nbsp;"</font>&nbsp;<font color="#0086b3"></font><font color="#ff3399">+</font>&nbsp;chevron);&nbsp;<font color="#999999">//&nbsp;chevron:&nbsp;3.99</font></div></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#4f4f4f; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table></div>

콘솔에 결과를 찍어보면 본래 \$4.19였던 shell의 휘발류 가격은 mobil의 가격과 동일한 \$3.97로 출력된다. 선언과 동시에 arco의 휘발류 값을 초기화한 chevron또한 archo가격이 복사되어 \$3.99가 되었다.

- ### Copying reference values



## Reference
- <a href="https://www.amazon.com/Understanding-Using-Pointers-Techniques-Management/dp/1449344186/ref=sr_1_1?crid=J4ASWRR1M98U&keywords=understanding+and+using+c+pointers&qid=1558195869&s=gateway&sprefix=understanding+and+using+c+po%2Caps%2C348&sr=8-1"  target="_blank">[Book] Understanding and Using C Pointer</a>
- <a href="https://hackernoon.com/javascript-reference-and-copy-variables-b0103074fdf0" target="_blank">[Text] JavaScript Reference and Copy Variables</a>
- <a href=http://cslibrary.stanford.edu/102/PointersAndMemory.pdf target="_blank">[Text] Pointers and Memory</a>
- <a href="https://www.youtube.com/watch?v=IX3fDYz0WyM" target="_blank">[Video] Stack Versus Heap</a>

