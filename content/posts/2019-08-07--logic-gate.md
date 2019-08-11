---
title: Logic gate
date: "2019-08-07T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/logic-gate/"
category: "Computer Architecture"
tags:
  - "TIL"
  - "Computer Architecture"
  - "Bianry"
  - "Logic gate"
  - "논리게이트"
  - "Circuit"


description: "논리연산자 AND, OR, NOT이 Hardware단에서 어떻게 동작하는지에 대해 알아보자."
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
    /* list-style: none; */
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
  ol, ul{
    line-height: 25px;
    font-size: 15px;
  }
  .alignR{
    text-align: left;
  }
  table{
    font-size: 16px;
  }
  table {
    width: 100%;
  }
  td, th{
    border: 1px solid black;
    text-align: left;
    text-indent: 10px;
    font-size: 14px;
  }
  tr:first-child{
    background-color: #DCDCDC;
  }
  center {
    line-height: 1.5;
  }
  a { 
    text-decoration: none;
  }
  .imageContainer {
    float: left;
  }
  .card{
    border: 1px dotted #2680d9;
    color: #2680d9;
    max-width: 380px;
    padding: 10px 10px;
    border-radius: 15px;
    font-size: 14px;
  }
</style>
<link href="https://fonts.googleapis.com/css?family=Sunflower:300&display=swap" rel="stylesheet">
<body>
    <!-- <img src="/media/bulbOn.svg" alt="On and Off circuit" height="150"  style="float: left; margin: 30px 0px 20px 150px; padding: 5px 0px">
    <img src="/media/bulbOff.svg" alt="On and Off circuit" height="150" vspace= "15" style="float: left; margin: 30px 0px 20px 0px; padding: 5px 0px">
    <br> -->
    <img src="/media/switchOnNOff.png" alt="Switch on and off" class="rdimg" width="300px" vspace="20px">
    <small><center><p style="padding-bottom: 15px; display:block; clear:both"> Image Source : <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a></p></center></small>
  <div style="font-family:Sunflower;">
  <center>컴퓨터를 구성하는 기본 블록인 논리게이트에 대해 알아보자</center>
  <h2>Logic Gate</h2>
  <p>
    논리게이트는 두가지 상태만으로 논리연산을 수행한다. <br>
    두 가지 상태라는 것은 참(1) 그리고 거짓(0)이다. 2진수로 데이터를 표현하는 것은 전기로 작동하는 컴퓨터가 데이터를 다루기에 가장 적합한 방법이다. 실질적으로 스위치를 On & Off 하면서 데이터를 전달하면 되기 때문이다. 
    <img src="/media/binary2States.png" alt="Binary two states" class="rdimg" vspace= "15">
    전자 회로에서 Switch가 On 되었다는 것은 5v의 전류가 흐르고 있다는 것을 뜻하고 Off는 전류가 흐르지 않는 상태인 0v를 의미한다. <i>'이 두 가지 상태만으로 복잡한 일이 가능할까?'</i> 라는 의문이 들 수 도 있겠지만, 컴퓨터는 0과 1만으로 연산, 게임, 무인항공기제어등 복잡한 일들을 무리 없이 수행해낸다. 컴퓨터가 수많은 분야에서 쓰일 수 있게 된 것은 불리언(Boolean)방정식이 논리연산과 산술연산 모두를 가능케 했기 때문이다. 조지 불이 고안해낸 불리언방정식을 클로드 섀넌이 1937년 디지털 논리회로로 접목시킬수 있음을 증명해냈다. 기존의 방정식이 미지수를 수학적 계산을 통해 풀어냈다면 불리언 방정식은 '참' 또는 '거짓'이라는 논리적 관계를 통해 풀어낸다. 여기서 미지수는 숫자뿐만 아니라 아이디어, 명제도 포함된다.
  </p>
  <p class="card">
    <img src="/media/georgeBoole.jpg" alt="George Boole" class="rdimg">
    <b>George Boole 조지 불 | 영국의 수학자<br>
    1815.11.02 (Lincoln, UK) ~ 1864.12.08 (Cork, Ireland)</b><br>
    George Boole 은 Mary Ann Joyce 어머니와 John Boole 아버지 사이에서 태어났다. 그는 1854년 불리언방정식에 대한 내용을 담고 있는 책 <i>An investigation into the Laws of Thought</i> 를 출판했다.
  </p>
  <p class="card">
    <img src="/media/claudeShannon.jpg" alt="Claude Shannon" class="rdimg" height="150px">
    <b>Claude Elwood Shannon 클로드 섀넌 | 미국의 전기공학자<br>
    1916.04.30 (Michigan, US) ~ 2001.02.24 (Massachusetts, US)</b><br>
    정보이론의 아버지라고 불리는 클로드 섀넌은 언어교사인 어머니와 사업가 아버지 사이에서 태어났다. 그는 1937년 불 논리를 이용한 이진수 사칙연산에 대한 석사 논문 <i>A mathematical theory of communication </i> 를 발표했다. 그로인해 1940년 프린스턴 고등연구소에 초빙되었으며 유명한 수학자 헤르만 바일, 존 폰 노이만등과 같이 연구를 진행했다.
  </p>
   <img src="/media/basicGates.gif" alt="Basic Gates" class="rdimg" vspace="70px">
   <small><center><p style="padding-bottom: 15px; display:block; clear:both"> Image Source : hyperphysics</center></small>
  <p>
    논리게이트는 보통 2개 이상의 Input 단자와 1개의 output 단자를 가진다. 
    여러 종류의 단자들이 모여 논리회로를 구성한다. 대표적인 논리게이트는 AND, OR, NOT, NAND, NOR, XOR, XNOR가 있다. 이들을 다양하게 조합하여 복잡한 논리를 간결하게 이진수로 표현해 낼 수 있다. 컴퓨터의 모든 동작은 논리회로의 동작으로 이루어진다. 아래에서는 몇가지의 논리게이트들을 진리표(truth tables) 와 함께 살펴보도록 하겠다.<br>
    <sub>*<b> 단자:</b> 전기회로나 전기기기 등에서 전류의 입력이나 출력부분에 전극을 접속시키기 위해 붙이는 끝 부분</sub>
  </p>
  <h3>AND gate</h3>
  <b>AND 게이트 | 논리곱</b><br>
    <center><b>논리식 : </b> A*B</center>
    <img src="/media/andGate.png" alt="AND Gate" width=180px>
    <img src="/media/andTruthTable.png" alt="AND Gate Truth Table" width=180px>
  <p>
    AND 게이트는 논리곱이라고도 불리우는데, 곱셈연산처럼 작동을 하기 때문이다.<br> 1*0, 0*1, 0*0 이 0인 것 처럼 True인 경우는 오직 하나 1*1 일 때만 가능하다. 즉 Input A 와 Input B 의 값이 모두 1인 상황에서만 True 를 반환한다. <br><br>
    예시를 들어보자
    <img src="/media/andEx.png" alt="AND Example" width=350px>
  </p>
  <p>
    첫번째, Input A<small>(내 이름은 Baby Tiger)</small>와 Input B<small>(호랑이다)</small>는 모두 true 이므로 Output은 True 가 되었다.<br>
    두번째, Input A<small>(내 이름은 Baby Tiger)</small>는 참이었지만 Input B<small>(사자다)</small>는 거짓이다. 두 가지 조건을 모두 충족하지 못했기에 결과는 False 가 된다.<br><br>
    Javscript에서 AND 연산자는 || 로 표시한다. 자바스크립트로 구현을 해본다면 아래와 같다.
  </p>
  <img src="/media/andJavaScript.png" alt="And JavScript code" width= 350px>
  <h3>OR gate</h3>
    <b>OR 게이트 | 논리합</b><br>
    <center><b>논리식 : </b> A+B</center>
    <img src="/media/orGate.png" alt="OR Gate" width=180px>
    <img src="/media/orTruthTable.png" alt="OR Gate Truth Table" width=180px>
  <p>
    OR 게이트는 논리합이라고도 불린다. 덧셈연산처럼 작동을 한다.<br>
    0+1, 1+0, 1+1 은 모두 참이 된다. False 인 경우는 오직 하나 Input A 와 Input B가 0 인 경우이다.<br><br>
    예시를 들어보자
    <img src="/media/orEx.png" alt="OR Example" width=300px>
  </p>
  <p>
    첫번째, Input A<small>(나는 사자)</small>은 거짓이지만 Input B<small>(호랑이다)</small>는 참이기에 결과는 참이된다.<br>
    두번째, Input A<small>(나는 육식동물)</small>과 Input B<small>(고양이과다)</small>모두 참이기에 이 역시 결과가 참이된다.<br><br>
    Javscript에서 OR 연산자는 && 로 표시한다. 자바스크립트로 구현을 해본다면 아래와 같다.
  </p>
  <img src="/media/orJavaScript.png" alt="Or JavScript code" width= 250px>
  <h3>NOT gate</h3>
    <b>NOT 게이트 | 논리부정</b><br>
    <center><b>논리식 : </b> A' = Ā</center>
    <img src="/media/notGate.png" alt="OR Gate" width=160px>
    <img src="/media/notTruthTable.png" alt="OR Gate Truth Table" width=180px>
  <p>
    인버터라고도 불리우는 NOT 게이트는 한개의 입력과 한개의 출력만을 가진다. Input된 논리를 반전시켜 반대의 결과를 도출해 내도록 하는 게이트이다. 0 이 Input되면 1 을, 1 이 Input 되면 0 을 반환한다.
  </p>
  <p>
    지금까지 논리게이트와 기본 논리게이트의 종류에 대해 알아보았다. 다음 포스팅에서는 세가지의 논리게이트를 조합하여 만들어낼 수 있는 NAND, NOR, XOR, XNOR에 대해 알아볼 것이다.
  </p>
  <h2>Reference</h2>
  <p>
    <ul>
      <li>
        <a href="http://www.ee.surrey.ac.uk/Projects/CAL/digital-logic/gatesfunc/" target="_blank" rel="noopener noreferrer">Logic Gates</a>
      </li>
      <li>
        <a href="https://www.britannica.com/biography/George-Boole" target="_blank" rel="noopener noreferrer">George Boole</a>
      </li>
      <li>
        <a href="https://www.cambridge.org/ad/academic/subjects/mathematics/historical-mathematical-texts/investigation-laws-thought-which-are-founded-mathematical-theories-logic-and-probabilities" target="_blank" rel="noopener noreferrer">An Investigation of the Laws of Thought</a>
      </li>
      <li>
        <a href="https://history-computer.com/ModernComputer/thinkers/Shannon.html" target="_blank" rel="noopener noreferrer">Claude Shannon</a>
      </li>
      <li>
        <a href="http://hyperphysics.phy-astr.gsu.edu/hbase/Electronic/gate.html" target="_blank" rel="noopener noreferrer">Basic Gates</a>
      </li>
    <ul>
  </p>
</body>