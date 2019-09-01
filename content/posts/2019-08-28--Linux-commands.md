---
title: Linux Commands
date: "2019-08-28T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/Linux-commands/"
category: "OS"
tags:
  - "TIL"
  - "Linux"
  - "Commands"
  - "리눅스 명령어"

description: "자주 쓰이는 리눅스 명령어에 대해 가볍게 살펴보자"
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
    line-height: 30px;
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
    line-height: 30px;
  }
  .alignR{
    text-align: left;
  }
  table{
    width: 100%;
    line-height: 25px;
    margin: 20px;
  }
  table, td, tr{
    border: 1px solid #2680d9;
    text-align: left;
    font-size: 13px;
    border-collapse: collapse;
    padding: 10px;
  }
  th{
    border: 1px solid #2680d9;
    font-size: 15px;
    padding: 10px;
  }
  tr:first-child{
    background-color: #3BAFC9;
    color: white;
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
<link href="https://fonts.googleapis.com/css?family=Nanum+Gothic+Coding&display=swap" rel="stylesheet">
<div style="font-family: 'Nanum Gothic Coding', monospace;">
<img src="/media/linuxCommands.jpg" alt="Linux Commands" class="rdimg"  vspace="15px" height="250">
<small><center><p style="padding-bottom: 15px; display:block; clear:both" > Image Source : Redbubble.com</center></small>
<p>
  다양한 리눅스 명령어 중에서 자주 쓰이는 명령어들에 대해 알아보도록 하자.
</p>
    <table>
      <tr>
        <th><center>Commands</center></th>
        <th><center>About</center></th>
      </tr>
      <tr>
        <td>
          <b><center>cd</center></b>
        </td>
        <td>
          <center>Change Directory<br>하위 디렉토리로 이동</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>cd ..</center></b>
        </td>
        <td>
          <center>상위 디렉토리로 이동</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>cp</center></b>
        </td>
        <td>
          <center>
            Copy<br>
            파일 복사
          </center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>adduser</center></b>
        </td>
        <td>
          <center>시스템에 사용자 추가</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>ls</center></b>
        </td>
        <td>
          <center>
            list<br>
            디렉토리 내 존재하는 파일 보기
          </center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>cat</center></b>
        </td>
        <td>
          <center>터미널 상의 텍스트 파일 보기</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>rm</center></b>
        </td>
        <td>
          <center>파일 지우기</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>rm p</center></b>
        </td>
        <td>
          <center>패키지 지우기</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>rmdir</center></b>
        </td>
        <td>
          <center>
            Remove Directory<br>
            디렉토리 지우기
          </center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>mkdir</center></b>
        </td>
        <td>
          <center>
            Make Directory<br>
            디렉토리 만들기
          </center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>mv</center></b>
        </td>
        <td>
          <center>
            Move<br>
            파일이 있는 위치 변경
          </center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>top</center></b>
        </td>
        <td>
          <center>메모리 상태 보기</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>mount</center></b>
        </td>
        <td>
          <center>장치 연결</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>unmount</center></b>
        </td>
        <td>
          <center>장치 해제</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>kill</center></b>
        </td>
        <td>
          <center>프로세스 종료</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>ps</center></b>
        </td>
        <td>
          <center>
            Process<br>
            현재 작동중인 모든 프로세스들 보기
          </center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>find x -name y -print</center></b>
        </td>
        <td>
          <center>디렉토리 x에서 파일 y를 찾아 화면에 출력</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>halt</center></b>
        </td>
        <td>
          <center>시스템 종료</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>touch</center></b>
        </td>
        <td>
          <center>
            새로운 파일 만들기<br>
            빈 파일만 생성된다.
          </center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>vi newfile</center></b>
        </td>
        <td>
          <center>만들어지는 새 파일을 vi 편집기 상태로 들어감</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>passwd</center></b>
        </td>
        <td>
          <center>패스워드 변경</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>history</center></b>
        </td>
        <td>
          <center>작성한 명령어들 전부 출력하기</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>df</center></b>
        </td>
        <td>
          <center>용량 확인</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>whoami</center></b>
        </td>
        <td>
          <center>접속 유저 확인</center>
        </td>
      </tr>
    </table>
  </p>