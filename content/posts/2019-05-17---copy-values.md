---
title: Copying Primitive Value Vs. Reference Value
date: "2019-05-17T22:40:32.169Z"
template: "post"
draft: false
slug: "/posts/copy-values/"
category: "JavaScript"
tags:
  - "Java Script"
  - "TIL"
  - "Primitive value"
  - "기본타입"
  - "Reference value"
  - "참조타입"
  - "자료형"
description: "기본타입과 참조타입의 값이 복사될 때 서로의 차이점은 무엇이며 메모리에서는 어떠한 현상이 일어날까?"
---

primitive value 와 reference value가 복사될 때의 차이점을 알기 위해서는 자료형과 스택, 힙에 관한 메모리 지식이 필요하다. 프로그래머가 작성한 기본타입과 참조타입의 데이터가 하드웨어에서 어떻게 돌아가고 그것이 소프트웨어에서 어떻게 반영되는지 알아보자.

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
프로그래머가 선언한 변수는 메모리(RAM)에 저장된다. 메모리는 byte(8 bit)단위로 엑세스 된다. 기본타입과 참조타입은 구조적인 차이도 있지만 메모리상에서 저장되는 위치도 다르다. 메모리의 저장공간은 크게 코드, 데이터, 스택, 그리고 힙 영역으로 나뉜다. 
기본타입은 메모리의 <b>스택(stack)</b>에 저장이 되고 참조타입은 <b>힙(heap)</b>에 저장이 된다.<br>

<b>[ 스택 Stack ]</b><br>
기본값을 저장하고 있는 변수들은 스택에 차곡차곡 쌓이게 된다. 스택은 input과 output이 한쪽 끝에서만 이루어지는 메모리 구조다. 스택은 LIFO(Last In First Out)의 특징을 갖고 있는데 제일 마지막으로 들어간 데이터가 메모리에서 제일 먼저 제거된다. 추상적이게만 느껴진다면 스택을 책상위에 쌓인 책이라고 생각해보자. 보통의 경우, 차례대로 책을 쌓아두고 위에서 부터 책을 집어드는 것처럼 스택이라는 자료구조 또한 한쪽에서 데이터가 입력(push)되고 제거(pop)된다.
![stack.jpg](/media/stack.jpg)

<b>[ 힙 Heap ]</b><br>
스택에 차곡차곡 가지런히 저장되어 있는 기본값과는 달리 참조값은 힙이라는 메모리공간에 패턴없이 저장되게 된다. 그리하여 힙에 저장되어 있는 데이터를 찾을때의 속도가 스택보다는 느리다. 그렇다면 규칙없이 이곳 저곳 저장되어버린 데이터를 어떻게 찾아낼 것인가?
![heap.png](/media/heap.png)
방법은 포인터(pointer)에 있다. 포인터는 해당 데이터의 주소를 담고 있다. 즉, 직접 해당 데이터의 값을 가지고 있는 것이 아니라 '값의 주소'를 담고 있다는 의미다. Pointer라는 단어를 살펴본다면 '특정 주소를 pointing(👈🏾)한다'는 뜻이 내포되어있다는 것을 알 수 있다. 정리하자면 포인터는 특정 주소를 지니고 있는 변수이다.
<center> ** <u>포인터는 스택</u>에 저장되고 포인터가 가리키는 <u>참조값은 힙</u>에 저장된다 ** </center>


## Copying values
기본값이 복사될 때와 참조값이 복사될 때 두 가지 경우를 비교해보자. 

- #### Copying primitive values
서로 다른 주유소의 브랜드(mobil, shell) 가 있다. 현재 mobil의 휘발류 가격은 \$3.97이다. 대입연산자를 사용하여 shell 에 mobil가격을 초기화시켰다. 7번 라인에 <code>console.log("shell: " + shell);</code> 을 찍어보면 shell에 mobil 가격 3.97이 잘 복사된것을 볼 수 있다.

<div class="colorscripter-code" style="color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#272727; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #4f4f4f"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#aaa; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//&nbsp;Copying&nbsp;value&nbsp;(Primitive)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//&nbsp;Gas&nbsp;Price&nbsp;example</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;mobil&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">3.</span><span style="color:#c10aff">97</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;shell&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;mobil;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">console</span>.log(<span style="color:#ffd500">"shell:&nbsp;"</span>&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">+</span>&nbsp;shell);&nbsp;<span style="color:#999999">//&nbsp;---&gt;&nbsp;"shell:&nbsp;3.97"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">mobil&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">4.</span><span style="color:#c10aff">19</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">console</span>.log(<span style="color:#ffd500">"mobil:&nbsp;"</span>&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">+</span>&nbsp;mobil);&nbsp;<span style="color:#999999">//&nbsp;---&gt;&nbsp;"mobil:&nbsp;4.19"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">console</span>.log(<span style="color:#ffd500">"shell:&nbsp;"</span>&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">+</span>&nbsp;shell);&nbsp;<span style="color:#999999">//&nbsp;---&gt;&nbsp;"shell:&nbsp;3.97"</span></div></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#4f4f4f; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table></div>

그렇다면 mobil에 새 값인 4.19를 할당했을때 shell에도 변화가 일어날까?<br>
9번 라인에서 mobil에 4.19을 할당한후 shell의 값도 변화되었는지 11번라인에 콘솔로 출력해보았다. mobil변수의 값은 4.19로 변화되었지만 shell은 3.97 그대로 남아있는것을 알 수 있다. 6번라인에서 shell은 mobil로 부터 값을 복사 하였고 stack에 같은 값을 지닌 두개의 변수가 저장되어 있는 것이다. 그리하여 mobil의 변화는 shell에 영향을 주지 않는다.
<div style="width: 20%; height: 20%;padding-bottom:30%;position:relative;"><iframe src="https://giphy.com/embed/lSPSDuDkJ0hMRJ80sJ" width="100%" height="100%" style="position:absolute" frameBorder="0" allowFullScreen></iframe></div></a></p>

- ### Copying reference values
이번에는 참조값을 복사하는 경우를 알아보자.<br><br>
Chris와 James 두 친구가 점심을 먹기위해 In N Out에 갔다. chrisOrder라는 객체 안에는 drink와 hamburger가 있다. James도 Chirs와 똑같은 메뉴를 먹고싶다. 9번라인에서 chrisOrder의 값을 jamesOrder에 초기화시켰다(참조값 복사).

<div class="colorscripter-code" style="color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#272727; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #4f4f4f"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#aaa; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:120%"><div style="line-height:120%">1</div><div style="line-height:120%">2</div><div style="line-height:120%">3</div><div style="line-height:120%">4</div><div style="line-height:120%">5</div><div style="line-height:120%">6</div><div style="line-height:120%">7</div><div style="line-height:120%">8</div><div style="line-height:120%">9</div><div style="line-height:120%">10</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:120%"><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#999999">//&nbsp;Copying&nbsp;value&nbsp;(Reference)</font></div><div style="background-color:#303030; padding:0 6px; white-space:pre; line-height:120%"><font color="#999999">//&nbsp;In&nbsp;N&nbsp;Out&nbsp;example</font></div><div style="padding:0 6px; white-space:pre; line-height:120%">&nbsp;</div><div style="background-color:#303030; padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;chrisOrder&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:120%">&nbsp;&nbsp;drink:&nbsp;<font color="#ffd500">"sprite"</font>,</div><div style="background-color:#303030; padding:0 6px; white-space:pre; line-height:120%">&nbsp;&nbsp;hamburger:&nbsp;<font color="#ffd500">"double-double"</font></div><div style="padding:0 6px; white-space:pre; line-height:120%">};</div><div style="background-color:#303030; padding:0 6px; white-space:pre; line-height:120%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#ff3399">var</font>&nbsp;jamesOrder&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;chrisOrder;</div><div style="background-color:#303030; padding:0 6px; white-space:pre; line-height:120%"><font color="#4be6fa">console</font>.log(jamesOrder);</div></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#4f4f4f; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table>
<code><span style= "font-size: 14px; color:black;">
  line 10: [object Object] {
    drink: "sprite",
    hamburger: "double-double"
  }
</code></span></div>

콘솔에 jamesOrder을 찍어보면 chrisOrder의 값이 똑같이 복사된 것을 알 수 있다. <br><br> 한 우유부단 하는 Chris는 더블더블 버거 대신 치즈버거가 먹고싶어졌다. 12번 라인의 명령문을 통해 크리스가 cheese burger를 먹을 수 있도록 바꾸어주자. 
<div class="colorscripter-code" style="color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important; overflow:auto"><table class="colorscripter-code-table" style="margin:0; padding:0; border:none; background-color:#272727; border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px; border-right:2px solid #4f4f4f"><div style="margin:0; padding:0; word-break:normal; text-align:right; color:#aaa; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:120%"><div style="line-height:120%">11</div><div style="line-height:120%">12</div><div style="line-height:120%">13</div><div style="line-height:120%">14</div></div></td><td style="padding:6px 0"><div style="margin:0; padding:0; color:#f0f0f0; font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; line-height:120%"><div style="padding:0 6px; white-space:pre; line-height:120%">&nbsp;</div><div style="background-color:#303030; padding:0 6px; white-space:pre; line-height:120%">chrisOrder.hamburger&nbsp;<font color="#0086b3"></font><font color="#ff3399">=</font>&nbsp;<font color="#ffd500">"cheese&nbsp;burger"</font>;</div><div style="padding:0 6px; white-space:pre; line-height:120%"><font color="#4be6fa">console</font>.log(chrisOrder);</div><div style="background-color:#303030; padding:0 6px; white-space:pre; line-height:120%"><font color="#4be6fa">console</font>.log(jamesOrder);</div></div></td><td style="vertical-align:bottom; padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none; color:white"><span style="font-size:9px; word-break:normal; background-color:#4f4f4f; color:white; border-radius:10px; padding:1px">cs</span></a></td></tr></table></div>

13번라인의 chrisOrder의 출력 결과를 보면 "double-double" 에서 "cheese burger"로 잘 바뀐 것을 알 수 있다.<br>
<code><span style= "font-size: 14px; color:black;">
  line 13 : [object Object] {
    drink: "sprite",
    hamburger: "cheese burger"
  }
</span></code>

하지만 문제가 생겼다! <br>
우리가 변경한 것은 분명 chrisOrder.hamburger 인데 jamesOrder까지 영향을 받았다. 불쌍한 James는 강제적으로 치즈버거를 먹게 되어버렸다. 😭 <br>
<code><span style= "font-size: 14px; color:black;">
  line 14 : [object Object] {
    drink: "sprite",
    hamburger: "cheese burger"
  }
</span></code>

이런 결과가 발생한 이유는 자바스크립트에서 Object는 참조형이기 때문이다. Object 값은 heap에 저장되어 있지만 해당 값을 가리키는 jamesOrder, chrisOrder 참조변수는 stack에 저장되어 있다. 이 변수들 안에는 heap에 위치한 object를 가리키는 포인터들이 있다. jamesOrder의 포인터와 chrisOrder의 포인터가 가리키는 object는 같다. 이러한 이유로 Object의 값을 바꾼다면 같은 주소를 들고있는 두 참조변수 jamesOrderd와 chrisOrder는 함께 영향을 받게된다.

<div style="width:50%;height:50%;padding-bottom:20%;position:relative;"><iframe src="https://giphy.com/embed/KDsRUPvh7xkY0ZfDYy" width="100%" height="100%" style="position:absolute" frameBorder="0" allowFullScreen></iframe></div></a></p>


## Reference
- <a href="https://www.amazon.com/Understanding-Using-Pointers-Techniques-Management/dp/1449344186/ref=sr_1_1?crid=J4ASWRR1M98U&keywords=understanding+and+using+c+pointers&qid=1558195869&s=gateway&sprefix=understanding+and+using+c+po%2Caps%2C348&sr=8-1"  target="_blank">[Text] Understanding and Using C Pointer</a>
- <a href="https://hackernoon.com/javascript-reference-and-copy-variables-b0103074fdf0" target="_blank">[Text] JavaScript Reference and Copy Variables</a>
- <a href=http://cslibrary.stanford.edu/102/PointersAndMemory.pdf target="_blank">[Text] Pointers and Memory</a>
- <a href="https://www.youtube.com/watch?v=IX3fDYz0WyM" target="_blank">[Video] Stack Versus Heap</a>



<div id="disqus_thread"></div>
<script>
var disqus_config = function () {
this.page.url = "babytiger.netlify.com/posts/copy-values/";
this.page.identifier = copy-values;
};
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://babytiger.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                            
                            