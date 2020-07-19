---
title: Goroutine
date: "2020-07-19T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/goroutine/"
category: "Go"
tags:
  - "TIL"
  - "golang"
  - "goroutine"
  - "고루틴"
  - "concurrency"
  - "wecode"

description: "goroutine 에 관하여 알아보자"
---
<head>
<style>
  code {background-color: #ececec}
  p    {font-size: 15px;}
  tr   {text-align: right;}
  sub { font-size: 14px; vertical-align: middle; padding-left: 10px; line-height: 30px; color: #2680d9;}
  /* li {margin: 20px 0px;list-style: none;} */
  strong {font-size: 18px;vertical-align: middle;}
  small {color: #808080; padding: 0px 3px;}
  #rcorners {
    border-radius: 25px;
    border: 2px solid #dd4ecf;
    padding: 20px; 
    width: 200px;
    height: 150px;  
  }
  .rdimg {border-radius: 25px;}
  img{margin-bottom: 10px;}
  ol, ul{line-height: 30px;}
  .alignR{text-align: left;}
  table{ width: 100%; line-height: 25px; margin: 20px; font-size: 14px; padding:10px;}
  a {text-decoration: none;}
  td {text-indent: 10px;}
</style>
</head>

<body>
<link href="https://fonts.googleapis.com/css?family=Nanum+Gothic+Coding&display=swap" rel="stylesheet">
<center>
  <div style="font-family: 'Nanum Gothic Coding', monospace;">
  <img src="https://user-images.githubusercontent.com/48475824/87862091-41cddd80-c987-11ea-9843-2576afb705b2.gif" vspace="15px" width="300" class="rdimg">
</center>

### Table of Contents
<small>링크를 클릭하면 해당 내용으로 이동합니다</small>

 + [About Goroutine](#about-goroutine)
 + [Create Goroutine](#create-goroutine)<br>
   <sub>
    [main goroutine](#main-goroutine)
   </sub>
 + [References](#references)


## About Goroutine  
<p>
Go 는 Concurrent 언어이다.<br>
Go 에서는 동시성(병행성) 구현을 위해 goroutine 을 사용한다.<br>
  <sub>
    * Concurrency ≠ Parallelism 동시성과 병렬성은 다르다. <br>
    <small> &nbsp;&nbsp;Concurrency(동시성 / 병행성) Vs. Parallelism(병렬성) 에 관하여는 다른 포스트에서 다룰 것이다.<br><br>
    </small>
  </sub>
  고루틴을 통해 한번에 여러개의 일을 동시에 실행할 수 있게 된다.  각각 실행되는 고루틴은 독립적으로서<small>(의존적이지 않은 관계)</small>서로에게 영향을 주지 않는다.  

  경량 스레드(thread)인 고루틴은 Go runtime에 의해 관리된다.  
  <sub>
    * 스레드 : 프로세스 내에서 실행되는 흐름의 단위  
  </sub><br>
  여기서의 경량<small>(lightweight)</small>은 고루틴을 생성하는데 적은 메모리가 든다는 것을 의미한다.  
  OS의 Thread 와 goroutine<small>(일종의 스레드)</small> 을 비교하였을 때 고루틴의 가벼움을 확실히 느낄 수 있다. 보통의 OS Thread 같은 경우 개당 1MB의 메모리 크기가 필요하지만 goroutine은 단지 2KB(0.002 MB) 크기로서 생성 가능하기 때문이다.<br>
  만약 기본 크기보다 더 큰 스택이 필요할 시에는 동적으로 증가하게 된다.
  <br>
  <sub>
    * <b>Go 1.2 :</b> goroutine의 스택사이즈는 4KB 에서 8KB로 늘어남.
  </sub><br>
  <sub>
    * <b>Go 1.4 :</b> gorouitne의 스택사이즈는 8KB 에서 2KB로 줄어듬. (현재 2KB)
  </sub>
</p>


 Go 에서는 <a style="text-decoration:none" href="https://github.com/8luebottle/TIL/blob/master/Go/channel.md" target="_blank" rel="noopener noreferrer">Channel</a> 이라는 것이 존재하는데, 이는 고루틴끼리 통신을 하기 위한 통로가 된다.
 <img width="680" alt="go channel" src="https://user-images.githubusercontent.com/48475824/87861805-ab98b800-c984-11ea-9f19-80ea3fe7dc80.png" class="rdimg">

[↑ return to TOC](#table-of-contents)

## Create Goroutine
<code>go</code> 키워드를 통해 고루틴을 생성할 수 있다.  
간단히 함수 혹은 메서드 앞에 <code>go</code> 키워드를 붙여주면 된다.  

<div style="color:#f0f0f0;font-family:Consolas,'Liberation Mono', Menlo, Courier, monospace;overflow:auto"><table style="margin:0;padding:0;background-color:#272727;border-radius:4px;" cellpadding="0"><td style="padding:5px 0;text-align:left">&nbsp;go&nbsp;func()</td></table></div>

<p>
  <sub>
    * Go 런타임은 위의 고루틴을 비동기적 (asynchronously) 으로 실행시킨다.
  </sub>
</p>


`gist:8luebottle/bd58660e470fc67723886af4cdec9324#gistfile1.go`

### main goroutine
<p>
  프로그래머가 goroutine을 생성하기 전에도 goroutine은 존재한다. 이를 main goroutine이라 부른다.<br>
  즉, 모든 고 프로그램에는 최소 한개의 고루틴이 존재하는 셈이다. 추후에 프로그래머에 의해 생성되는 고루틴은 main goroutine 아래에서 돌아가게 된다. 
</p>


[↑ return to TOC](#table-of-contents)


## References
[A Tour of Go | Goroutines](https://tour.golang.org/concurrency/1#:~:text=A%20goroutine%20is%20a%20lightweight%20thread%20managed%20by%20the%20Go%20runtime.&text=The%20evaluation%20of%20f%20%2C%20x,shared%20memory%20must%20be%20synchronized.)  
[Go: How Does the Goroutine Stack Size Evolve?](https://medium.com/a-journey-with-go/go-how-does-the-goroutine-stack-size-evolve-447fc02085e5)  
[Gorotuines-Concurrency in Golang](https://www.geeksforgeeks.org/goroutines-concurrency-in-golang/?ref=lbp)  