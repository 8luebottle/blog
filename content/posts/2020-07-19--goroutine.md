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
    [Sound Wave Example](#sound-wave-example) <br>
   </sub>
   <sub>
    [main goroutine](#main-goroutine)
   </sub>
 + [References](#references)

> 👩‍💻 해당 포스트는 연재 중입니다 👩‍💻

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

### Sound Wave Example
아래는 sync 패키지를 사용한 고루틴의 예제 코드이다.  
소리를 시각화한 형태인 Sound bar 처럼 구현해보았다.

<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div><div style="line-height:130%">27</div><div style="line-height:130%">28</div><div style="line-height:130%">29</div><div style="line-height:130%">30</div><div style="line-height:130%">31</div><div style="line-height:130%">32</div><div style="line-height:130%">33</div><div style="line-height:130%">34</div><div style="line-height:130%">35</div><div style="line-height:130%">36</div><div style="line-height:130%">37</div><div style="line-height:130%">38</div><div style="line-height:130%">39</div><div style="line-height:130%">40</div><div style="line-height:130%">41</div><div style="line-height:130%">42</div><div style="line-height:130%">43</div><div style="line-height:130%">44</div><div style="line-height:130%">45</div><div style="line-height:130%">46</div><div style="line-height:130%">47</div><div style="line-height:130%">48</div><div style="line-height:130%">49</div><div style="line-height:130%">50</div><div style="line-height:130%">51</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">package</span>&nbsp;main</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">import</span>&nbsp;(</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ffd500">"fmt"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ffd500">"sync"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ffd500">"time"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//&nbsp;Note&nbsp;:&nbsp;Keep&nbsp;in&nbsp;mind&nbsp;of&nbsp;WaitGroup&nbsp;(concurrent-safe&nbsp;counter)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//&nbsp;In&nbsp;this&nbsp;example&nbsp;I'm&nbsp;going&nbsp;to&nbsp;use&nbsp;three&nbsp;Methods</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//&nbsp;(1)&nbsp;wg.Add&nbsp;&nbsp;&nbsp;(2)wg.Done&nbsp;&nbsp;&nbsp;(3)wg.Wait</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">var&nbsp;(</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;wg&nbsp;sync.WaitGroup</div><div style="padding:0 6px; white-space:pre; line-height:130%">)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">var&nbsp;(</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;shortSong&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">10</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">var&nbsp;(</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;wave1&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ffd500">"■&nbsp;1"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;wave2&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ffd500">"■■&nbsp;2"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;wave3&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ffd500">"■■■&nbsp;3"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;wave4&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ffd500">"■■■■&nbsp;4"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;wave5&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ffd500">"■■■■■&nbsp;5"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;wave6&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ffd500">"■■■■■■&nbsp;6"</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">func&nbsp;soundWave(s&nbsp;string)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>&nbsp;i&nbsp;:<span style="color:#0086b3"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">0</span>;&nbsp;i&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">&lt;</span>&nbsp;shortSong;&nbsp;i<span style="color:#0086b3"></span><span style="color:#ff3399">+</span><span style="color:#0086b3"></span><span style="color:#ff3399">+</span>&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fmt.Printf(<span style="color:#ffd500">"%v\n"</span>,&nbsp;s)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;time.Sleep(time.Millisecond&nbsp;<span style="color:#0086b3"></span><span style="color:#ff3399">*</span>&nbsp;<span style="color:#c10aff">100</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;wg.Done()&nbsp;&nbsp;&nbsp;<span style="color:#999999">//&nbsp;Done&nbsp;--&gt;&nbsp;indicate&nbsp;to&nbsp;the&nbsp;WaitGroup&nbsp;that&nbsp;you've&nbsp;exited</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">func&nbsp;playMusic2()&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;wg.Add(<span style="color:#c10aff">6</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;go&nbsp;soundWave(wave1)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;go&nbsp;soundWave(wave2)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;go&nbsp;soundWave(wave3)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;go&nbsp;soundWave(wave4)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;go&nbsp;soundWave(wave5)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;go&nbsp;soundWave(wave6)</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">func&nbsp;main()&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;playMusic()</div><div style="padding:0 6px; white-space:pre; line-height:50%">&nbsp;&nbsp;&nbsp;&nbsp;wg.Wait()&nbsp;&nbsp;&nbsp;<span style="color:#999999">//&nbsp;Wait&nbsp;&nbsp;--&gt;&nbsp;inidcate&nbsp;goroutines&nbsp;has&nbsp;exited</span></div><div style="padding:2 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><br></td></tr></table></div>

Line 40-45 번에서 비동기로 <code>soundWave</code> 라는 함수를 실행시킨다.  
총 6개의 Wave는 동시에 실행되기 때문에 어떤 함수가 먼저 실행되고 끝날지는 우리는 알지 못한다. 매번 코드를 실행시킬 때마다 결과가 다르게 나올 것이다.  
<img alt="sound bar" src="https://user-images.githubusercontent.com/48475824/87868605-abbfa480-c9d2-11ea-866c-20a6e5541e9b.gif" vspace="15px" width="250" class="rdimg">



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