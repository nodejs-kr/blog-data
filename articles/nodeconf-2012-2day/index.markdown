{
    "title": "NodeConf 2012 2 Day 요약",
    "author": "Rhio Kim",
    "date": "2012-07-06T01:50:23.227Z",
    "categories": [],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-07-06T01:50:23.227Z",
    "status": "public",
    "important": true,
    "advanced": {}
}

리오: "아직 공유되지 않는 발표자료가 있어 정리되지 않는 부분도 있습니다.
공유되는 데로 업데이트할 예정입니다."

## DTrace, Node.js, and Flame Graphs
* 발표자 : [Dave Pacheco](https://twitter.com/#!/dapsays)
* 발표자료 : [PDF](http://dtrace.org/blogs/dap/files/2012/07/nodeconf.pdf)

Dave Pacheco 는 Joyent 사의 소프트웨어 엔지니어로 있으며 최근까지 프로덕션 레벨의 노드를 위한 런타임 프로파일링과 postmortem 디버깅 도구를 구축하였고 노드의 모듈 의존성을 해결하기 위한 shrinkwrap 패키지 관리 구조를 만들었습니다.

이 발표에서는 DTrace 를 이용한 프로덕션 레벨의 노드 프로파일링에 대해 이야기를 하고 있습니다.  이 발표는 지난 4월에 블로그에 작성한 [노드 프로파일링의 내용](http://dtrace.org/blogs/dap/2012/04/25/profiling-node-js/)을 자세히 소개하고 있습니다.

>[DTrace(Dynamic Trace : 동적 추적)](http://en.wikipedia.org/wiki/DTrace)은 썬 마이크로 시스템즈가 개발한 솔라리스 100 및 OpenSolaris, Mac OS X, FreeBSD 에 탑재된 로우레벨 단에서의 시스템 정보를 추적하는 기능입니다. 또한 프로세스내에서 특정 함수가 호출되면서 전달되는 인수와 그에 대한 로그, 특정 파일에 액세스 하는 프로세스의 목록과 같은 보다 세밀한 정보를 추적할 수 있습니다. 노드에서는 Dtrace 를 사용하여 노드 프로세스의 메모리 사용량, CPU 타임, 파일시스템, 네트워크 리소스등의 정보를 수집하고 콜 스택의 트레이싱을 완벽에 가깝게 분석할 수 있는 유용한 도구이다.

## Fast Binary Stream Parsing
* 발표자 : [Felix Geisendörfer](http://twitter.com/felixge)
* 발표자료 : 

Felix 는 transloadit.com 의 공동 설립자이고 노드 코어 커미터입니다. 그외 [Felix's Node.js Guide](http://nodeguide.com/index.html) 로도 잘 알려져 있습니다.

## Memory Leaks. So What?
* 발표자 : [Jed Parsons](https://twitter.com/#!/drainmice)
* 발표자료 : [Web](http://jedp.github.com/node-memwatch-demo/)

Jed Parsons 는 노드계에서는 잘 알려지지 않았는데 이번 컨퍼런스에서 메모리 릭 디텍터와 힙 메모리 비교할 수 있는 [모듈](https://github.com/lloyd/node-memwatch)을 통해 메모리 누수를 파악하고 해결하기 위한 방법을 소개합니다.

리오: '프리젠테이션 정말 개발자스럽네요.'

## Node Streams
* 발표자 : [Marco Rogers](https://twitter.com/#!/polotek)
* 발표자료 : [Github](https://github.com/polotek/nodeconf-2012-streams-talk)

Marco Rogers 는 야머 자바스크립트 엔지니어로 노드에서 쉘 스크립트를 통한 I/O 조작을 손쉽게 하기 위한 [procstreams](https://github.com/polotek/procstreams) 모듈과 노드를 위한 [xml](https://github.com/polotek/libxmljs) 라이브러리 바인딩 모듈 개발자입니다. 

이 발표에서는 Collector, LogStream, FileLogStream, GZipStream 등의 예제를 통해 노드의 스트림의 특징과 효율적인 사용에 대해서 다루고 있습니다. 

## Porting Node
* 발표자 : [Tim Caswell](http://twitter.com/creationix)
* 발표자료 : [Github](https://github.com/creationix/nodeconf2012)

Tim Caswell 은 howtonode.org 운영자이며 NVM(node version manager) 와 step 이라는 control flow 모듈을 개발한 노드계의 슈퍼 개발자입니다. 첫째날 libuv 에 대해 발표한 bert belder 와 같이 Cloud9 IDE 엔지니어입니다.

최근 노드를 루아(Lua) 로 포팅하면서 얻은 경험을 공유하고 있으며 Github 에 그 내용을 공유하고 있습니다. 노드가 새로운 프로그래밍으로 포딩되는 것은 노드가 갖는 기술적인 아키텍쳐와 특징이 앞으로 중요하기 때문이라고 예측해 볼 수 있습니다.

## Streams at Scale
* 발표자 : [Matt Ranney](http://twitter.com/mranney)
* 발표자료 :

Matt 는 Voxer CTO 이며 노드 초창기에 HTTP 구현에 커미터로 활동하였습니다.  뿐만아니라 패킷 캡쳐 라이브러리인 pcap 을 노드로 바인딩한 [node_pcap](https://github.com/mranney/node_pcap) 모듈과 redis 클라이언트인 [node_redis](https://github.com/mranney/node_redis) 모듈도 개발하였다.

## You've got a memory leak
* 발표자 : [Danny Coates](http://twitter.com/antiserf)
* 발표자료 :

Danny 는 Voxer 의 엔지니어로 v8 과 WebInspector 를 기반한 노드 디버깅 툴인 [node-inspector](https://github.com/dannycoates/node-inspector) 개발자입니다. 

이번 발표에서는 노드의 메모리와 CPU 프로파일링을 통해 메모리릭을 효율적으로 대응하기 위한 노하우에 대해서 다루고 있습니다.

#### 함께보세요.
* http://howtonode.org/debugging-with-node-inspector

## JavaScript Arduino Programming
* 발표자 : [Rick Waldron](http://)
* 발표자료 : [Web](https://dl.dropbox.com/u/3531958/nodeconf/index.html#/)]

Rick Waldron 는 자바스크립트 에반젤리스트로 bocoup.com 에서 근무하고 있습니다. 최근 노드를 이용한 Ardunio 프로젝트들에 영감을 얻어 노드와 가속계, 버튼, LED, 조이스틱, 모터, 광센서, 조사각 센서, 위치제어 등을 조합해 로봇 [johnny-five](http://www.johnny-five.com/) 제어를 시연하였습니다.

## Node and SPI
* 발표자 : [@russellhay](http://twitter.com/russellhay)]
* 발표자료 : [PDF](https://www.dropbox.com/s/ff2k39ul5bs29e2/Node%20and%20SPI%20%28nodeconf2012%29.pdf)

Russell Hay 는 소프트웨어 메니저와 테스트 엔지니어링 전문가로 Tableau Software 에 근무하고 있습니다. 노드의 serialport 모듈에 영감을 얻어 모토로라에 의해 개발된 전이중(full duplex) 통신이 가능한 동기 통신 규격인 [직렬 주변기기 인터페이스 버스(Serial Peripheral Interface Bus)](http://ko.wikipedia.org/wiki/%EC%A7%81%EB%A0%AC_%EC%A3%BC%EB%B3%80%EA%B8%B0%EA%B8%B0_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4_%EB%B2%84%EC%8A%A4)를 노드로 구현하였습니다. node-spi 모듈은 두개의 주변 장치간에 직렬 통신으로 테이터를 교환할 수 있게 해준다.

이 발표에서는 모듈을 구현하기 위한 기술과 모듈의 API, 로드맵에 대해서 소개하고 있습니다.

SPI Bus 를 이용해 컨트롤할 수 있는 장치들에는 다음과 같은 것들이 있습니다.

* EEPROM
* I/O Extenders
* Motor Controllers
* LED Drivers
* ADC
* Sensors of all kinds
* Voice Record and Playback
* DSP
* Touchscreens

## Node [point] JS & Black Box Prototyping
* 발표자 : [Emily Rose](http://twitter.com/nexxylove)
* 발표자료 : [Google Doc](https://docs.google.com/presentation/d/1m1MiyNffoqeYQMLrtqnY990kJdfaPKhtyEXh5MQ6rC0/edit?pli=1#slide=id.g14c70e36_0_0)

이 발표에서는 노드를 이용한 하드웨어 컨트롤을 위한 마이크로 컨트롤러의 구조, 스케치, 트리거링에 대한 이야기를 다루고 있습니다. 이미 국외에서는 제품화하여 판매할 수준의 제품들도 몇몇 있습니다. 국내에서도 몇몇 개발자들에 의해서 노드를 이용한 아두이노 토이 프로젝트들이 공개되어 있습니다.

* [데모소스](https://github.com/nexxy/orobos-vine)

## tmpad
발표자 : [Elijah Insua](http://twitter.com/tmpvar)
발표자료 : [Web](http://tmpvar.com/nodeconf-2012/assets/fallback/index.html)

이 발표에서는 하드웨어 세션으로 노드와 아두이노를 이용해 MIDI 플레이를 위한 전자 악기의 일종인 tmpad 를 제작한 전 과정에 대해서 소개합니다.  개인적으로 제작 과정중 터치의 민감도를 적외선(IR) 터치스크린으로 처리한 것이 아이디어인 것 같다는 생각을 합니다.

그냥 압력 센서를 사용했다면 눌러서는 소리의 강도를 표현하기 어려워 단조로운 음밖에는 표현 못할꺼라 생각했지만 적외선 센서를 이용함으로 누르는 강도와 표면적에 따라서 음을 자유자재로 표현할 수 있다는 것은 괜찮은 아이디어네요.

아무튼 노드와 아두이노는 재미있고 아이디어 넘쳐나게 하는 녀석들입니다. 물론 재미요소 말고도 소프트웨어 분야 개발자들도 큰 가치를 만들 수 있게 해주죠.

![image](http://www.tmpvar.com/project/tmpad/static/img/revision4-500.jpg) 

#### 함께보세요.
* [http://www.tmpvar.com/project/tmpad/](http://www.tmpvar.com/project/tmpad/)

## References
* http://lanyrd.com/2012/nodeconf/
* http://www.davetech.com/blog/
* http://jeditoolkit.com/2012/07/05/nodeconf-2012.html#post
* https://gist.github.com/3048132

>NodeConf 2012 다녀온 #octoberskyjs 분들이 랩업 세미나를 한다고 하니 기대해봐야겠네요.


