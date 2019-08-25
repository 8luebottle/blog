---
title: Linux Boot Loader
date: "2019-08-19T11:11:11.121Z"
template: "post"
draft: false
slug: "/posts/linux-boot-loader/"
category: "OS"
tags:
  - "TIL"
  - "Linux"
  - "Boot loader"

description: "파워 버튼을 누르면 제일 먼저 실행되는 리눅스의 프로그램인 boot loader에 대해 알아보자"
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
  table, td, th, tr{
    border: 1px solid #2680d9;
    text-align: left;
    font-size: 13px;
    border-collapse: collapse;
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
<link href="https://fonts.googleapis.com/css?family=Sunflower:300&display=swap" rel="stylesheet">
<div style="font-family:Sunflower;">
<img src="/media/linux_gnu.jpg" alt="Linux GNU" class="rdimg"  vspace="15px" height="250">
<small><center><p style="padding-bottom: 15px; display:block; clear:both" > Image Source : Redbubble.com</center></small>
<center font-size="13px">시스템 파워 버튼을 누른 다음 리눅스에서는 어떠한 일이 일어날까? </center><br>
<h3>Boot Loader</h3>
<p>
  부트로더는 OS를 부트 시킬때 실행되는 프로그램이다. 즉 가장 먼저 실행되는 프로그램이라 할 수있다. 부트로더는 하드웨어 의존성이 강하기에 각각의 OS별로 다른 부트로더들이 사용된다. 우리는 리눅스의 부트로더에 대해 알아볼 것이다.
  <br><sub><b>* boot :</b> 컴퓨터에 리셋을 발생시켜 새롭게 컴퓨터를 기동시키는 작업 | 전원을 누르는 순간부터 바탕화면이 뜨는 그 순간까지를 의미</sub>
</p>
<p>
  만약 컴퓨터에 단 하나의 OS만 존재한다면 부트로더는 해당 커널을 로드하기만 하면 된다. 하지만 여러 OS가 설치되어있거나 다양한 커널이 설치되어 있다면 컴퓨터는 그 중에 어떤 것(OS든 커널이든)을 사용할것인지 우리가 선택하도록 해준다. 부트로더는 운영체제가 실행되기 전에 필히 먼저 실행되야 하는 프로그램으로써 커널이 올바르게 작동될 수 있도록 모든 관련 작업들을 처리한다. 
</p>
<h4>기능</h4>
<p>
  부트로더의 기능은 아래와 같다.
  <ul>
    <li><b>초기화 :</b> 메모리, 하드웨어, 직렬포트, 네트워크, 프로세서 속도, 인터럽트</li>
    <li><b>적재 및 실행 :</b> Kernel, RAM</li>
    <li><b>UI :</b> 사용자 인터페이스 기능</li>
  </ul>
</p>
<h4>6가지 스탭</h4>
<p>
리눅스의 부트로더는 총 6가지<small>(BIOS 부터 Runlevel까지)</small>의 스탭으로 나뉜다. 각각의 스탭은 아래와 같다.
  <!-- <ol>
    <li>BIOS</li>
    <li>MBR</li>
    <li>GRUB</li>
    <li>Kernel</li>
    <li>Init</li>
    <li>Runlevel</li>
  </ol> -->
</p>
<img src="/media/bootloaderStep.png" alt="Step of Bootloader" vspace="30px" width="300">
<p>
  이 여섯가지의 Boot process의 과정을 배움으로써 리눅스에서 발생한 문제를 해결할수 있는 능력이 상승할 것이다. 또한 리눅스 작동원리에 대한 이해력이 높아진다. 스탭별로 어떠한 작업이 이루어지는지 자세히 알아보자.
</p>
<h3>BIOS</h3>
<p>
  <b>BIOS:</b> Basic Input Output System<br>
  파워 버튼을 누르면 파워 서플라이가 전기가 공급되는지 확인을 한 후에 BIOS로 "Power Good" 이라는 신호<small>(+5 volts signal)</small>를 보내게 된다. 이 과정은 보통 0.1초에서 0.5초 정도 소요된다. 
  <img src="/media/powerGood.png" alt="Power Good Signal" vspace="30px" width="300">
  그 후, Boot Process의 첫번째 과정인 BIOS 프로그램이 실행된다. BIOS는 이름이 의미하듯이 모든 데이터의 입출력을 제어하여 주는 프로그램이다. BIOS가 시작되면서 키보드, 스크린을 포함한 하드웨어를 초기화하고 설정한다. 이 과정을 POST<small>(Power On Self Test)</small>라고 한다. Test가 진행되며 여러 요소들을 체크 한 후 POST 과정을 모니터에 출력시킨다. 테스트 내용으로는 System Bus, RTC<small>(Real-Time Clock)</small>, 그래픽 카드, 키보드 동작, RAM등이 있다. 화면에 관련 정보인 BIOS, Mainboard, CPU, 메모리 용량 등이 표시된다. 이 이후 과정은 OS가 주관하게 된다.
  <br><sub>* <b>BIOS</b>는 마더보드에 장착되어 있는 ROM 칩에 저장되어 있다.<br>
  * <b>POST (시동 자체 시험) :</b>BIOS가 CPU에게 POST 작업을 지시한다.
  </sub>  
</p>
<h3>MBR</h3>
<p>
  <b>MBR : </b>Master Boot Record<br>
  POST가 완료되면, 시스템 컨트롤은 BIOS를 부트로더에 옮긴다. 대부분의 경우 부트로더는 하드디스크에 담겨있다. OS를 실행시키기 위해 하드디스크에 저장되어진 정보를 읽어들여야 하는데 이 정보는 MBR에 저장되어 있다. MBR은 기억장치의 512 bytes 저장공간이다. 
  <br><sub>* 리눅스가 부팅이 안되는 상황은 MBR이 제거된 경우에도 벌어진다. 이럴때는 지워진 MBR을 다시 복구해야 한다.</sub>
</p>
<img src="/media/sector.png" alt="Sector" class="rdimg"  vspace="30px" height="500">
<p>
  MBR이 위치한 곳은 기억장치에서 첫번째 섹터<small>(Sector)</small>이다. MBR에는 부팅을 하기 위한 정보를 갖고 있다. MBR은 GRUB 부트로더를 적재시키고 실행한다.
 <br><sub>*<b> Sector:</b> 하드디스크에서 주소 지정을 할 수 있는 최소의 단위 | 섹터단위로 데이터를 읽거나 기록 ( 섹터 하나당 512 바이트 기록 가능)</sub>
</p>
<img src="/media/MBRloads.png" alt="MBR loads GRUB" class="rdimg"  vspace="30px" width="350">
<p>
  MBR은 세 가지 구성요소인 부트코드<small> (446 bytes)</small>, 파티션 테이블 <small>(64 bytes)</small>, 시그니쳐 <small>(2 bytes)</small>로 이루어져 있다. 512 bytes가 어떠한 정보로 이루어져 있는지 살펴보자.<br>
  <sub>* 리눅스에서 부트로더는 GRUB 외에도 다양하다. 다른 종류로는 <b>ISOLINUX</b> (이동식 매체로 부터 부팅 될 때), <b>DAS U-Boot</b> (embedded 디바이스로부터 부팅 될때) 등이 있다.</sub>
</p>
<img src="/media/mbrStruct.png" alt="MBR Structure" class="rdimg"  vspace="30px" height="480">
<img src="/media/mbrArchi.png" alt="MBR Partition Table" vspace="30px" width="400">
<p>
  <ol>
    <li><b>Boot Code 부트코드</b> (446 bytes)</li>
    부팅을 하기 위한 정보가 담겨 있다.<br>
    실행될 코드와 에러 메시지가 저장되어 있다.
    <li><b>Partition Table 파티션 테이블 | 분할표</b> (64 bytes)</li>
    파티션에 관한 정보가 담겨 있다.<br>
    부팅에 필요한 정보가 있는 파티션으로 점프시켜주기 위한 정보.<br>
    총 네개의 파티션으로 나뉘어져 있다. (4 * 16)<br>
    OS는 파티션을 단위로 하여 디스크를 처리한다.
    <table>
      <tr>
        <th><center>10진수</center></th>
        <th><center>16진수</center></th>
        <th><center>About</center></th>
        <th><center>Byte(s)</center></th>
      </tr>
      <tr>
        <td>
          <b><center>0</center></b><br>
        </td>
        <td>
          <center>0x0000</center>     
        </td>
        <td>
          <b>Boot Indicator</b><br>
          부팅 가능시 : 0x80 | 부팅 불가시 : 0x00<br>
          해당 파티션이 부팅 가능한 파티션인지 아닌지를 표시
        </td>
        <td>
          <center>1</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>1~3</center></b><br>
        </td>
        <td>
          <center>0x0001~0x0003</center>
        </td>
        <td>
          <b>Starting CHS Address</b><br>
          CHS의 시작 주소.<br>
          CHS 주소를 사용할 경우 0:06CA 으로 점프.<br>
          부팅 가능한 파티션의 첫 섹터를 읽어 메모리 0:7c00에 덮어쓴다.
        </td>
        <td>
          <center>3</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>4</center></b><br>
        </td>
        <td>
          <center>0x0004</center>
        </td>
        <td>
          <b>Partition Type</b><br>
          파티션의 종류.
        </td>
        <td>
          <center>1</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>5~7</center></b><br>
        </td>
        <td>
          <center>0x0005~0x0007</center>
        </td>
        <td>
          <b>Ending CHS Address</b>
        </td>
        <td>
          <center>3</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>8~11</center></b><br>
        </td>
        <td>
          <center>0x0008~0x000B</center>
        </td>
        <td>
          <b>Starting LBA Address</b><br>
          LBA의 시작주소. 파티션의 시작 위치이다.<br>
          LBA 주소를 사용할 경우 0:06E6 으로 점프.<br>
          부팅 가능한 파티션의 첫 섹터를 읽어 메모리 0:7c00에 덮어쓴다.
        </td>
        <td>
        <center>4</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>12~15</center></b><br>
        </td>
        <td>
          <center>0x000C~0x000F</center>
        </td>
        <td>
          <b>Total Sectors</b><br>
          파티션의 총 색터 개수
        </td>
        <td><center>
          4
        </center></td>
      </tr> 
    </table>
    <sub>
    * 리눅스는 최소 두 개 이상의 파티션을 필요로 한다.
    <br>
    * <b>Partition :</b> 저장장치 내에서 나뉘어진 연속된 논리적 저장공간을 의미한다. 여러개의 파티션으로 나뉜다면 각각의 파티션은 드라이브로 인식된다.  저장공간을 나눔으로써 효율적이며 안전하게 데이터를 관리할 수 있게 된다.
    <br>
    * 파티션 설정 방법은 <b>MBR</b>과 <b>GPT</b>(GUID Partition Table)두 가지로 나뉜다. 대부분의 OS는 더 오래된 방법인 MBR(1983)을 사용한다. 둘의차이점에 대해 알고싶다면 <a href="https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/" target="_blank" rel="noopener noreferrer">여기</a>에서 확인하도록 하자.
    </sub>
    <li><b>Signature</b></li>
    해당 섹터의 오류 확인에 관한 값의 정보<br>
    기본값은 0xAA55 이다. <br>
    값이 0xAA55로 뜨게 된다면 BIOS는 시스템 부팅을 시작한다. 만약 0x0000 값이 뜬다면 '부팅 가능한 디스크를 찾지 못했다'는 의미이기에 BIOS로부터 에러메세지를 받게 된다.
  </ol>
</p>
<img src="/media/bootloaderInAction.png" alt="Bootloader in Action" vspace="30px" width="250">
<p>
  부트로더(MBR)는 partition table을 검사하며 부팅가능한 파티션을 찾는다. 부팅 가능한 파티션을 찾아낸 후에는 두번째로 진행되야 할 부트로더(GRUB)를 찾는다. MBR 은 다음 스탭인 GRUB 를 RAM에 적재시킨 후 실행시킨다.
</p>
<h3>GRUB</h3>
<p>
  <b>GRUB :</b> Grand Unified Bootloader<br>
  리눅스에서 사용하는 부트로더는 LILO<small> (LInux LOader)</small> 와 GRUB 가 있다. 두 방법 모두 싱글유저모드로 부팅하는 기능을 제공해준다. 만약 옛날 리눅스를 사용한다면 LILO 방법을 이용하고 있을 것이다. 현재는 대부분 GRUB를 사용하고 있기에 우리는 GRUB를 알아볼 것이다. GRUB는 GNU에서 만든 부트로더이다.<br>
  <sub>
  * GNU 가 무엇인지 모른다면 <a href="https://babytiger.netlify.com/posts/intro-linux/" target="_blank" rel="noopener noreferrer">이전 포스팅</a>을 참고하자.
  <br>
  * LILO와 GRUB 에 대한 차이점을 자세히 알아보고자 한다면 <a href="http://www.hanbit.co.kr/channel/category/category_view.html?cms_code=CMS6259570844" target="_blank" rel="noopener noreferrer">여기</a>를 통해 공부해보자.</sub>
</p>
<p>
  GRUB를 통해 대부분의 OS 커널을 불러올 수 있다. 아래와 같은 기능을 지원한다.
  <ul>
    <li>사용자 정의  부팅 기능</li>
    <li>파일 시스템 직접 접근 기능</li>
    <li>다양한 실행 파일 형식 지원</li>
    BSD FFS, FAT16, FAT32, Minix, and ext2 etc
    <li>비 멀티부팅 운영 체제 지원</li>
    Multiboot을 지원하지 않는 OS<small>(Linux, FreeBSD, NetBSD, and OpenBSD etc)</small>를 chain-loading을 통해 지원해준다. 체인로딩은 PC BIOS 또는 EFI<small> (Extensible Firmware Interface)</small> 플랫폼에서만 지원이 된다.<br>
    <sub>* Chian-loading 에 관한 자세한 정보는 <a href="https://www.gnu.org/software/grub/manual/grub/html_node/Chain_002dloading.html" target="_blank" rel="noopener noreferrer">여기</a>에서 알아볼 수 있다.</sub>
    <li>메뉴 인터페이스 제공</li>
    <li>다양한 파일 시스템 지원</li>
    <li>자동으로 압축 해제 지원</li>
    gzip
    <li>모든 RAM을 BIOS와 관계 없이 인식</li>
    <li>LBA 및 네트워크 지원</li>
    <li>디스크 없는 시스템 지원</li>
    <li>사람이 읽을 수 있는 설정 파일 제공</li>
  </ul>
</p>
<p>
  BIOS가 부팅 장치를 찾고 MBR을 읽어온 후 GRUB 의 첫번째 스테이지는 MBR 에서 시작된다. 이 후 GRUB 에 위치한 stage 1.5 를 불러들인다. root 디스크의 특정 위치로 부터 stage 2를 불러들여 실행시킨다. 그로인해 메뉴나 명령 프롬프트가 화면에 출력이 된다. LILO 와 비교하였을때 GRUB 가 가지는 가장 큰 특징은 GRUB 는 커널의 물리적인 위치를 알 필요가 없다는 것이다. 즉, 파일명과 커널이 위치하고 있는 파티션만 안다면 커널을 로드할 수 있다. 파일명이 바뀌지 않는이상 매번 GRUB를 실행해 주지 않아도 된다. GRUB 실행 화면을 통해 어떤 커널<small>(두 개 이상 사용시)</small>을 로딩할 것인가 선택할 수 있다.
  <br><sub>* GRUB를 설치하고자 한다면 <a href="ftp://alpha.gnu.org/gnu/grub/" target="_blank" rel="noopener noreferrer">이곳</a>에서 다운 가능하다.<br>
  * Debian 을 사용하는 경우라면 <code># apt-get install grub</code> 의 명령어만 입력하면 된다.
  </sub>
</p>
<h3>Kernel</h3>
<p>
  OS 의 핵심이 되는 부분. <br>
  가상 메모리, 하드웨어 입출력 자원관리, 시스템 동작, 보안등을 제어해준다. <br><br>
  다음 작업으로써는 리눅스 커널과 initramfs<small>(initial RAM-based file system)</small> 가 메모리에 적재된다. GRUB 부트로더가 Kernel의 이미지를 읽어서 부팅시킨다. 리눅스 커널은 bzImage<small> (Big Zimage)</small> 의 형태를 띄고 있다. 이 이미지는 커널이 컴파일 되는 동안 생성 된다. 관련 명령어는 <code>make bzImage</code> 이다. bzImage는 부트섹션, 셋업코드, 커널이미지로 구성되어 있다. 셋업코드는 하드웨어 장치를 해당 리눅스 커널에 맞게 초기화 작업을 진행한다. <code>setup()</code> 에 관한 작업 내용은 아래와 같다. <br>
  <ul>
    <li>키보드 반복 간격과 속도의 설정</li>
    <li>VGA 초기화</li>
    <li>디스크 컨트롤러 초기화</li>
    <li>PS/2 장치 검사</li>
    <li>APM<small> (Advanced Power Management) </small>과 EDD<small> (Enhanced Disk Drive) </small>의 BIOS 지원 여부 검사</li>
    <li>FPU<small> (Floating Point Unit) </small> 초기화 (FPU가 존재할 경우에만)</li>
    <li>PIC<small> (Programmable Interrupt Controllers) </small> 를 다시 프로그래밍 한 후 모든 인터럽트 마스크</li>
    <li>...etc</li>
  </ul>
</p>
<p>
  이 후 <code>strtup_32()</code> 에 해당되는 작업이 시작된다. 레지스터와 임시 스택을 초기화 시켜주는 작업이 이루어진다. 상기 두 명령어에 해당하는 작업이 끝나면 커널이 실행된다. 작업 명령어는 <code>start_kernel</code> 이다.<br>
  <sub>* 커널의 동작에 관해 더 자세히 알고자 한다면 <a href="https://0xax.gitbooks.io/linux-insides/Booting/linux-bootstrap-2.html" target="_blank" rel="noopener noreferrer">여기</a>에서 세부 내용을 공부해보도록 하자</sub>
</p>
<img src="/media/bzImage.png" alt="Anatomy of bzImage" vspace="30px" width="450">
<h3>Init</h3>
<p>
  커널이 셋업이 완료된 후에 커널은 시스템 초기화 작업인 <code>/sbin/init</code> 을 수행시킨다. 이로써 리눅스 유저를 위한 환경이 준비가 된다. 그 다음은 <code>/etc/rc.d/rc.sysinit</code> 으로써 환경 경로, 스왑 시작, 파일 시스템 확인등에 관한 작업이 진행된다. 초기화에 관한 작업이 모두 수행된 후에는 마지막 스탭인 Runlevel 프로그램이 수행된다.
</p>
<img src="/media/initService.png" alt="Init" width="200">
<h3>Runlevel</h3>
<p>
  이 부분에서는 <code>/etc/rc.d/rc*.c</code> 에 관한 작업이 수행된다. 여러 가지로 분류되어 있는데 시스템을 어떤 방식으로 부팅할 것인가에 관한 것이다. Runlevel의 종류는 아래와 같다. 현재의 진행중인 runlevel에 관한 정보를 알고 싶을때 사용하는 명령어는 <code>#who -r</code>이다.
  <table>
      <tr>
        <th><center>Runlevel</center></th>
        <th><center>Mode | Directories</center></th>
        <th><center>Action</center></th>
      </tr>
      <tr>
        <td>
          <b><center>0</center></b>
        </td>
        <td>
          <center>
            <b>Shutdown</b><br>
            /etc/rc.d/rc0.d/
          </center>     
        </td>
        <td>
          <center>Shuts down system</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>1</center></b>
        </td>
        <td>
          <center><b>Single-User Mode</b><br>
            /etc/rc.d/rc1.d/
          </center>     
        </td>
        <td>
          <center>Maintenance mode</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>2</center></b>
        </td>
        <td>
          <center><b>Multi-User Mode</b><br>
            /etc/rc.d/rc2.d/  
          </center>     
        </td>
        <td>
          <center>Does not configure network interfaces</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>3</center></b>
        </td>
        <td>
          <center><b>Multi-User Mode with Networking</b><br>
            /etc/rc.d/rc3.d/
          </center>
        </td>
        <td>
          <center>Starts the system normally with all the services(Text mode interface)</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>4</center></b>
        </td>
        <td>
          <center><b>N/A</b><br>
            /etc/rc.d/rc4.d/
          </center>   
        </td>
        <td>
          <center>Not used</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>5</center></b>
        </td>
        <td>
          <center><b>X11</b><br>
            /etc/rc.d/rc5.d/
          </center>   
        </td>
        <td>
          <center>As runlevel 3 + GUI</center>
        </td>
      </tr>
      <tr>
        <td>
          <b><center>6</center></b>
        </td>
        <td>
          <center><b>Reboot</b><br>
            /etc/rc.d/rc6.d/
          </center>
        </td>
        <td>
          <center>Reboots the system</center>
        </td>
      </tr>
  </table>
</p>
<p>
  이로써 bootloader의 6가지의 스탭들을 알아보았다. 각각의 스탭별로 더 자세한 내용을 공부하고자 한다면 아래 reference에 정리해둔 링크를 참고하도록 하자. 다음 포스팅에서는 커널에 대해 자세히 알아보고 한다.
</p>
<h3>Reference</h3>
<p>
  <ul>
    <li><a href="http://www.pas.rochester.edu/~pavone/particle-www/telescopes/ComputerCommands.htm" target="_blank" rel="noopener noreferrer">Basic Linux Commands</a></li>
    <li><a href="http://www.ittc.ku.edu/~kulkarni/teaching/EECS678/projects/scheduling/materials/plka.pdf" target="_blank" rel="noopener noreferrer">Linux Kernel Architecture by. Wolfgang Mauerer</a></li>
    <li><a href="http://www.linuxlab.co.kr/docs/01-05-5.htm" target="_blank" rel="noopener noreferrer">막강한 부트로더 GRUB</a></li>
    <li><a href="https://gerardnico.com/data_storage/mbr" target="_blank" rel="noopener noreferrer">Data Storage - The Master Boot Record (MBR) </a></li>
    <li><a href="https://www.thegeekstuff.com/2011/02/linux-boot-process" target="_blank" rel="noopener noreferrer">6 Stages of Linux Boot Process (Startup Sequence)</a></li>
    <li><a href="https://hyd3.tistory.com/122?category=805746" target="_blank" rel="noopener noreferrer">[File System] Partition VS Volume</a></li>
    <li><a href="https://oracle-base.com/articles/8i/partitioned-tables-and-indexes" target="_blank" rel="noopener noreferrer">Partitioned Tables And Indexes</a></li>
    <li><a href="https://en.wikipedia.org/wiki/Linux_kernel" target="_blank" rel="noopener noreferrer">Linux Kernel</a></li>
    <li><a href="https://www.youtube.com/watch?v=qIEGavnI-B4" target="_blank" rel="noopener noreferrer">Linux Boot Process : Grub, initrd, explained</a></li>
    <li><a href="https://www.sunpower-uk.com/glossary/what-is-power-good-signal/" target="_blank" rel="noopener noreferrer">Power Good Signal</a></li>
    <li><a href="http://forensic-proof.com/archives/435" target="_blank" rel="noopener noreferrer">MBR (Master Boot Record)</a></li>
    <li><a href="https://stackoverflow.com/questions/1125025/what-is-the-role-of-magic-number-in-boot-loading-in-linux" target="_blank" rel="noopener noreferrer">What is the role of Magic Number in boot loading in Linux?</a></li>
    <li><a href="https://ko.wikipedia.org/wiki/GRUB" target="_blank" rel="noopener noreferrer">GRUB</a></li>
    <li><a href="https://tldp.meulie.net/en/Kernel-HOWTO/ar01s10.html" target="_blank" rel="noopener noreferrer">Kernel Files Information</a></li>
    <li><a href="https://commons.wikimedia.org/wiki/File:Anatomy-of-bzimage.png" target="_blank" rel="noopener noreferrer">File:Anatomy-of-bzimage.png</a></li>
    <li><a href="https://lunatine.net/2015/12/18/linux-booting/" target="_blank" rel="noopener noreferrer">Linux 부팅과정 </a></li>
    <li><a href="https://access.redhat.com/documentation/ko-kr/red_hat_enterprise_linux/6/html/installation_guide/s2-boot-init-shutdown-init" target="_blank" rel="noopener noreferrer">F.2.4. /SBIN/INIT 프로그램</a></li>
    <li><a href="http://www.linuxvasanth.com/tag/runlevels/" target="_blank" rel="noopener noreferrer">What is Run Level in Linux?</a></li>  
    <!-- <li><a href="#" target="_blank" rel="noopener noreferrer">-</a></li>       -->
  </ul>
</p>