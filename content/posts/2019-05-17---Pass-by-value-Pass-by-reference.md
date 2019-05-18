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

## Copying values
기본값이 복사될때와 참조값이 복사될때 두 가지 경우를 비교해보자. 

<div class="colorscripter-code" style="color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#272727; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #4f4f4f"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#aaa; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:120%"><div style="line-height:120%">1</div><div style="line-height:120%">2</div><div style="line-height:120%">3</div><div style="line-height:120%">4</div><div style="line-height:120%">5</div><div style="line-height:120%">6</div><div style="line-height:120%">7</div><div style="line-height:120%">8</div><div style="line-height:120%">9</div><div style="line-height:120%">10</div><div style="line-height:120%">11</div><div style="line-height:120%">12</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:120%"><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#999999">//&nbsp;Copying&nbsp;value&nbsp;(Primitive)</font></div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#999999">//&nbsp;Gas&nbsp;Price&nbsp;example</font></div><div style="padding:0 6px; white-space:pre; line-height:120%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;mobil&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;<font color="#c10aff">3.</font><font color="#c10aff">97</font>;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;arco&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;<font color="#c10aff">3.</font><font color="#c10aff">99</font>;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;shell&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;<font color="#c10aff">4.</font><font color="#c10aff">19</font>;</div><div style="padding:0 6px; white-space:pre; line-height:120%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:120%">shell&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;mobil;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#4be6fa">console</font>.log(<font color="#ffd500">"shell:&nbsp;"</font>&nbsp;<font color="#0086b3"></font><font color="#ff3399">+</font>&nbsp;shell);&nbsp;<font color="#999999">//&nbsp;shell:&nbsp;3.97</font></div><div style="padding:0 6px; white-space:pre; line-height:120%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;chevron&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;arco;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#4be6fa">console</font>.log(<font color="#ffd500">"chevron:&nbsp;"</font>&nbsp;<font color="#0086b3"></font><font color="#ff3399">+</font>&nbsp;chevron);&nbsp;<font color="#999999">//&nbsp;chevron:&nbsp;3.99</font></div></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#4f4f4f; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table></div>

서로 다른 주유소의 브랜드(mobil, arco, shell, chevron) 가 있다. mobil의 휘발류 가격은 \$3.97이고 shell의 가격은 \$4.19 이다. 대입연산자를 사용하여 shell 에 mobil가격을, chevron에 arco가격을 복사하였다.
콘솔에 결과를 찍어보면 본래 \$4.19였던 shell의 휘발류 가격은 mobil의 가격과 동일한 \$3.97로 출력된다. 선언과 동시에 arco의 휘발류 값을 초기화한 chevron또한 archo가격이 복사되어 \$3.99가 되었다.


## Reference
<a href="https://hackernoon.com/javascript-reference-and-copy-variables-b0103074fdf0" target="_blank">JavaScript Reference and Copy Variables</a>