{
    "title": "Top 10  Node Dependency modules",
    "author": "Rhio Kim",
    "date": "2012-06-27T02:49:19.276Z",
    "categories": [
        "module"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-06-27T02:49:19.276Z",
    "status": "public",
    "important": false,
    "advanced": {}
}

노드의 플랫폼이 성장하는데 큰 영향을 준 NPM 은 노드는 짧은 기간(약 2년 6개월) 동안 많은 개발자들로 하여금 엄청난 모듈들을 개발하고 이를 오픈 소스 개발자들과 다시 나눌 수 있게 하였습니다.  이 글을 작성하는 시점에서 노드의 모듈은 114,000 개가 등록되어 있습니다.  오픈 소스 프로젝트에서 이러한 에코시스템은 굉장히 큰 역할을 하는데요.

이 모듈들 중에 가장 높은 의존성을 갖은 탑 모듈들을 소개합니다.

(아래 모듈 의존성 정보는 글을 작성하는 시점을 기준으로 하기 때문에 언제든지 변할 수 있습니다.  정확한 정보는 [http://search.npmjs.org/#/_browse/deps](http://search.npmjs.org/#/_browse/deps) 에서 확인하세요.)

### underscore
* 의존성 : 1035
* 사이트 :  [http://documentcloud.github.com/underscore/](http://documentcloud.github.com/underscore/)
* 소개 : underscore 는 자바스크립트 MVC 프레임웍으로 잘 알려진 백본(backbone.js) 의 코어 라이브러리입니다. 객체 지향 자바스크립트를 위한 핵심중의 핵심만을 잘 추려 구현되어 노드에서 뿐만아니라 클라이언트측 자바스크립트 라이브러리로도 굉장히 잘 알려져 있습니다.  

### coffee-script
* 의존성 : 669
* 사이트 : [http://coffeescript.org/](http://coffeescript.org/)
* 소개 : 커피스크립트는 차세대 자바스크립트에 가장 큰 영향을 준 트랜스 컴파일 언어로 자바스크립트에서 루비 표현식을 사용할 수 있도록 해주는 스크립트 언어입니다.  이 언어는 특히 서버측 자바스크립트인 노드가 이슈화되면서 서버측 언어인 루비 개발자들에 의해서 큰 학습 요소없이 노드 플랫폼을 이용할 수 있게되면서 크게 인기를 끌면서 세계적으로 이슈가 되었고 노드 모듈도 루비 개발자들에 의해서 많들어 지고 있는 모듈이 그만큼 많다는 의미도 찾아 볼 수 있습니다.

### request586
* 의존성 : 586
* 사이트 : [https://github.com/mikeal/request](https://github.com/mikeal/request)
* 소개 : nodeconf 컨퍼런스를 만든 mekeal 에 의해서 만들어진 심플한 HTTP 요청 모듈로 브라우저에서 특정 URL 로 요청하듯이 HTTP 요청을 자유자재로 조작하여 만들 수 있는 웹 애플리케이션 구축 시 필수적이며 유용한 모듈입니다. 예를 들어 oAuth 인증이 필요한 기능에서도 request 모듈을 통해 브라우저에서 oAuth 인증 절차를 손쉽게 흉내낼 수 있게 됩니다.( 근데 high 클래스 oAuth 인증 모듈도 이미 많이 있습니다. )

### async
* 의존성 : 558
* 사이트 : [https://github.com/caolan/async/](https://github.com/caolan/async/)
* 소개 : 이 모듈은 그간 서버에서는 대부분의 절차적 프로그래밍이 주를 이뤘으나 자바스크립트의 비절차적인 비동기 이벤트 모델의 특징이 노드와 함께 서버로 넘어오면서 많은 이슈와 논의가 있었습니다.  이 이슈를 해소하기 위한 모듈입니다. 

### express
* 의존성 : 518
* 사이트 : [http://expressjs.com/](http://expressjs.com/)
* 소개 : 이것은 모듈이라고 하기보다 프레임워크입니다. 웹 애플리케이션 구축을 위한 high 클래스 API 들을 제공함으로써 이름에 걸맞게 빠른 웹 애플리케이션 구축에 필수적인 요소라 할 수 있습니다. express.js 는 Ruby 의 [sinatra](http://www.sinatrarb.com/) 프레임워크의 영향을 받아 그 구조와 특징이 매우 유사합니다.

### optimist
* 의존성 : 494
* 사이트 : [https://github.com/substack/node-optimist](https://github.com/substack/node-optimist)
* 소개 : 노드는 서버측에서 파이썬, 루비, 펄 등과 같이 CLI(Command Line Interface) 를 제공하여 쉘 스크립트로도 사용됩니다.  옵티미스트는 콘솔에서 수행되는 명령행 옵션을 코드에서 손쉽게 접근할 수 있도록 파싱해주는 유용한 모듈입니다. (예를 들어 `$ node_script.js -x 10 -y 15` 라면 `node_script.js` 내부에서는 `{ x: 10, y: 15 }` 형태로 손쉽게 접근할 수 있게 됩니다.) 

### colors
* 의존성 : 351
* 사이트 : [https://github.com/Marak/colors.js](https://github.com/Marak/colors.js)
* 소개 : 이 모듈은 옵티미스트와 동일하게 콘솔상에 처리를 위한 유틸성 모듈로 출력되는 텍스트의 색상을 손쉽게 설정할 수 있도록 해줍니다.

### connect
* 의존성 : 321
* 사이트 : [https://github.com/senchalabs/connect](https://github.com/senchalabs/connect)
* 소개 : 이 모듈은 Sencha Lab 에서 개발한 HTTP 를 확장한 서버 프레임워크를 입니다.  노드 서버를 구현하기 위한 20 여개의 미들웨어(로깅, 세션, 쿠키, 멀티파트, 압축, 가상호스트, 서브도메인 등)가 탑재되어 있습니다. 이 모듈은 express.js 에서도 기본 모듈로 사용되고 있기 때문에 실상 express.js 가 갖은 의존성 만큼 connect 모듈의 의존성도 높다고 할 수 있습니다.  만약 HTTP 서버의 동작 원리를 이해하고 싶다면 이 모듈을 분석해보는 것도 좋습니다. 

### commander
* 의존성 : 315
* 사이트 : [https://github.com/visionmedia/commander.js](https://github.com/visionmedia/commander.js)
* 소개 : 이 모듈은 optimist 와 동일한 역할을 하는 모듈로 노드계의 슈퍼 커미터인 visionmedia 의 [TJ Holowaychuk](http://tjholowaychuk.com/) 가 루비의 [commander](https://github.com/visionmedia/commander)에 를 노드 버젼으로 포팅한 것입니다.

### uglify-js
* 의존성 : 304
* 사이트 : [https://github.com/mishoo/UglifyJS/](https://github.com/mishoo/UglifyJS/)]
* 소개 : 본래 uglify-js 는 커뮤니티에 의해 클라이언트 측 자바스크립트 압축을 위한 도구로 만들어진 라이브러리입니다. 이 모듈은 단순히 압축뿐만 아니라 압축된 자바스크립트를 보기 좋게 출력하기 위한 용도와 AST(Abstract Syntax tree) 분석을 위한 도구로도 활용됩니다.

## 요약
의존성 탑 모듈들을 살펴보면 참 재미있는 사실을 발견할 수 있습니다. (노드에 관심있는 개발자만 재미있을 수도 있음)

1위를 하고 있는 underscore 모듈은 프론트 앤드를 위한 모듈입니다. 즉 브라우저에서 UI 개발에서 사용되던 prototype.js, jquery, extjs core 들과 같은 것입니다. 그런데 서버에서 인기가 만만치 않습니다.  2위를 차지한 모듈은 자바스크립트라고 하기보다 루비에 가깝다고 해야 어울리는 녀석입니다.  3위를 차지한 모듈은 Ajax 에 의존해오던 자바스크립트가 HTTP 프로토콜을 이용해 저레벨 요청을 제어할 수 있게 해줍니다. 4위를 차지한 async 모듈은 자바스크립트의 특징 중 비동기 절차를 절차 지향으로 변환해주는 녀석입니다. 마지막 5위를 차지한 express.js 는 서버 프레임워크로 웹 서비스를 구축하는데 동일한 언어로 동형의 프로그래밍(Isomorphic Programming) 이 가능하도록 하였습니다.

이런 모듈의 아이디어를 보면 서버측의 사상은 물론이고 브라우저 영역의 기술과 아이디어를 그대로 활용할 수 있기 때문에 다른 서버측 언어들에 비해 톡톡 튀는 아이디어가 많을 수 밖에 없습니다.

## top 11~20
이하 모듈도 의존성 100 이상의 모듈들로 그 인기와 사용성이 높기 때문에 시간이 된다면 함께 살펴보면 좋습니다.

* socket.io : 웹 소켓 모듈
* redis : redis 클라이언트 모듈
* jade : 템플릿 엔진 모듈
* mime : mime 타입 모듈
* mkdirp : mkdir 확장 모듈
* jsdom : 서버측 DOM 모듈
* node-uuid : 유니크 아이디 생성 모듈
* mongodb : mongoDB 클라이언트 모듈
* stylus : 다이나믹 스타일시트 언어 파싱 모듈
* pkginfo : 노드 모듈 정보를 확인하기 위한 모듈
* ejs : 템플릿 엔진 모듈
* less : 다이나믹 스타일시트 언어 파싱 모듈
* winston : 비동기 로깅 모듈
* mongoose : mongoDB 클라이언트 모듈
* xml2js : XML/JSON 변환 모듈