---
title: Media query
date: "2019-08-05T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/media-query/"
category: "HTML | CSS"
tags:
  - "TIL"
  - "CSS"
  - "Media query"
  - "Responsive"

description: "반응형 웹디자인을 구현하기 위해 필수적으로 알아야 할 Media query에 대해 알아 보자"
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
  .idnt{
    text-indent: 50px;
  }
  .container{
    float: left;
    position: relative;
    padding: 5px;
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
</style>
<link href="https://fonts.googleapis.com/css?family=Sunflower:300&display=swap" rel="stylesheet">
<body>
  <img src="/media/mediaQuery.jpg" alt="Media Query" class=rdimg width="450" vspace= "15">
  <div style="font-family:Sunflower;">
  <h2>About Media Query</h2>
  <p>
    반응형 웹사이트 구현시 빠지지 않고 사용하는 것이 미디어 쿼리이다. 반응형 웹은 기존의 정적인 페이지에서 벗어나 화면이 동적으로 변화 할수 있는 웹을 말한다. 반응형 웹을 구현하기 위해 사용하는 미디어 쿼리는 다양한 디바이스 화면 규격에 맞는 해상도 분기점을 제공한다. 핸드폰 해상도와 타블렛 그리고 와이드 모니터의 해상도는 제각각이다. 유저가 어떠한 디바이스를 사용하는지는 우리가 예상 할 수 없기 때문에 다양한 단말기를 염두에 두고 화면 구성을 해야 한다. 미디어쿼리는 화면 넓이가 어떤 사이즈이던지 아름답게 보이도록 도와준다. 미디어 쿼리를 사용함으로 인해 사용자 친화적인 화면구성이 가능해진다.<br><br>
    <b>Ethan Marcrotte</b><br>
    <img src="/media/ethan.png" alt="Ethan" class=rdimg width="200" vspace= "15">
    <img src="/media/ethansBook.png" alt="Ethan" class=rdimg vspace= "15">
   반응형 web design은  Ethan Marcotte가 처음 사용한 개념이다. 웹 디자이너인 Ethan은 작가이기도 한데 유명한 저서로는 <a href="https://www.amazon.com/Responsive-Design-Brief-People-Websites/dp/098444257X/ref=sr_1_2?keywords=Responsive+Web+Design&qid=1565098961&s=gateway&sr=8-2" target="_blank">Responsive Web Design</a> 과 <a href="https://www.amazon.com/Responsive-Design-Principles-Ethan-Marcotte/dp/1937557332/ref=sr_1_1?keywords=Responsive+Design%3A+Patterns+and+Principles&qid=1565099059&s=gateway&sr=8-1" target="_blank">Responsive Design: Patterns and Principles</a>가 있다. 그가 만든 작품에 관해 보고싶다면 <a href="https://ethanmarcotte.com/work/" target="_blank">여기</a>를 클릭하자.
    <br><br>
    <b>반응형의 웹의 중요성</b><br>
    Hosting Facts의 통계에 따르면, 2018년 한 해 전세계 인터넷 사용자의 수는 41억명이다. 이는 37억명이었던 2017년 인구의 10.8% 가 증가된 수치이다. 적지않은 사람들이 여러대의 디지털 기기<small>(tablet, smartphone, laptop etc)</small>를 소유하고 있다. 특히 모바일을 통한 웹리소스 소비가 두드러진다. 가까운 나라 중국의 경우<small>(Image 01 참고)</small>, 98%에 달하는 인터넷 사용이 모바일을 통해 이루어지고 있다. 모바일을 통한 글로벌 인터넷 사용률<small>(Image 02 참고)</small>도 2017년부터 이미 절반을 넘어섰다.
    <img src="/media/98percentChineseMobileUser.jpg" alt="Chinese Mobile User" class="rdimg" vspace="10px">
    <small><center>Image 01 : Chinese</center></small><br>
    <img src="/media/globalMobileTraffic.png" alt="Global Mobile Traffic" class="rdimg" vspace="10px">
    <small><center>Image 02 : Global</center></small><br>
  <p>
    2007년 스마트폰<small>(최초의 스마트폰은 이보다 15년 앞서 등장했다)</small>의 대중화의 성공으로 인하여 모바일로 언제 어디서나 인터넷을 접속하는 유저가 기하급수적으로 증가하였다. 이러한 시대의 흐름에 부합할 수 있는 반응형 웹을 구현해 낼 수 있어야 한다. 화면이 줄어들거나 늘어나더라도 화면이 뭉개지지 않도록 미디어 쿼리의 힘을 빌려보자.<br><br>
    <sub>* 세계 최초의 스마트폰은 1992년 IBM 이 'Simon'이란 이름으로 출시한 스마트폰이다. Simon은 계산기, 메모장, 스케치패드, 이메일기능등을 지닌 혁신적인 기기였다. 하지만 당시 $899( 2019년 8월 현 시세 $1,641 )이라는 적지 않은 금액, 1시간남짓한 베터리 수명등과 같은 단점으로 인해 대중화되지는 않았다*</sub>
  </p>
  <h2>미디어 쿼리의 구조</h2>
  <p>
    미디어 쿼리가 웹사이트를 아름답게 꾸며줌에도 불구하고 그 구조는 단순하다. 미디어 쿼리를 사용하는 기본 방법은 CSS 코드들이 있는 stylesheet위에 작성하는 방법이다. 
    미디어 쿼리의 예시 하나를 살펴보며 구조를 이해해보자.
    <div class="colorscripter-code" style="color:white;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#white;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%"></div><div style="line-height:130%"></div><div style="line-height:130%"></div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">&nbsp;&nbsp;&nbsp;&nbsp;@media&nbsp;only&nbsp;screen&nbsp;and&nbsp;</span>(<span style="color:#4DA51B">min-width</span><span style="color:#ff3399">:</span><span style="color:#4DA51B">&nbsp;600px</span>)<span style="color:#ff3399"></span>{<span style="color:#ff3399"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;body&nbsp;</span>{<span style="color:#0099cc">&nbsp;background-color</span><span style="color:#ff3399">:</span><span style="color:#0066cc">&nbsp;green</span><span style="color:#ff3399">;</span><span style="color:#0066cc">&nbsp;</span>}<span style="color:#0066cc"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0066cc">&nbsp;&nbsp;&nbsp;&nbsp;</span>}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;margin-bottom:10px;font-size:9px;font-style:italic"></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"></td></tr></table></div>
  </p>
  <p>
    Stylesheet에서 미디어 쿼리는 늘 <code>@media</code>로 시작한다. 미디어쿼리를 정의하는 단계라고 보면 된다. 그 다음은 '미디어 타입'이 무엇인지가 오게된다. 여기서는 <code>screen</code>으로 작성되었다. <code>only</code> 키워드는 선택사항이다. 이 키워드가 추가되었을시 미디어쿼리를 지원하는 웹 브라우저에서만 미디어 쿼리를 실행하도록 만든다. 즉, 미디어쿼리를 지원하지 않는 브라우저일시 해당 코드는 무시된다. <code>and</code>논리 AND연산을 수행한다. <code>(괄호 안)</code>은 조건문을 적는 공간으로써 CSS처럼 <code> :</code> 연산자를 사용한다. <code>{중괄호 안}</code>은 실행문이 들어가는 공간으로써 CSS 코드를 이 안에 작성하게 된다. 조건문이 '참' 일 시에만 실행문의 문장들을 해석하게 된다.
    <img src="/media/mq-syntax.png" alt="Syntax of Media query" class="rdimg" vspace="10px" width="400px"><br>
    예시문의 해석은 끝났으니 종류별로 자세히 알아보도록 하겠다.
  </p>
  <h4>Media Type</h4>
   <p>
    미디어 타입은 case sensitive 이기 때문에 작성시 대소문자를 유의하여 써주어야 한다. 보통의 경우 all, print, screen을 사용한다.
    <ul>
      <li><b>all : </b>모든 디바이스 지원</li>
      <li><b>aural : </b>음성 장치</li>
      <li><b>braille : </b>점자 장치</li>
      <li><b>embossed : </b>페이지에 프린트된 점자 장치</li>
      <li><b>handheld : </b>휴대용 작은 스크린</li>
      <li><b>print : </b>인쇄</li>
      <li><b>projection : </b>프로젝터</li>
      <li><b>tty : </b>tty 미디어 유형</li>
        <sub>디스플레이 능력이 한정적인 텔렉스, 터미널 등과 같은 장치</sub><br>
        <sub>px 단위 사용 불가</sub>
      <li><b>tv : </b>티비유형 디바이스</li>
        <sub>음성 + 영상이 함께 지원되는 장치를 뜻함.</sub>
    </ul>
  </p>
  <h4>조건문</h4>
    <p>
      조건문이 true이면 실행문을 해석, false 이면 실행문을 해석하지 않는다. <br>
      <code>and</code>키워드나 <code>,</code>를 사용하여 두개 이상의 조건문 작성이 가능하다.<br>
      조건문이라고해서 보통의 조건문의 연산자를 모두 사용 가능한 것은 아니다. <code>&lt;</code>, <code>&gt;</code>, <code>=</code>와 같은 연산자는 지원하지 않는다. 최소값, 최대값을 비교하고자 할 때는 <code>min-</code> 나 <code>max-</code> 를 이용한다.
    </p>
  <h4>실행문</h4>
    <p>
      CSS 코드 작성 부분. 조건문이 참일시 실행될 코드를 적는다.
    </p>
  <h2>Breakpoints</h2>
  <p>
    각 디바이스마다 알맞는 해상도 분기점을 알아보자. 분기점은 viewport 해상도에 따라 분류된다. 보통의 경우 아래와 같은 분기점을 따른다.<br>
    <sub>viewport : 실제 웹페이지 상에서 내용이 보여지는 영역을 말한다.</sub>
  </p>
  <table>
    <tr>
        <th>Type</th>
        <th>Resolution</th>
        <th>Type</th>
        <th>Resolution</th>
    </tr>
    <tr>
      <td><b>Phone</b></td>
      <td><b>Portrait :</b> 320px <br>&nbsp;&nbsp; <b>Landscape :</b> 480px</td>
      <td><b>Desktop</b></td>
      <td><b>Regular :</b> 1280px <br>&nbsp;&nbsp; <b>Wide : </b>1440px</td>
    </tr>
    <tr>
      <td><b>Small Tablet</b></td>
      <td><b>Portrait :</b> 600px <br>&nbsp;&nbsp; <b>Landscape :</b> 800px</td>
      <td><b>Large Tablet</b></td>
      <td><b>Portrait :</b> 768px <br>&nbsp;&nbsp; <b>Landscape :</b> 1024px</td>
    </tr>
  </table><br>
  <img src="/media/mq-phone.png" alt="Phone Resolution" width="350" vspace="10">
  <img src="/media/mq-tabletSmall.png" alt="Small Tablet Resolution" width="350" vspace="40">
  <img src="/media/mq-tabletLarge.png" alt="Large Tablet Resolution" width="350" vspace="40">
  <img src="/media/mq-desktop.png" alt="Desktop Resolution" width="350" vspace="40">
  <img src="/media/mq-desktopWide.png" alt="Wide Screen Desktop Resolution" width="350" vspace="40">
  <p>
    원하는 분기점을 나눈후 각각의 분기점별로 CSS를 적용해 줄 수 있다. 
    <!-- 분기하는 방법은 두 가지가 있다.  1, Markup 2, style tag 3, Css (@media) -->
  </p>

  <h2>반응형 디자인으로 구현한 웹</h2>
  <p>
    반응형으로 만든 웹사이트들이 어떤 모습을 갖추고 있는지 참고하실 수 있도록 사이트를 모아보았다. 원하는 사이트에 접속하여 개발자들이 반응형 웹을 어떻게 구현해 내었는지 둘러보자.
    <ol>
      <li><a href="https://www.yale.edu/" target="_blank">Yale University</a></li>
      <li><a href="https://www.cornell.edu/" target="_blank">Cornell University</a></li>
      <li><a href="http://web.mit.edu/" target="_blank">Cornell University</a></li>
      <li><a href="https://monese.com/" target="_blank">monese</a></li>
      <li><a href="https://transferwise.com/" target="_blank">TransferWise</a></li> 
      <li><a href="https://www.coinbase.com/" target="_blank">coinbase</a></li> 
      <li><a href="https://monzo.com/" target="_blank">monzo</a></li>
      <li><a href="https://www.curve.app/" target="_blank">CURVE</a></li> 
      <li><a href="https://www.countable.us" target="_blank">Countable</a></li>
      <li><a href="https://medium.com/" target="_blank">Medium</a></li>  
    </ol>
  </p>
  <h2>Reference</h2>
  <ul>
    <li><a href="https://www.businessinsider.com/worlds-first-smartphone-simon-launched-before-iphone-2015-6" target="_blank">The world's first smartphone</a></li>
    <li><a href="http://web.archive.org/web/19990221174856/byte.com/art/9412/sec11/art3.htm" target="_blank">BellSouth's communicative Simon is a milestone in the evolution of the PDA</a></li>
    <li><a href="https://www.usinflationcalculator.com/" target="_blank">US Inflation Calculator</a></li>
    <li><a href="https://www.silocreativo.com/en/media-queries-css-work/" target="_blank">Media Queries in CSS. How do They Work?</a></li>
    <li><a href="https://offbyone.tistory.com/121" target="_blank">반응형 웹을 위한 미디어 쿼리 사용법(CSS media queries)</a></li>
    <li><a href="https://www.dimensions.guide/browse" target="_blank">Dimensions Guide</a></li>
    <li><a href="https://internetingishard.com/html-and-css/responsive-design/" target="_blank">A beginner’s tutorial for crafting mobile-friendly websites</a></li>
    <li><a href="https://www.w3.org/TR/css3-mediaqueries/" target="_blank">W3C Media Queries</a></li>
    <li><a href="https://www.w3.org/TR/CSS21/media.html#media-types" target="_blank">7.2.1 The @media rule</a></li>
    <li><a href="https://css-tricks.com/snippets/css/media-queries-for-standard-devices/" target="_blank">Media Queries for Standard Devices</li>
  </ul>
</body>