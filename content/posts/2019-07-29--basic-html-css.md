---
title: HTML 기초
date: "2019-07-29T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/basic-html-css/"
category: "HTML | CSS"
tags:
  - "TIL"
  - "HTML"
  - "elements"
  - "Semantic Element"

description: "HTML의 기초와 Semantic Element를 잘 사용하는 것이 왜 중요한지에 대해 알아보자"
---
<head>
<style>
  code {
    background-color: #ececec
  }
  p {
    font-size: 15px;
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
  }
</style>
  <link href="https://fonts.googleapis.com/css?family=Sunflower:300&display=swap" rel="stylesheet">
</head>
<header>

</header>
<body>
  <img src="/media/htmlcss.jpg" alt="HTML & CSS" height="350" class=rdimg>
  <small><center>Skull Queen by Riza Peker</small></center>
  <div style="font-family:Sunflower;">
  <p>HTML의 기초적인 용어 및 용도를 살펴보자.</p>
  <h2>HTML</h2>
  <p>
    tag는 세 종류로 나뉜다.
    <ol>
      <li>시작 태그</li>
      <sub>&lt;span&gt;&nbsp;&nbsp;&nbsp;&lt;p&gt;&nbsp;&nbsp;&lt;body&gt;&nbsp;&nbsp;&lt;html&gt;</sub>
      <li>종료 태그</li>
      <sub>&lt;/span&gt;&nbsp;&nbsp;&lt;/p&gt;&nbsp;&nbsp;&lt;/body&gt;&nbsp;&nbsp;&lt;/html&gt;</sub>
      <li>빈 태그</li>
      <sub>&lt;br&gt;&nbsp;&nbsp;&lt;li&gt;&nbsp;&nbsp;&lt;img&gt;&nbsp;&nbsp;&lt;hr&gt;&nbsp;&nbsp;&lt;area&gt;&nbsp;&nbsp;&lt;track&gt;&nbsp;&nbsp;&lt;input&gt;
      </sub>
    </ol>
    '시작태그'와 '종료태그'는 한 세트이다. 종료태그가 필요 없는 태그를 '빈 태그'라고 한다.
  </p>
  <p>
    HTML의 기초적인 구성요소를 살펴보자면 아래와 같다.
    <br>&nbsp;&nbsp;&nbsp;&nbsp;- element 요소
    <br>&nbsp;&nbsp;&nbsp;&nbsp;- attribute 속성
    <br>&nbsp;&nbsp;&nbsp;&nbsp;- value 값
    <br>&nbsp;&nbsp;&nbsp;&nbsp;- content 내용
    <br><br>
    위의 단어들을 이해하기 쉽게 그림으로 알아보자.<br>
    <img src="/media/tagEg01.png" alt="Tag Example" width=420>
    시작태그는 <strong>&lt;p&gt;</strong>, 종료태그는 <strong>&lt;/p&gt;,</strong> content는 <strong>Baby T, Enjoy Every Moment</strong>이다. Element는 시작태그 + content + 종료태그, 즉 <strong>&lt;p&gt;Baby T, Enjoy Every Moment&lt;/p&gt;</strong>를 말한다.<br><br>
    다른 예로 빈 태그의 경우를 봐보자.
    <img src="/media/tagEg02.png" alt="Empty Tag Example" width=280>
    이 요소는 컨텐츠가 존재하지 않는데 꺽쇠의 시작부터 끝까지가 요소가 된다. <strong>src</strong>는 속성의 이름, 그리고 <strong>"lovely.png"</strong>는 속성의 값이 된다.
  </p>
  <h2>Semantic Element Vs. Non-semantic Element</h2>
  <img src="/media/semant-non-semant.png" alt="Semantic Vs. Non-Semantic" width=420>
  <p>
    <strong>Semantic Element:</strong> 의미를 가지고 있는 요소<br>
    <sub>&nbsp;&nbsp;&nbsp;&nbsp;&lt;header&gt;&nbsp;&nbsp;&nbsp;&nbsp;&lt;footer&gt;&nbsp;&nbsp;&nbsp;&nbsp;&lt;table&gt;&nbsp;&nbsp;&nbsp;&nbsp;&lt;article&gt;&nbsp;&nbsp;&nbsp;&nbsp;&lt;aside&gt;&nbsp;&nbsp;&nbsp;&nbsp;&lt;time&gt;</sub><br>
    <strong>Non-semantic Element:</strong> 의미를 가지고 있지 않은 요소<br>
    <sub>&nbsp;&nbsp;&nbsp;&nbsp;&lt;div&gt;&nbsp;&nbsp;&nbsp;&nbsp;&lt;span&gt;</sub><br>
    Semantic Element를 잘 쓰는 것이 중요하다. 이를 잘 활용한다는 것은 컨텐츠의 계층구조를 잘 알고 있다는 것을 뜻한다. 적재적소에 Semantic Element를 사용하지 못하고 본 의미에 벗어난 채로 사용하게 되면 안쓰느니만 못하다. <br>
    여기서 말하는 '의미'란? 개발자 뿐만아니라 기계도 알아들을 수 있는 뜻을 갖고 있는 것을 말한다. 즉, 태그만 보고 기계와 개발자는 명확한 의미를 알 수 있다.
  </p>
  <p>
    개발자와 기계가 의미를 알 수 있도록 시맨틱 요소를 사용하는 것이 왜 중요할까? <br>
크게 세 가지 이유를 들 수 있겠다. 접근성, 관리<small>(유지보수)</small>, 그리고 SEO 측면이다.
  <ol>
    <li>접근성</li>
    더 많은 유저들에게 접근이 가능하다. 스크린을 볼 수 없는 시각장애인들뿐만 아니라 Stylesheet이 적용되지 않은 브라우저를 사용하는 유저에게도 접근이 가능해진다.
    <li>SEO</li>
    기계가 태그의 의미를 세세히 알 수 있다는 것은 검색에 최적화 되어 있다는 것과 같다. 이는 해당 페이지의 노출의 우선순위가 타 페이지<small>(의미 없는 태그를 사용한 페이지)</small>보다 높아지는 것을 뜻한다.
    <li>관리</li>
    협업이 필수인 프로그래밍 분야에서는 관리하기 좋은 코드를 잘 짤 줄 알아야 한다. 알아보기 좋은 코드는 타 개발자에게도 이득이지만 시간이 한참 흐른후 희미해진 기억을 가진 미래의 자신에게도 충분히 플러스 요소가 된다.
  </ol>

  </p>

  </div>
</body>