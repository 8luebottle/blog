---
title: target="_blank"
date: "2019-08-06T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/target-blank/"
category: "HTML | CSS"
tags:
  - "TIL"
  - "HTML"
  - "phishing"
  - "target"
  - "tabnabbing"

description: "링크 클릭시 새 창을 띄우기 위해 보통 target=\"_blank\" 를 사용한다. 하지만 이는 보안상 문제가 될 수 있기에 안전한 대응방법을 알아보도록 하겠다."
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
</style>
<link href="https://fonts.googleapis.com/css?family=Sunflower:300&display=swap" rel="stylesheet">
<body>
  <img src="/media/phishing.jpg" alt="Phishing Attack" class=rdimg width="450" vspace= "15">
  <small><center>Image Source : ophtek.com</center></small><br>
  <div style="font-family:Sunflower;">
  <p>
    SNS 관련 프로젝트를 진행하던 도중 Twitter와 Facebook에서 공통적으로 발견한 코드가 있었다. 새 창을 띄우기 위해 <b>target="_blank"</b>를 사용할 경우 <b><code>rel="noopenner"</code></b>과 같은 속성을 추가하여 사용하고 있다. 이는 보안 취약성을 해결하고자 함이다. target="_blank"사용시에 어떠한 문제가 야기되며 그에 대한 대응방안은 무엇이 있는지 알아보도록 하겠다.
  </p>
  <h2>새 창 띄우기</h2>
  <p>혹시 아래와 같이 여러개의 창들을 띄워본적이 있는가? <br>
  대부분의 인터넷 유저는 한개의 페이지만을 오픈하여 사용하지는 않는다. 대신에 아래와 같이 여러개의 tab을 동시다발로 열어놓은 채 사용할 것이다. 유저가 직접 새 창을 띄워 탭을 늘리는 경우도 있지만 페이지 상의 특정 링크를 클릭할 시 새 탭이 열리게 되는 경우도 있다.</p>
  <img src="/media/multiTab.png"  alt="" class="rdimg">
  <small><center>인터넷을 애용하는 현대인에게는 너무나 친숙한 multiple tabs....</center></small><br>
  <p>
    <!--여기다 글을 써줄 것-->
    유저가 link를 클릭 했을시 현재의 창이 아닌 새로운 창으로 띄워주기 위해 사용할 수 있는 HTML 속성은 target 속성이다. 예를들어 만약 당신이 '행복해하는 강아지'의 이미지를 구글링된 새 화면으로 보여주고 싶다면 아래와 같이 코드를 작성할 수 있겠다.
    <div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%"></div><div style="line-height:130%"></div><div style="line-height:130%"></div><div style="line-height:130%"></div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#010101">&lt;</span><span style="color:#066de2">a</span>&nbsp;<span style="color:#0a9989">href</span>=<span style="color:#df5000">"https://www.google.com/search?q=happy+dog&amp;source=lnms&amp;tbm=isch&amp;sa=</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#df5000">X&amp;ved=0ahUKEwik9P7GmPLjAhWBHKYKHWvTDggQ_AUIECgB&amp;biw=740&amp;bih=665#imgrc=_"</span><span style="color:#0a9989"></span>&nbsp;<span style="color:#0a9989"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0a9989">target</span>=<span style="color:#df5000">"_blank"</span><span style="color:#0a9989"></span><span style="color:#010101">&gt;</span>Happy&nbsp;dog<span style="color:#010101">&lt;</span><span style="color:#010101">/</span><span style="color:#066de2">a</span><span style="color:#010101">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"></td></tr></table></div>
  </p>
  <center><a href="https://www.google.com/search?q=happy+dog&source=lnms&tbm=isch&sa=X&ved=0ahUKEwik9P7GmPLjAhWBHKYKHWvTDggQ_AUIECgB&biw=740&bih=665#imgrc=_" 
target="_blank">Happy dog</a></center>
  <p>
    <code>a</code>태그에 <code>href</code>로 링크를 걸어주었고 <code>target</code> 속성의 <code>_blank</code> 를 이용하여 새 창에 띄우도록 하였다. 위의 Happy dog 링크를 누르면 구글 이미지 검색창으로 순조롭게 이동 될 것이다. 하지만 이는 보안성을 생각하지 않은 코드이다. 그 누구도 자신이 작성해놓은 코드로 인하여 유저의 정보를 위험에 빠트리기 원치 않을 것이다. 여기서 문제점이 되는 코드는 <code>target="_blank"</code>이다. 해커는 <code>_blank</code> 속성값으로 인해 새롭게 열린 창을 이용하여 피싱(phishing)공격을 감행한다. 해커가 이용하는 이 특정 피싱 공격의 명칭은 <b>Tabnabbing</b> 이라고 불리운다.<br>
    <sub><b>Phishing:</b> Private Data와 Fishing의 합성어. 온라인상에서 개인정보를 악용하기 위해 불법적으로 취득하는 것을 말한다.<br>
    <b>Phishing 언어의 유래: </b>1996년 해커 뉴스그룹 <a href="https://www.2600.com/" target="_blank" rel="noopener">alt.2600</a>에서 첫 사용. </sub>   
  </p>
  <h2>Tabnabbing</h2>
  <p>
    <!-- nab 이라는 단어가 의미하듯이 해커는 tab을 통해---를 가져간다.  -->
    Tabnabbing은 피싱공격의 일종. <br>
    2010년, 보안전문가 Aza Raskin이 피싱공격에 붙인 단어이다. 단어가 내포하고 있는 의미처럼 공격은 새 창(새 탭)을 통해 이루어 진다.
    해커는 유저가 <code>target</code> 속성으로 열게 된 새 창의 페이지를 window.opener 속성을 이용하여 미리 준비해둔 피싱 사이트로 바꾼다. 이를 코드를 통해 보면 아래와 같다. <br><br>
    파란색 박스는 유저가 보는 페이지의 HMTL소스이다. 분홍 박스는 해커가 작성한 페이지이다. 조건문을 통해 window.opener 속성에 접근하여 피싱 사이트로 바꾸어 주었다. 보통의 유저는 새롭게 뜬 창이 해커가 바꾼 악성사이트인지를 알아차리기가 힘들다. 악성사이트 상에서 자신의 정보를 입력하게 되고 그 정보는 고스란히 해커에게 전달된다.<br>
    <sub>* <b>target</b> 속성은 링크된 문서를 어디서 어떻게 열 것인가를 지정해주는 기능을 갖고있다.</sub>
    <img src="/media/tabnabEg.png" alt="Example of Tabnabbing" class="rdimg" vspace= "15">
  </p>
  <b>해커가 접근 가능한 속성</b><br>
  <p>
    새 창에서 열린 부모에 접근하려 할 때 opener 속성을 통해서 한다.
    <ul>
      <li>opener.closed</li>
      <li>opener.frames</li>
      <li>opener.length</li>
      <li>opener.opener</li>
      <li>opener.parent</li>
      <li>opener.self</li>
      <li>opener.top</li>
    </ul>
  </p>
  <h2>해결 방안</h2>
  <p>
    <b>1. noopener | noreferrer 사용하기</b><br>
    noopener와 noreferrer 키워드를 이용함으로써 웹사이트의 보안성을 높여줄 수 있다.<br> 
    실제로 Facebook 과 Twitter는 위의 두 방법을 사용하고 있다.<br><br>
    위에서 코드로 보았듯이, 해커는 window.opener로 접근하여 새창의 주소를 악성 사이트로 바꾸는 방법을 사용했다. 그렇다면 해커가 해당 속성에 접근하지 못하도록 설정을 해놓아 버리자. 이는 noopener 와 noreferrer을 이용하여 window.opener가 가리키는 값을 null로 확정지어 버리면 된다. 코드는 <code>rel</code> 속성을 이용하여 작성해주면 된다.
    <br>
    위에서 보았던 보안이 취약한 코드를 고친다면 아래와 같다.
  </p>
  <div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%"></div><div style="line-height:130%"></div><div style="line-height:130%"></div><div style="line-height:130%"></div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#010101">&lt;</span><span style="color:#066de2">a</span>&nbsp;<span style="color:#0a9989">href</span>=<span style="color:#df5000">"https://www.google.com/search?q=happy+dog&amp;source=lnms&amp;tbm=isch&amp;sa=</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#df5000">X&amp;ved=0ahUKEwik9P7GmPLjAhWBHKYKHWvTDggQ_AUIECgB&amp;biw=740&amp;bih=665#imgrc=_"</span><span style="color:#0a9989"></span>&nbsp;<span style="color:#0a9989"></span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0a9989">target</span>=<span style="color:#df5000">"_blank"</span><span style="color:#0a9989"></span>&nbsp;<span style="color:#0a9989">rel</span>=<span style="color:#df5000">"noopener"</span><span style="color:#0a9989"></span><span style="color:#010101">&gt;</span>Happy&nbsp;dog<span style="color:#010101">&lt;</span><span style="color:#010101">/</span><span style="color:#066de2">a</span><span style="color:#010101">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none"></a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px"></span></a></td></tr></table></div>
  <p>
    보다시피 rel 속성을 붙여준것을 알 수 있다. 
  </p>
      <center><code>rel="noopener noreferrer"</code></center><br>
  <p>
    오래전에 발견된 이 피싱공격에 대해 Google, Facebook, Twitter와 같은 해외의 기업들은 tabnabbing에 대한 대응을 잘 하고 있다. 하지만 9년이 지난 현재까도 국내의 유명 포털사이트들의 소스코드를 열어본다면 이 위험에 대해 예방해 놓지 않고 있다는 것을 알 수 있다.
  </p>
    <img src="/media/tabnabbingFacebook.png" alt="Facebook and Tabnabbing" class="rdimg" vspace= "30">
    <small><center>Pixar의 Facebook 페이지 소스코드</center></small><br>
    <img src="/media/singleNmultiProcess.png" alt="Single Process Multi Process" class="rdimg" vspace= "30">
  <p>
    대부분의 브라우저는 멀티프로세스 방식으로 작동한다. 탭 마다 프로세스를 실행한다. 그로인해 메모리는 많이 차지하지만 안정성과 속도<small>(응답시간 86% 단축)</small>는 향상된다. <br>
    <br>
    <sub>* 다중 프로세스 지원이 안되던 Firefox도 뒤늦게(2016-03-08) 멀티프로세스를 지원(Firefox 48 정식판 부터)하기 시작했다. 전기분해의 의미를 지닌 <a href="https://wiki.mozilla.org/Electrolysis" target="_blank" rel="noopener noreferrer">Electrolysis</a> 프로젝트를 통해 싱글프로세스 방식을 유지하던 Firefox가 다중프로세스 방식으로 변경. 그로인해 브라우저 잦았던 UI 버튼 먹통의 현상을 해결하였다.</sub><br>
    <br>
    <!-- rel="noopener" 의 속성은 새 페이지에서 열린 
    rel=”noopener” attribute protects the new page to be accessed by the window.opener property and make sure it runs in a separate process.
    rel=”noreferrer” attribute has a similar quality, but it also prevents passing on the referrer information to the new page. -->
    <sub> *이 기능을 알면서도 SEO 순위를 우려하여 사용하지 않는 개발자들도 있다. 하지만  <code>rel="noopener"</code>을 사용하더라도 SEO에 대한 영향을 주지는 않으니 안전성을 위해 사용하도록 하자! SEO와 효율성에 관한 글은 <a href="https://searchenginelaws.com/seo/what-is-rel-noopener-noreferrer-tag/" target="_blank" rel="noopener noreferrel">여기서</a> 읽어보길</sub>
  </p>
  <!-- <p>
    그렇다면 이번에는 브라우저 콘솔창에서 rel 속성을 사용한것과 그렇지 않았을때의 차이점을 비교해보도록 하자. 
  </p> -->
  <h2>Reference</h2>
  <p>
    <ul>
      <li> <a href="http://www.itfind.or.kr/WZIN/jugidong/1237/123701.htm" target="_blank" rel="noopener">피싱(Phishing) 위협 및 대응 방안</a></li>
      <li><a href="https://techblog.topdesk.com/security/developers-need-know-reverse-tabnabbing/" target="_blank" rel="noopener">What all Developers need to know about: Reverse Tabnabbing</a></li>
      <li><a href="https://mathiasbynens.github.io/rel-noopener/" target="_blank" rel="noopener">About rel=noopener</a></li>
      <li><a href="https://developer.mozilla.org/ko/docs/Web/API/Window/opener" target="_blank" rel="noopener">Window.opener</a></li>
      <li><a href="https://caniuse.com/#feat=rel-noopener" target="_blank" rel="noopener">noopener and browser compatibility</a></li>
      <li><a href="" target="_blank" rel="noopener noreferrer">Reverse Tabnabbing</a></li>
      <li><a href="https://developers.google.com/web/tools/lighthouse/audits/noopener?hl=ko" target="_blank" rel="noopener noreferrer">rel="noopener"을 사용하여 외부 앵커를 여는 사이트</li>
      <li><a href="https://jakearchibald.com/2016/performance-benefits-of-rel-noopener/" target="_blank" rel="noopener noreferrer">The performance benefits of rel=noopener</a></li>
      <li><a href="https://arstechnica.com/information-technology/2017/06/firefox-multiple-content-processes/" target="_blank" rel="noopener noreferrer">Firefox 54 finally goes multiprocess, eight years after work began</a></li>
      <li><a href="https://wiki.mozilla.org/Electrolysis" target="_blank" rel="noopener noreferrer">Electrolysis<a></li>
    </ul>
  </p>
</body>