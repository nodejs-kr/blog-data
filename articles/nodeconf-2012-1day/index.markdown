{
    "title": "NodeConf 2012 1 Day 요약",
    "author": "Rhio Kim",
    "date": "2012-07-03T05:52:35.762Z",
    "categories": [
        "node.js"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-07-03T05:52:35.762Z",
    "status": "public",
    "important": true,
    "advanced": {}
}

리오: "아직 공유되지 않는 발표자료가 있어 정리되지 않는 부분도 있습니다.
공유되는 데로 업데이트할 예정입니다.

## Inﬂuences of Node
* 발표자 : [Ryan Dahl](http://twitter.com/ryah)
* 발표자료 : [PDF](http://tinyclouds.org/nodeconf2012.pdf)

Ryan Dahl 는 노드 창시자이고 현재 joyent 에서 다른 일을 진행하며 노드에 계속 기여하고 있습니다. 
 
이번 발표에서는 노드의 탄생 배경에 대해서 매우 자세히 설명해주고 있습니다. PT 자료를 보면 라이언은 웹 사이트 구축을 위해 꾀 오랜 시간동안 다양한 시도와 연구를 해온 흔적들을 모두 확인할 수 있습니다.
 
노드 탄생은 2004년 11월 10일 뉴욕의 로체스터에서 [토폴로지](http://ko.wikipedia.org/wiki/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC_%ED%86%A0%ED%8F%B4%EB%A1%9C%EC%A7%80) 를 연구하며 Ph.D로 있던 라이언이 졸업 학점을 우수하게 받고나서의 공허감(PQS: Post-Quals Slump)을 느끼고 있던 끝에 클라우드를 통해 노드(토폴로지에서 말하는 노드)간에 통신할 수 있는 방법을 밝혀내기 위해 시작하게 되었습니다. 이 때부터 루비를 배우기 시작했고 새로운 HTML 템플릿 엔진도 개발했다고 합니다.
 
그러던 중 Ruby on Rails 와 PHP 를 주로 하는 Engine Yard 라는 회사와 HAProxy 와 유사한 Nginx 로드 밸런서를 구축하기 위해 풀 타임으로 일을하게 되고 개인의 연구 결과를 증명하기 위해 시작된 결과가 노드가 탄생하게 되었습니다.
 
그렇게 연구의 결과를 증명하기 위해 레일즈로 구현체를 만들던 중 레일즈의 한계를 느껴 새로운 시도를 하게 되었고 결국 자바스크립트의 싱글 쓰레드 방식으로 진행하게 되었습니다.

> 2009-01-26. Cologne. The result is what every system admin knows intuitively: Rails gets worse over time if loaded down with connections. The culprit is most likely MRI’s crappy thread implementation. While Rails serves 1 request, 29 threads are there sitting idle sucking up resources. [livejournal](http://four.livejournal.com/955817.html)

노드는 아래의 기술에 많은 영향을 받았다고 합니다. 

> CouchDB, Ebb, Flow, FUSE, libebb, libeio, libev, libircclient, Merb, Mongrel, NGINX, nginx-ey-balancer, Ragel, Ruby on Rails, SqueezeBox, timber lang, XUpload

>>리오: 다소 요약이 부실하지만 발표자료에서 디테일하게 확인하세요.

## Oh the places you'll node
* 발표자 : [Matthew Podwysocki](https://twitter.com/#!/mattpodwysocki)
* 발표자료 : [SlideShare](http://www.slideshare.net/mattpodwysocki/oh-the-places-youll-node-13520581)

Matthew Podwysocki 는 노드의 윈도우 지원을 위한 MS 엔지니어입니다. 노드 0.6 버젼부터 꾸준히 기술 지원끝에 0.8 버젼부터는 안정화된 버젼으로 출시되었습니다. 뿐만아니라 노드 플랫폼을 감싼 MS 의 다양한 프로덕트(Windows Azure, WebMatrix2, sqlserver driver)에 대한 소개와 노트 커뮤니티를 위한 기술에 대해 소개합니다.

## Real time at larger scale
* 발표자 : [Mikito Takada](http://twitter.com/mikitotakada)
* 발표자료 : [Web](http://mixu.net/slides/nodeconf/)

Mikito Takada 는 [Zendesk.com](http://www.zendesk.com/product/key-features) 의 엔지니어로 [http://book.mixu.net/](http://book.mixu.net/) 의 저자이고 Socket.io/Engin.io 공헌자로 잘 알려져 있습니다.

이 발표에서는 Zendesk 를 노드 기반으로 구축하면서 얻은 노하우에 대해서 깊이 있게 다루고 있습니다. Zendesk 는 HAProxy/f5 + Socket.io + redis 를 기반으로 구축되었고 올해 Engine.io 로 변경하였다고 합니다.  

### 인프라를 구축하면서 얻은 경험
* 동립적으로 확장이 용이한 프로세스. 
> 독릭접으로 응용 프로그램 수준의 기능을 추가할 수 있어야 한다. 사용하는 기술이 무엇이든 간에 서비스중에 서버측에 새로운 프로세스를 추가할 수 있어야 한다. 앱에서 어떤 기능을 구현하던 간에 구현의 세부 정보는 몰라도 될 정도의 API 를 작성해야 한다.
* 가능한한 작게 쪼개라. 
> 프로세스에서 관리 코드는 포함시키지 말고, 하나 당 하나의 일만 하도록 해라.
* Statelessness(상태없음) 는 매우 중요. 
> 세션을 피하고 각각의 노드가 독립적이고 스스로 동작할 수 있도록 유지해야 합니다. 
* Disposability. 
> 어떤 실패 처리에 우와하게 대응하고 클라이언트 충돌은 리로드로 서버의 충돌은 기존의 상태를 이용할 수 있어야 한다.
* 디버깅보다 중요한 것은 모니터링이다. 
> 웹 서비스는 굉장히 다양한 네트워크 대역폭을 갖는 유저들이 사용한다. 모든 환경에 유연하게 대응하는 것은 디버깅보다 모니터링이 더욱 중요하다.
* 간단하게 유지하라. 
> 엔드 유저는 큰 문제가 있지 않은 한 아키텍쳐에 전혀 관여하지 않는다. 한꺼번에 많은 것을 처리하려 하려는 것보다 나눠서 조금씩 변화시켜라.

(리오: 직접 들었다면 제일 지루했을 것 같은 발표이다. ^-^)

## State of node
* 발표자 : [Issac](http://twitter.com/issac)
* 발표자료 : [PDF](http://dl.dropbox.com/u/3685/presentations/nodeconf-2012/state-of-the-node.pdf)

Issac 는 NPM 을 개발한 Issac 은 현재 노드를 리드하고 있고 과거부터 현재 그리고 앞으로 노드의 변화에 대해 일목요연하게 잘 설명해주고 있습니다.  내용을 간단히 요약하자면 다음과 같습니다.

* v0.2 부터 0.8 까지의 변화
* v0.8 에 추가된 실험적인 domain 모듈에 대한 설명
* 새로운 npm 사이트 구축중
* 작년에 비해 변화된 노드 커뮤니티와 시장 변화
* v0.9 계획 그리고 v1.0 에 대한 생각(Version 은 마케팅 요소)

## Candor
 ![Candor](https://raw.github.com/indutny/candor/master/logo/logo.png)
 
* 발표자 : [Fedor Indutny](http://twitter.com/indutny)
* 발표자료 : [PDF](https://t.co/jLq2mREu)

Fedor Indutny 는 러시아 친구이고 현재 [Nodejitsu.com](http://nodejitsu.com) 에 엔지니어로 있으며 노드 커미터로도 활동하고 있습니다.

[Candor](http://indutny.github.com/candor/) 도 자바스크립트에서 영감을 얻어 CoffeeScript, JSPP, Dart 와 유사한 프로그래밍 언어입니다. 차세대 자바스크립트의 표준인 ECMA 명세를 일부 구현하였고 Candor 의 목적도 다른 언어들과 마찬가지로 모든 개발자들에게 거부감 없이 손쉽게 접근할 수 있는 프로그래밍 언어로 발전하는데 있습니다. 

## Streams are Useful When Writing Javascript Programs
* 발표자 : [Max Ogden](http://twitter.com/maxogden)
* 발표자료 : [Web](http://t.co/ZhYAin3h)

턱수염이 인상적인 Max Ogden 은 마켓 리서치 회사에서 근무하며 GeoGraphic 데이터 시각화에 관심을 갖은 개발자입니다.

![image](http://a3.twimg.com/profile_images/1507010845/Screen_Shot_2011-08-18_at_5.08.05_PM.png)

이 발표에서는 자바스크립트 프로그래밍에서 유용한 스트림에 대해서 다루고 있습니다. 일반적으로 스트림을 다루는 경우는 브라우저에서도 많습니다. Ajax, WebSocket, files, web workers, webcam, microphone, indexedDB 등. 이런 스트림을 다룰때 흐름 제어가 필요한데 브라우저에서는 높은 레벨의 API 를 제공하기 때문에 복잡한 흐름제어를 하는 경우는 없고 이벤트를 통해 결과에 대한 핸들링만 합니다.

하지만 이런 API 을 서버측 자바스크립트 노드 스타일로 제공하면 더욱더 간단합니다. Max 는 Substack 가 만든 노드의 모듈을 브라우저에서 사용할 수 있도록 하는[browserify](https://github.com/substack/node-browserify) 모듈과 같이 스트림을 다루는 HTML5 API 를 노드 스타일로 제공하도록 [domnode](https://github.com/maxogden/domnode) 모듈을 개발하였습니다.

기존에 Ajax 방식의 코드

```js
var request = new XMLHttpRequest();
var offset = 0;
request.open("GET", "http://html5zombo.com", true);
request.onreadystatechange = function() {
   if ( request.responseText.length > offset ) {
      console.log(res.responseText.slice(this.offset));
      offset = res.responseText.length;
   }
}
request.send(null);
```

domnode 방식의 코드

```js
var request = require('request');
request('http://html5zombo.com');
   .on('data', console.log);
```

>>리오: 좀더 많은 예제들은 발표 자료를 확인하세요. 

#### 함께보세요.
* [블로그](http://maxogden.com/node-streams)
* [동영상](http://www.youtube.com/watch?feature=player_embedded&v=tnXz4HigcoI#!)

## Two Years of NodeJS At Yammer
* 발표자 : [Matthew Eemisse](https://twitter.com/#!/mde)
* 발표자료 : 

Mattew Eemisse 는 현재 야머에 백엔드 엔지니어로 근무하고 있습니다. 이 발표에서는 마이크로소프트사에 12억 달러에 팔게된 야머의 성공으로 이끌게 해준 노드에 대한 내용입니다. 

### 노드는 야머에 왜 적합했을까? 
노드의 확장성은 정말 뛰어나다. 야머의 서비스 코어팀의 친구들이 말하기를 서비스를 만들다보면 기능이 추가될 수록 신속한 확장이 점점 어려워지지만 노드로 인해 그런 걱정이 필요 없었습니다.  핵심 서비스 팀원들은 개발과 배포 주기를 짧게 가져감으로 확장성에는 크게 걱정하지는 않았다고 합니다.  물론 어떤 상황에서는 구성원이 선호하는 플랫폼으로 서비스를 재 작성할 수도 있지만 우리는 그렇게 하지 않고도 아주 빠르게 구축할 수 있었다고 합니다.

### 노드는 개발이 굉장히 빠르다.
새로운 기능 추가를 빠르게 할 수 있고 서비스에 배포하고 개발하는 과정에서 사용자의 반응에 대한 통계를 봐가며 무엇을 개발해야 할지를 생각하며 즉각적으로 반응할 수 있습니다. 자바스크립트와 노드는 이런 측면에서는 정말 훌륭합니다. 

### 노드는 활기가 넘치는 에코 시스템과도 같다.

노드 커뮤니티에는 정말 멋지고 흥미롭습니다. 그리고 도움을 얻을 수 있는 사람들과 흥미로운 것들이 널려있습니다.
그리고 야머의 성공에는 노드가 있었고 코어 서비스 개발팀이 있었습니다.
Bob Remeika, Daniel Erickson, Mike Ihbe, Mikeal Rogers, Marco Rogers

## Node Knockout History
* 발표자 : [Visnu Pitiyanuvath](http://twitter.com/visnup)
* 발표자료 : [Web](http://nodeknockout.com/tell-me-a-story)

Node Knockout 행사는 노드를 이슈화하는데 많은 영향을 주었습니다. 해카톤과 유사한 행사로 정해진 48시간 동안 노드를 이용해 아이디어를 구현합니다. 2010 년부터 현재 2회 개최되었고 매우 훌륭한 작품들이 출시되었습니다. [2010](http://2010.nodeknockout.com/), [2011](http://2011.nodeknockout.com/)
이 발표에서는 Node Knockout 행사의 히스토리를 이야기하고 있습니다.

## Socket.io Background
* 발표자 : [Guillermo Rauch](https://twitter.com/#!/rauchg)
* 발표자료 : 

LearnBoot 사에서 개발한 이 라이브러리는 이미 웹 소켓과 함께 굉장히 유명한데요. 웹 소켓을 지원하지 않는 브라우저에서 웹 소켓 기능과 서버측에서 노드와 함께 소켓 서버 역할을 할 수 있는 모듈을 함께 제공하고 있습니다. 이 발표에서는 Socket.io 를 개발하게된 동기와 구현 과정에 대해 소개하고 있습니다.

## More Realtime
* 발표자 : [Daniel Shaw](http://twitter.com/dshaw)
* 발표자료 : [Web](http://dshaw.github.com/2012-07-nodeconf/#/)

Daniel Shaw 는 Voxer 플랫폼팀에서 노드 엔지니어로 근무하고 있습니다. 그는 Voxer 를  Redis 와 Socket.io 로 좀더 나은 리얼타임 웹 애플리케이션 개발을 위한 경험을 이 발표를 통해 설명하고 있습니다.
Socket.io RedisStore 는 굉장히 멋지다. 서버의 클러스트당 2만 유저를 케어할 수 있었고 단일 이벤트로 동시에 수천명의 사용자와 수천번의 배치를 처리할 수 있는 능력이 필요했고 그것을 Socket.io 와 RedisStore 로 해결하였습니다.

* [Socket.io-Announce](https://github.com/dshaw/socket.io-announce) 는 Socket.io RedisStore 와 함께 다중 채널 브로드캐스팅을 구현한 모듈입니다. 
* [Redis Monitor](https://github.com/dshaw/redis-monitor) 는 실시간으로 Redis [정보](http://redis.io/commands/info)를 모니터링하기 위한 모듈입니다.

## libuv : The Little Library That Could
* 발표자 : [bert belder](https://twitter.com/#!/piscisaureus)
* 발표자료 : [Web](http://www.2bs.nl/nodeconf2012)

[libuv](https://github.com/joyent/libuv) 는 v0.6 부터 크로스 플랫폼 지원하기 위한 추상화 레이어를 구현한 라이브러리입니다. 이 발표에서는 libuv 내부에 대한 이야기를 자세히 다루고 있습니다. 

### libuv 목적
* 동작을 추상화
* 서로 다른 Non-Blocking I/O 모델을 제공 (윈도우에 매우 중요하다)
* 임베디드의 용이함과 성능에 포커스하여 개발
* libev 와 비슷함

### libuv 주요기능
* TCP/UDP 소켓
* DNS
* 타이머와 별도의 이벤트 루프
* 파일과 파일 시스템
* 자식 프로세스
* 파이프

## Substack (Things Which Are Relevant)
* 발표자 : [James Halliday](http://twitter.com/substack)
* 발표자료 : [Web](http://substack.net/doc/nodeconf_2012/)

James Halliday 는 노드 커뮤니티의 슈퍼 개발자로 현재 각양 각색의 무수히 많은 노드 모듈을 구현한 개발자입니다. 특히 James 는 컴퓨터로 그림그리는 것을 즐겨하는데 이번 PT 에 그런 그림들의 총 집합체라고 할 수 있다. (리오: 마니아틱한 노드 닌자입니다.) 

이 발표에서는 최근 자신의 노드에 대한 몇몇 경험중 NPM 과 Streams 에 대해 공유합니다.  노드는 미래웹과 큰 거래중입니다. 기술적으로는 V8 로켓을 장착한 거북이라고 표현하며 천천히 걸어가는 거북이 같지만 NPM에 의해 노드는 수톤급 핵폭탄 역할을 할것이라고 이야기하고 있습니다.

![image](http://images.wikia.com/memoryalpha/en/images/d/d6/Coffee_replicates_then_mug.jpg) 

현재 14,000 개가 넘는 모듈이 있는데 이 모듈이 서버측뿐만 아니라 브라우저에서도 사용할 수 있게 된다면 그건 정말 어마어마한 일입니다. 이것을 해결하기 위해 Substack이 개발한 [browserify](https://github.com/substack/node-browserify) 모듈은 스타트랙의 리플리케이터와도 같은데 노드 모듈을 그대로 브라우저에서도 사용할 수 있도록 해줍니다. (리오: 물론 노드 전용 API 를 사용한다면 브라우저에서는 안되겠지만 예를 들어 이메일 유효성 체크 모듈이나 XML을 JSON 으로 변환하는 모듈등 서버와 클라이언트 구분없이 사용될 수 있게 됩니다.) 

노드에 [Streams](http://nodejs.org/api/stream.html) 은 I/O 를 분리하기 위한 진짜 멋진 방법을 제공하고 [dnode](https://github.com/substack/dnode) 모듈을 이용하면 좀더 깔끔한 코드를 작성할 수 있다고 합니다.

## 요약
첫번째 날의 내용은 역시 가벼운 내용으로 시작하였네요.  노드의 탄생 배경과 현재의 진행 상황과 발전 방향에 대해서 이해할 수 있는 것 같습니다.  그리고 이번 v0.8 에서 가장 중요한 변화인 libuv 의 기술 리포팅으로 크로스 플랫폼을 지원하기 위한 기술을 쉽게 이해할 수 있겠습니다.

그리고 시장에 뜨거운 감자로 이제 어느정도 자리매김을 해서 Zendesk 의 경험사례 공유와 야머의 12억 달러의 판매에 노드를 채택한 것이 가장 큰 성공의 요인이라고 포장을 하고 있다. 
변화하는 웹 소프트웨어 아키텍쳐를 이해하고 시장에서 노드의 방향에 대해서 짐작할 수 있었습니다.

그외에 커미터들과 모듈 개발자들의 경험사례도 실무에 꼭 필요한 요소들을 잘 설명해주고 있습니다.

## References
* https://github.com/octoberskyjs/home/blob/gh-pages/nodeconf2012_day01.md
* http://lanyrd.com/2012/nodeconf/
* http://www.davetech.com/blog/
* http://jeditoolkit.com/2012/07/05/nodeconf-2012.html#post
* https://gist.github.com/3048132

## 기타
* 노드 컨퍼런스에서 한국 음식에 반응이 좋음 (https://twitter.com/mde/status/219898392707465218)
