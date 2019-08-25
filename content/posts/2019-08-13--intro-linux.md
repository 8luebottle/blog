---
title: Intro to Linux
date: "2019-08-13T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/intro-linux/"
category: "OS"
tags:
  - "TIL"
  - "Linux"
  - "Unix"
  - "GNU"
  - "MULTICS"

description: "리눅스의 뿌리는 유닉스에서 찾을 수 있다. 유닉스와 리눅스의 역사와 철학에 대해 알아보자"
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
  }
  .alignR{
    text-align: left;
  }
  table{
    font-size: 16px;
    width: 100%;
  }
  table, td, th, tr{
    border: 1px solid #2680d9;
    text-align: left;
    font-size: 14px;
    border-collapse: collapse;
    padding: 15px;
  }
  tr:first-child{
    background-color: #3BAFC9;
    color: white;
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
</head>
<body>
<link href="https://fonts.googleapis.com/css?family=Sunflower:300&display=swap" rel="stylesheet">
<div style="font-family:Sunflower;">
<img src="/media/linuxHistory.png" alt="Linux History" class="rdimg"  vspace="15px">
<small><center><p style="padding-bottom: 15px; display:block; clear:both"> Image Source : digitalocean.com</center></small>
<center font-size="13px">리눅스의 뿌리는 Unix로 부터 비롯되기에 <br>
리눅스를 알아보기에 앞서 간단히 Unix에 대해서 알아보도록 하자.</center><br><br>
<p>
아래 이미지는 UNIX의 계보(1969-2017)이다. 한 눈에 봐도 여러 갈래로 나뉘어 복잡한 것을 알 수 있다.<br>
  <img src="/media/unix-family.png" alt="UNIX Family" class="rdimg"  vspace="40px">
  <small><center><p style="padding-bottom: 15px; display:block; clear:both"> 유닉스 계보
    <br><b>Green:</b> Open Source | <b>Red:</b> Closed Source | <b>Yellow:</b> Mixed/Shared Source
    <br> (크게 보려면 <a href="https://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg" target="_blank" rel="noopener noreferrer">여기</a>를 클릭)</center></small>
</p>
<p>
  Unix 라는 이름은 Multics 프로젝트의 Multic의 Multi-를 Uni-로 바꾼 말장난에서부터 탄생했다. UNICS 에서 UNIX로 최종 변경되었다. <br>
  <sub>* 1970년 Brian Kernighan이 UNICS 에서 UNIX로 명명</sub>
</p>
<h2>MULTICS Project</h2>
<img src="/media/multics.png" alt="MULTICS" class="rdimg">
<p>
 <b>Mult</b>iplex <b>I</b>nformation and <b>C</b>omputing <b>S</b>ervice | 대화식 다중 사용자 시스템<br><br>
 대화식 다중 사용자 시스템이란 여러 명의 사용자가 같은 컴퓨터에서 동시에 작업 가능한 시스템이라 할 수 있다. UNIX가 개발되기 이전 다른 OS들은 한 시스템에서 한 사용자만 접근할 수 있었다. UNIX는 멀티유저(Multi-user)와 멀티태스킹(Multi-tasking)이 가능하며 이식성과 호환성이 뛰어난 OS이다.<br>
 <sub>* <b>멀티유저 :</b> 여러명의 유저가 동시가 동일한 하나의 컴퓨터를 공유 가능</sub><br>
 <sub>* <b>멀티태스킹 :</b> 동시에 여러 명령어를 처리 가능</sub><br>
 <sub>* <b>이식성 및 호환성 :</b> 특정 하드웨어에 종속적이지 않고 어떤 하드웨어에도 제한없이 사용 가능</sub>
 <br><br>
 UNIX의 탄생은 Multics Project 로 부터 비롯되었다. 멀틱스 프로젝트는 AT&T 벨 연구소, MIT, General Electric 라는 세가지 그룹이 모여 1965년 부터 시작하여 1972년 끝을 맺었다. <br>
 <sub>* 벨 연구소는 다른 두 조직과의 방침 차이로 인해 1969년부터는 멀틱스 프로젝트를 더 이상 진행하지 않았다.
</sub><br><br>
 멀틱스 프로젝트의 목표는 아래와 같다. 
 <ul>
  <li>같은 컴퓨터에서 동시에 여러 유저가 작업 가능한 환경</li>
  <li>충분한 계산력과 데이터의 저장</li>
  <li>데이터전송을 원하는 유저끼리의 손쉬운 데이터 전송</li>
 </ul>
</p>
<h2>History of Unix</h2>
<p>
  유닉스의 역사는 길고 길기에 1991년 LINUX가 등장하기 전까지만 살펴보도록 하겠다.<br>
  <sub>* LINUX에 대해서만 알고자 한다면 이 부분은 뛰어넘도록 하자.</sub>
  <table>
    <tr>
      <th><center>Year</center></th>
      <th><center>Note</center></th>
    </tr>
    <tr>
      <td>
        <b><center>1965</center></b><br>
      </td>
      <td>
        멀틱스 프로젝트 시작
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1969</center></b><br>
      </td>
      <td>
        벨 연구소의 켄 톰슨(Ken Thompson)이 홀로 1개월 정도의 시간을 투자하여 초기 형태의 UNIX를 개발하였다.
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1971</center></b><br>
      </td>
      <td>
        첫번째 에디션 PDP-11/20
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1972</center></b><br>
      </td>
      <td>
        데니스 리치가 켄 톰슨의 B언어를 토대로 C언어를 만들었다. C언어는 UNIX 를 만들어내기 위해 개발된 언어이다. C가 개발되기 전에는 프로그램 개발을 어셈블리 언어로 하였었다. 고급언어로 유닉스를 개발하기 위해 C를 만들어 냈던것. Unix는 범용 사용자 방식의 시분할 운영체제이다.<br><br>
        <sub>
        * B 언어는 데니스 리치의 감수하에 켄 톰슨이 만들었다. B언어는 멀틱스의 BCPL(Basic Combined Programming Language)을 바탕으로 개발된 언어이다. <br><br>
        * B 라는 이름은 연구소의 B를 따서 명명<br><br>
        * C 라는 이름은 알파벳 B 다음이 C이기에 C로 명명했다.
        </sub>
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1973</center></b><br>
      </td>
      <td>
        데니스 리치와 톰슨이 기존의 어셈블리어로 되어 있던 Unix의 Kernel을 고급언어인 C언어로 다시 작성. 이로써 최초의 이식가능한 운영체제 (Portable Operating System)가 탄생하게 되었다. C는 UNIX운영체제의 근본이 되는 언어라고 할 수 있다. Unix 운영 체제의 90% 이상이 C언어로 작성되어 있기 때문이다. 개발자들 사이에서 이식성과 호환성이 뛰어난 UNIX 뿐만아니라 강력하고 융통성이 좋은 C언어 또한 빠르게 퍼졌다. 유닉스와 C 이전의 프로그램 개발은 PDP-7 컴퓨터에서 어셈블리어를 사용하였다. <br><br>
        <sub>
          * <b>PDP-7 :</b> PDP는 Programmed Data Processor의 줄임말이다. Digital Equipment Corporation(DEC)에서 내놓은 18비트 미니컴퓨터중 하나. 1965년에 등장하였다. PDP 시리즈에 관해 더 알고싶으면 <a href="http://www.linfo.org/pdp-7.html" target="_blank" rel="noopener noreferrer">여기</a>를 클릭하자
        </sub>
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1975</center></b><br>
      </td>
      <td>
        UNIX의 6번째 version
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1979</center></b><br>
      </td>
      <td>
        UNIX의 7번째 version
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1980</center></b><br>
      </td>
      <td>
        마이크로소프트사에서 UNIX시스템 기반의 Xenix를 출시. 16비트 마이크로컴퓨터용 운영 체계
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1982</center></b><br>
      </td>
      <td>
        AT&T의 USG(Unix System Group)에서 System III를 출시. HP-UX 와 Ultrix-11이 소개됨.
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1983</center></b><br>
      </td>
      <td>
        AT&T에서 유닉스의 최초 상용버전인 System V 출시
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1984</center></b><br>
      </td>
      <td>
        버클리대에서 4.2BSD를 공개. 여러 편리한 기능들 메일, 가상기억장치, TCP/IP와 같은 것들이 추가되었다. SYSTEM V 2(SVR 2)의 출시. 전 세계적으로  UNIX가 100,000번 설치 되었다.
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1986</center></b><br>
      </td>
      <td>
        4.3BSD의 출시. <br>
        BSD에 관한 자세한 정보는 <a href="https://ko.wikipedia.org/wiki/BSD" target="_blank" rel="noopener noreferrer">여기</a>에서
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1987</center></b><br>
      </td>
      <td>
        SVR 3 출시. 이 시기 전 세계적으로 UNIX가 750,000번 설치 되었다. IRIX가 소개됨.<br>
        앤드루 타넨바움(Andrew S. Tanenbaum)이 미닉스(MINIX) 개발<br><br>
        <sub>* 미닉스 운영체제를 만든 앤드루와 리눅스 운영체제를 만든 리누스의 1992년 1월 29일에 시작된 논쟁은 <a href="https://groups.google.com/forum/?hl=ko#!search/comp.os.minix/comp.os.minix/wlhw16QWltI/XdksCA1TR_QJ" target="_blank" rel="noopener noreferrer">여기</a>서 볼 수 있다.</sub>
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1988</center></b><br>
      </td>
      <td>
        POSIX 1 가 공개됨. Portable Operating System Interface + X 의 줄임말이다. POSIX 는 IEEE가 제정한 유닉스의 API의 규격이다.
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1989</center></b><br>
      </td>
      <td>
        SVR 4  출시.
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1990</center></b><br>
      </td>
      <td>
        X/Open라는 시스템 제작회사에서 XPG3(x/open Portability Guide)라는 UNIX System 규약을 발표
      </td>
    </tr>
    <tr>
      <td>
        <b><center>1991</center></b><br>
      </td>
      <td>
        리누스 토르발스가 리눅스라는 OS 개발 발표
      </td>
    </tr>
  </table><br>
</p>
<p>
  1991년 LINUX가 등장하였다. LINUX의 뿌리인 UNIX에 대해서는 이만큼 보도록 하고 지금부터는 LINUX에 대해 살펴보자.
</p>
<h2>About LINUX</h2>
<img src="/media/linux.png" alt="LINUX" class="rdimg" width="150"><br>
<p>
  리눅스는 리누스 토르발스에 의해 탄생했다.<br><br>
  <b>1991년 8월 25일</b><br>
  당시 21살이던 리누스 토르발스(Linus Benedict Torvalds)는 핀란드의 헬싱키 대학(University of Helsinki)에 재학중이었다. 그는 Linux라는 공개용 OS 프로그램을 유즈넷 뉴스그룹에 공개했다.<br><br>
  <b>1991년 10월 1일</b><br>
  온라인에서 Linux 0.01를 배포하였다. 초기의 리눅스는 많은 해커들이 참여하여 만들었다.<br><br>
  <b>1992년 1월 5일</b><br>
  Linux 커널이 GNU GPL(General Public License)로 재허가를 받았다. <br><br>
  리눅스는 개발자 친화적이기에 많은 엔지니어들의 사랑을 받는다. 리눅스는 시스템을 운영을 위한 OS로써 제일 높은 점유율을 갖고 있다. 리눅스가 가진 특징을 꼽자면 오픈소스, 보안성, 신뢰성, 호환성, 그리고 안정성이라 할 수 있겠다.
  <ul>
    <li>오픈소스</li>
    여러 개발자가 함께 참여하는 개방형 개발방법이다. 소스코드가 모두에게 투명히 공개된다. 저작권이 없기 때문에 비용을 지불할 필요가 없다. 버그를 발견했을 시 사용자와 개발자 모두 참여하여 해결할 수 있다.
    <li>보안성</li>
    소스코드가 공개되어 있기에 취약점이 발견된다면 빠른 보안 업데이트가 진행된다. 지속적으로 보안 패치가 이루어지면서 소프트웨어는 더 견고해진다.
    <li>안정성</li>
    효율적인 자원관리가 가능하다.
    <li>호환성</li>
    여러 시스템에 적용 가능하다. 광범위한 하드웨어 뿐만 아니라 다양한 프로세서 아키텍쳐<small>(Alpham PowerPC, ARM, AVr, x86 등)</small>도 지원된다.
    <li>신뢰성</li>
    다수의 개발자와 사용자에 의해 테스트 되고 디버깅 되기 때문에 상당한 신뢰성을 지니게 된다.
  </ul>
</p>
<h3>LINUX 배포판</h3>
<p>
  리눅스는 다양한 배포판이 존재한다.
  <ul>
    <li>레드햇 (Red Hat)</li>
    <img src="/media/redhat.png" alt="RED HAT" width="150" align="left">
    <p>&nbsp;미국의 레드햇사가 개발한 배포판</p>
    <li>페도라 (Fedora)</li>
    <img src="/media/fedora.png" alt="Fedora" width="150" align="left">
    <p>&nbsp;레드햇 계열의 배포판</p>
    <li>센트OS (CentOS)</li>
    <img src="/media/centos.png" alt="CentOS" width="150" align="left">
    <p>&nbsp;플랫폼 제공의 목적으로 만들어진 무료 배포판</p>
    <li>우분투 (Ubuntu)</li>
    <img src="/media/ubuntu.png" alt="Ubuntu" width="150" align="left">
    <p>&nbsp;데비안 기반의 배포판</p>
    <li>민트 (Mint)</li>
    <img src="/media/mint.png" alt="Mint" width="150" align="left">
    <p>&nbsp;우분투와 데비안을 기반으로 개발된 배포판</p>
    <li>수세 (SuSE)</li>
    <img src="/media/suse.png" alt="SUSE" height="45" align="left">
    <p>&nbsp;독일에서 출시된 배포판</p>
    <li>안드로이드 (Android)</li>
    <img src="/media/android.png" alt="Android" width="150" align="left">
    <p>&nbsp;리눅스의 커널을 사용</p>
  </ul>
</p>
<p>
  이처럼 다양한 배포판이 존재하는 이유는 GNU의 자유소프트웨어 정신으로 비롯된 것이다. 자유소프트웨어는 저작권 없이 자유롭게 배포 가능한 소프트웨어를 뜻한다. LINUX와 GNU는 뗄레야 뗄 수 없는 관계이기 때문에 GNU가 무엇인지 아래서 알아보도록 하자.<br>
  <sub>* 리눅스 배포판은 너무나 광범위하기에 자세히 다루지는 않겠다. 더 관심이 있다면 <a ref="https://en.wikipedia.org/wiki/List_of_Linux_distributions" target="_blank" rel="noopener noreferrer">여기서</a> 공부해 보도록 하자</sub>
</p>
<h2>GNU</h2>
<img src="/media/gnu.png" alt="GNU" class="rdimg"  vspace="40px" width="300px">
<p>
  <b>GNU: G</b>NU is <b>N</b>ot <b>U</b>nix<br>
  GNU로 부터 자유 소프트웨어(Free Software)가 시작되었다. 저작권이 없는 무료 소프트웨어를 제작 및 배포하기 위한 프로젝트이다. Copyleft 운동이라고 할 수 있는데 저작권을 의미하는 Copyright에 반대되는 개념으로써 저작권의 공유를 의미한다. 언어유희로써 -right의 반대인 -left를 사용하였다. GNU는 1983년 MIT출신 리처드 스톨만(Richard Stallman)이 만든 유닉스 계열 OS 이다. GNU의 정신은 ‘소프트웨어의 자유로운 실행, 복사, 수정, 배포' 라 볼 수 있다. GNU는 LINUX와 결합하여 엄청난 상승효과를 받았다.<br>
  <sub>* ‘오픈소스’와 ‘자유 소프트웨어’는 같은 의미가 아니다. 차이점을 보고 싶다면  이 글<a href="http://www.zdnet.co.kr/view/?no=20180206130532" target="_blank" rel="noopener noreferrer">(오픈소스 20년...일상에 물처럼 스며들다)</a>을 추천한다.</sub><br><br>
  리눅스는 엄밀히 말하자면 운영체제제 전체를 뜻하기 보단 커널을 뜻한다. 리눅스 프로젝트는 유닉스 형태의 커널을 개발하기 위해 시작되었다. 커널이 존재하지 않았던 GNU에 토르발즈의 리눅스 프로젝트는 많은 사람들의 이목을 끌었다. 이는 다수의 GNU 와 연관된 개발자의 참여를 불렀다. 리눅스로 인해 GNU에 커널이 더해짐으로써 완전한 자유 운영체제가 되었다. 그로인해 GNU/LINUX 라 표기된다. <br><br>커널은 OS에서 핵심이 되는 프로그램이다. 하드웨어와 OS의 소통, 보안과 같은 중요한 부분을 담당한다. 커널만으로는 시스템이 돌아갈 수 없기에 커널 위에 다양한 프로그램을 얹어서 사용해야 한다. 이러한 이유로 여러 리눅스 배포판이 탄생한 것이다.<br>
  <sub>* 커널의 종류로써는 단일형 커널(monolithic kernel), 마이크로 커널(microkernel), 혼합형 커널(hybrid kernel), 나노 커널(nanokernel), 엑소커널(exokernel) 등이 있다.</sub>
</p>
<h2>Reference</h2>
<p>
  <ul>
    <li><a href="https://www.google.com/search?ei=APFXXYSkNeKMr7wPj8eF6Ac&q=linux+history+site%3A.edu&oq=linux+history+site%3A.edu&gs_l=psy-ab.3...1019.1583..1803...0.0..0.115.325.1j2......0....1..gws-wiz.......35i39..11%3A1j12%3A1j13%3A0.UIVYjHNo6t8&ved=0ahUKEwiEpK6J8onkAhVixosBHY9jAX0Q4dUDCAo&uact=5" target="_blank" rel="noopener noreferrer">Unix/Linux: History and Philosophy</a></li>
    <li><a href="http://learn.linksprite.com/pcduino/linux-applications/a-complete-historical-timeline-of-linux-evolution/" target="_blank" rel="noopener noreferrer">A Complete Historical Timeline of Linux Evolution</a></li>
    <li><a href="https://hiello.tistory.com/89" target="_blank" rel="noopener noreferrer">리눅스의 개요</a></li>
    <li><a href="http://www.unix.org/what_is_unix/history_timeline.html" target="_blank" rel="noopener noreferrer">UNIX Past</a></li>
    <li><a href="https://dog-developers.tistory.com/34" target="_blank" rel="noopener noreferrer">유닉스의 탄생
</a></li>
    <li><a href="http://www.linfo.org/pdp-7.html" target="_blank" rel="noopener noreferrer">PDP-7 Definition</a></li>
    <li><a href="https://en.wikipedia.org/wiki/Tanenbaum%E2%80%93Torvalds_debate" target="_blank" rel="noopener noreferrer">Tanenbaum–Torvalds debate</a></li>
    <li><a href="https://www.guru99.com/difference-unix-vs-linux.html" target="_blank" rel="noopener noreferrer">Unix Vs. Linux: What’s the Difference?</a></li>
    <li><a href="https://ko.wikipedia.org/wiki/%EC%BB%A4%EB%84%90_(%EC%BB%B4%ED%93%A8%ED%8C%85)" target="_blank" rel="noopener noreferrer">커널 (컴퓨팅)</a></li>
  </ul>
</p>