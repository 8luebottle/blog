---
title: Linux Filesystem
date: "2019-08-29T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/Linux-filesystem/"
category: "OS"
tags:
  - "TIL"
  - "Linux"
  - "Filesystem"

description: "리눅스의 커널이 파일시스템의 파일들을 어떻게 관리할까 ?"
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
<img src="/media/filesystem.png" alt="Linux Filesystem" class="rdimg"  vspace="15px" height="250">
<h2>File System</h2>
<p>
리눅스는 계층적인 트리구조<small>( 많은 파일들을 가지고 있기 때문에 이것을 관리하기 위해 계층 구조를 갖고 있다.)</small>로 파일을 관리한다. 파일시스템은 어떻게 관리할 것인가에 대한 정책이다.

리눅스는 다양한 파일 시스템을 지원한다. 이는 유연성을 높여주고 다른 운영체제와 잘 공존할 수 있게 해준다.

<ol>
  <li>File</li>
  Metadata region 과 Data region으로 나뉜다.
  <li>Directory</li>
  Data 영역이 있다. 여러개의 파일을 묶어 그룹으로 만든다.
</ol>
</p>

<h2>File</h2>
<p>
	파일이란 디스크와 같은 물리적 저장 매체에 저장되는 데이터 집합을 말한다. 데이터 정보에 대한 논리적인 저장 단위이며 저장장치의 물리적 특성을 추상화한 논리적 저장 단위이다. 파일들은 모두 2진수로 저장된다. 파일의 타입으로는 크게 두 종류로 나뉜다.
  
  <ol>
    <li>Text file | 텍스트 파일</li>
    ASCII 또는 Unicode → 8 bit/ 16bit로 끊어서 → 문자로 해석
    <li>Binary file | 바이너리 파일</li>
    이진수 데이터 → format 에 따라, 특별한 해석 <br>
    .jpg → image | .mp3 → music | .mpg → video
  </ol>
</p>

<h2>Linux’s native filesystem types</h2>
<p>
  리눅스의 파일 시스템 타입으로는 ext3, ext4, squashfs, btrfs 등이 있다.<br><br>
  
  <b>ext2, ext3, ext4</b><br>
  Extended FIlesystem<br>
  Chris Provenzano가 처음으로 만든 파일 타입이다. 라이너스 토발즈가 다시 썼다. 긴 파일이름을 지원한다.최대 255 캐릭터 까지 가능하다.
  <ul>
    <li>ext → (primarily was developed of MINIX)</li>
    <li>ext2 → improved version</li>
    <li>ext3 → added performance improvement</li>
    <li>ext4 → was a performance improvement besides additional providing additional features. (Ext4 is the preferred and most widely used Linux file System.)</li>
  </ul>
</p>
<p>
  <b>JFS</b><br>
  Journaled File System (developed by IBM for AIX UNIX)

  <b>XFS</b><br>
  High speed JFS (NASA still usages this file system)

  <b>trfs</b><br>
  B-Tree FIles System focus on fault tolerance
</p>
