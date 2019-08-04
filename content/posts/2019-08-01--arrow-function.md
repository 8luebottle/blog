---
title: Arrow Function
date: "2019-08-01T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/arrow-function/"
category: "ES6"
tags:
  - "TIL"
  - "ES6"
  - "Arrow function"

description: "ES6에서 등장한 화살표 함수는 어떠한 특징이 있기에 개발자들이 애용하는 것일까?"
---
<head>
<style>
  code {
    background-color: #ececec
  }
  p {
    font-size: 15px;
  }
  tr{
    text-align: right;
  }
  sub{
    font-size: 14px;
    vertical-align: middle;
    padding: 0px;
    color: #2680d9;
  }
  li{
    margin: 20px 0px;
  }
  strong{
    font-size: 18px;
    vertical-align: middle;
  }
  small{
    color: #808080;
  }
  #rcorners {
    border-radius: 25px;
    border: 2px solid #dd4ecf;
    padding: 20px; 
    width: 200px;
    height: 150px;  
  }
  .rdimg {
    border-radius: 25px;
  }
  img{
    margin-bottom: 10px;
  }
  ol{
    line-height: 25px;
    font-size: 15px;
  }
  .alignR{
    text-align: left;
  }
  table{
    font-size: 16px;
  }
  .idnt{
    text-indent: 50px;
  }
</style>
<link href="https://fonts.googleapis.com/css?family=Sunflower:300&display=swap" rel="stylesheet">
<body>
  <img src="/media/arrow.jpg" alt="Arrow Function" height="300" class=rdimg vspace= "10">
  <small><center>Arrow by. Paweł Czerwiński</center></small>
  <div style="font-family:Sunflower;">
</body>
  <p>
    <center>화살표 함수의 특징과 장점, 그리고 언제 사용하는 것이 좋은지에 대해여 알아보자</center>
  </p>
  <center><sub>화살표함수에 대해 이해하기 위해서는 최소 this, scope, 그리고 익명함수에 관한 개념을 알고 있어야 한다.</sub></center>
  <h2>ES6 : Arrow Function</h2>
  <p>
    <sub>앞으로 React에 관한 글도 연재할 생각이다. 그렇기에 React 시작전 선행학습 해야할 ES6문법에 관한 중요한 기능들을 하나씩 posting 해 나갈 예정이다. 이번 포스팅에서는 화살표 함수를 다루겠다.</sub><br><br>
    ES6 에 등장한 새로운 기능들이 많이 있다.
    Arrow function이라 불리우는 함수는 <strong>=></strong> 부호를 통해 구현한다. 화살표함수는 ES6의 새로운 기능중에서 사람들이 제일 애용하는 기능중 하나이다. 아래에서 화살표함수 특징에 대해 하나씩 살펴보며 사랑받는 이유에 대해 알아보자.<br><br>
    <sub>
      화살표 함수의 또 다른 이름은 <b>Fat arrow function</b>이다.  &nbsp;&nbsp; ( => Fat arrow 라 지칭 ) &nbsp;&nbsp;| &nbsp;&nbsp;( -> Thin arrow 라 지칭 ) <br>
      Coffee Script같은 경우에는 fat arrow(=>)와 , thin arrow(->) 모두를 사용한다.
    </sub>
  </p>
  <h2>화살표 함수의 특징</h2>
  <!-- <p>
    Web 프로그래머라면 대부분 JavaScript를 구사 가능하다. 대다수의 자바스크립트 프로젝트는 event-driven 스타일로 작성되어 유저들과의 상호작용을 만들어 낸다. 유저의 행동을 기준으로 <small>(버튼 클릭이라던지, 스크롤을 내린다던지)</small>동작--?<br>
  </p> -->
  <p>
    <table>
      <tr>
        <td><b>간결성 ⬆&nbsp;</b></td>
        <td class="alignR">화살표함수를 사용함으로 인해 코드의 군더더기가 제거되고 깔끔한 모습을 갖추게 된다.</td>
      </tr>
      <tr>
        <td><b>익명성 ➕</b></td>
        <td class="alignR">모든 화살표함수는 익명함수이다.</td>
      </tr>
      <tr>
        <td><b>this ✖&nbsp;</b></td>
        <td class="alignR">화살표 함수는 자신의 this값을 정의하지 않는다.</td>
      </tr>
      <tr>
        <td><b>생성자 ✖&nbsp;</b></td>
        <td class="alignR">화살표 함수는 생성자를 사용할 수 없다. 당연히 new 연산자 또한 사용불가</td>
      </tr>
    </table>
  </p>
  <p>
    나열한 화살표 함수의 특징들을 기존 ES5문법의 보통 함수와 비교하며 자세히 알아보도록 하자.
  </p>
  <h2>Arrow Function Vs. Regular Function</h2>
  <p>
    <img src="/media/regularFunc-vs-arrowFunc.png" alt="Regular Function Vs. Arrow Function" vspace= "10" >
    <small><center>Image 01: 일반함수와 화살표함수의 비교</center></small>
    <p>
    기존의 ES5 함수(Regular function)와 ES6화살표함수간에는 여러가지 차이점이 존재한다. Image 01을 보면 화살표 함수의 사용으로 인해 코드가 한결 간결해졌다는 것을 알 수 있다. 그럼 지금부터는 화살표 함수가 가진 특징들을 예시와 함께 알아보자.
    </p>
    <ol>
      <b><li>간결성</li></b>
        화살표함수의 간결성은 생략으로 비롯된다. 기존 함수에서는 생략할 수 없었던 token들을 생략 가능하다. 그 토큰들은 아래와 같다.<br>
        <ul>
          <li><b>&#123;&nbsp;&#125;</b> &nbsp;중괄호<br></li>
          <li><b>&#40;&nbsp;&#41;</b> &nbsp;소괄호<br></li>
          <li><b>return</b> 리턴 키워드<br></li>
        </ul>
        상기 토큰들은 각각 정해진 특정 상황에서만 생략할 수 있다. 생략 가능한 상황과 그렇지 않은 상황들을 살펴보자.
        <ol type="i">
          <b><li>Parameter 가 없을시</li></b>
            소괄호 생략 불가. <br>
            <img src="/media/param00.png" alt="No Parameter" width="500" vspace= "10"><br>
          <b><li>Parameter 가 한개일시</li></b>
            소괄호 생략 가능. <br>
            왼쪽의 ES5 문법과 오른쪽의 ES6문법의 parameter 부분을 봐보라. ES5 문법에 소괄호를 생략한다면 오류가 발생하지만 ES6는 그렇지가 않다.
            <img src="/media/param0101.png" alt="One Parameter" vspace= "10"><br>
          <b><li>Parameter 가 두개 이상</li></b>
            소괄호 생략 불가. <br>
            <img src="/media/param02.png" alt="More than 2 Parameter" vspace= "10"><br>
            <b><li>return</li></b>
            화살표함수에서는 묵시적으로 리턴을 해주기 때문에 return이라는 키워드를 생략 가능하다. 단, 명령문이 한줄로만 작성된 경우에 한해서이다. return문과 중괄호가 생략된 것을 볼 수 있다.<br>
            <sub>!!중괄호를 함께 생략해주어야 한다!!</sub>
            <img src="/media/return.png" alt="return" vspace= "10"><br>
            <b><li>중괄호</li></b>
            화살표 안의 명령문이 한 문장일 경우 중괄호를 생략가능하다.<br> 
            두 문장 이상일 시에는 &#123;&nbsp;&#125;를 빼먹지 말고 작성해주어야 한다.
            <img src="/media/curlyB.png" alt="Curly Braces" vspace= "10" width="400"><br>
            명령문이 두문장 이상인 경우에는 중괄호를 생략할 수 없다.
        </ol>
      <b><li>익명성</li></b>
      화살표함수는 항상 익명함수이다.<br>
      익명함수라는 것은 이름이 없는 함수를 뜻하는데 이름을 부르지 않아도 만들어진 해당 위치에서 실행 가능하다. <br><br>
      setTimeout() 의 예를 들어보자. 3초 후에 메세지를 콘솔에 띄우는 코드이다. 해당 코드를 작성하면 콘솔창에 3초 후에 <i>Time doesn’t wait for anyone</i> 라는 문자열이 뜬다.
      <img src="/media/arrowFuncAnnony.png" alt="Curly Braces" vspace= "10" ><br>
      기존에 여러줄에 작성해야 했던 코드는 한줄로 짧아 졌으며 함수 이름 자체를 사용하지 않아도 된다.
      <b><li>this와 binding</li></b>
      화살표함수의 this는 보통의 함수와 다르게 동작한다. <br>
      Regular function은 <b>호출</b>시에 this가 동적으로 결정된다면 arrow function은 함수 <b>생성</b>당시 this가 정적으로 결정된다. 자신이 위치한 상위 스코프를 this로 binding한다. 즉, 화살표함수의 this를 알기 위해서는 생성됬을시 화살표 함수의 상위 스코프를 참고하면 된다. 정적으로 this 가 결정되는 화살표 함수의 특성으로 인해 call, apply, bind메소드를 사용할 수 없다. (this가 한번 결정되었으므로 변경 불가)<br> 
      <sub>이렇게 this에 바인딩할 객체가 정적으로 결정되는 this를 Lexical this라고 한다.</sub><br>
      <b><li>생성자 constructor</li></b>
       화살표 함수의 또다른 특징은 생성자로 사용할 수 없다는 것이다.<br>
       보통의 함수같은 경우 함수를 생성할 시에 <code>prototype</code> 프로퍼티가 자동으로 만들어진다. 하지만 화살표함수는 <code>prototype</code> 프로퍼티가 생성되지 않을 뿐더러 <code>arguments</code>키워드, 그리고 내부 메소드도 없다. 이 말은 화살표 함수를 이용해 인스턴스를 만들지 못한다는 뜻이다. 그렇기에 생성자로써의 역할을 할 수가 없다.<br><br>
       아래의 예시를 보라. 화살표 함수를 통해 instance를 생성하려 했지만 TypeError가 뜨는 것을 볼 수 있다.
       <img src="/media/arrFuncConstructor.png" alt="Arrow Function Constructor Error" vspace= "10" width="350">
      </ol>
  </p>
  <h2>Reference</h2>
  <p>
    <ul>
      <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions" target="_blank">Arrow functions</a><br></li>
      <li><a href="http://www.cs.tufts.edu/~jfoster/papers/dls09-arrows.pdf" target="_blank">Directing JavaScript with Arrows</a><br></li>
      <li><a href="https://poiemaweb.com/es6-arrow-function" target="_blank">화살표 함수</a><br></li>
      <li><a href="https://zendev.com/2018/10/01/javascript-arrow-functions-how-why-when.html" target="_blank">JavaScript Arrow Functions</a><br></li>
      <li><a href="https://github.com/airbnb/javascript#arrow-functions" target="_blank">Airbnb/javascript#Arrow-Function</a><br></li>
    </ul>
  </p>

  <!-- <h2>Usage</h2>
  <p>
    -
  </p>
  <h4>When you should use</h4>
  <p>
    -
  </p>
  <h4>When you should not use</h4>
  <p>
    -
  </p>-->
</body>