{
    "title": "Node.js v0.8 릴리즈와 API 변경이력",
    "author": "Rhio Kim",
    "date": "2012-06-26T02:18:12.022Z",
    "categories": [
        "news"
    ],
    "tags": [],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-06-26T02:18:12.022Z",
    "status": "public",
    "important": false,
    "advanced": {}
}

노드의 v0.8 의 가장 큰 목표는 크로스 플랫폼의 호환성에 있습니다. 0.6 부터 추가되었던 lib_uv 는 윈도우 지원을 위한 추상 레이어로 lib_uv 를 통해 시스템 API 를 핸들링할 수 있게 됩니다. 이번 v0.8 은 이 부분을 완벽히 처리하였습니다. 그리고 오픈 소스의 가장 중요한 에코시스템인 모듈 시스템은 노드 창시자인 라이언(@ry)에서 아이작(@issac) 에게 넘어가면서 좀더 완벽한 시스템으로 발전해왔습니다.

그중 크로스플랫폼에서 네이티브 모듈 빌드 시스템의 의존성과 복잡도를 낮추고 노드에 적합한 새로운 메타 빌드 시스템인[node-gyp](https://github.com/TooTallNate/node-gyp) 로 전환하는 대대적인 작업이 이루어졌습니다.

이와 더불어 다음 버젼에서는 기존의 [npm](http://npmjs.org) 모듈도 `npm install module` 이 아닌 `node install module` 형태로 변경하는 작업 진행중에 있습니다.  이번 릴리즈를 통해 노드는 좀더 쉽고 좀더 빠르고 좀더 넓은 플랫폼에서 기존의 솔루션들과 경쟁할 수 있게 되었습니다.

그외 노드 공식사이트에서 소개하고 있는 v0.8 의 개선사항은 다음과 같습니다.

1. 매우 큰 폭의 성능 향상되었다.
2. 크로스플랫폼에서의 높은 안정성
3. You can do stuff with file descriptors again.
4. [클러스터(cluster)](http://nodejs.org/api/cluster.html) 모듈이 좀더 나아졌다.
5. [도메인 모듈](http://nodejs.org/api/domain.html)이 추가되었다.
6. 노드 repl(Read Eval Print Loop) 이 더 나아졌다.
7. 네이티브 애드온 빌드 툴이 [Waf](http://code.google.com/p/waf/) 에서 [GYP](http://code.google.com/p/gyp/wiki/GypLanguageSpecification) 로 변경되었다.
8. 기타 수 많은 변경사항이 있다.


## 더 이상 지원하지 않는
* http.Client()
* path {exists, existsSync} 는 fs {exists, existsSync} 로 변경되었습니다.
* tty.setRawMode (mode) 는 tty.ReadStream # setRawMode() (즉 process.stdin.setRawMode() )로 변경되었습니다.
* ev_ * 및 eio_ * 함수를 직접 사용하는 것은 권장하지 않습니다. 대신 libuv 가 제공하는 함수를 사용하십시오. 
* eio_custom 에서 uv_queue_work 로 마이그레이션 방법은[wiki 페이지](https://github.com/joyent/node/wiki/How-to-migrate-from-eio_custom-to-uv_queue_work) 를 참조하십시오.


## 제거된
* waf 빌드 시스템 - node.js 은 gyp 를 사용하게 되었습니다.
    - 네이티브 모듈의 저자 경우 즉시 [node-gyp](https://github.com/TooTallNate/node-gyp) 로 마이그레이션 하십시오!
* `require ('sys')` 는 예외를 throw 합니다. `require('util')` 를 사용하십시오. "sys"는 node v0.4에서 deprecated되었습니다.
* `process.installPrefix` 삭제되었습니다. ( [#3483](https://github.com/joyent/node/pull/3483) ) `process.installPrefix` 은 v0.6에서는 항상 `undefined` 입니다.
* `node-vars` 삭제되었습니다 ( [#3483](https://github.com/joyent/node/pull/3483) ) `node-vars` 는 v0.6에서는 항상 빈 문자열을 반환했습니다.

> [Waf](http://code.google.com/p/waf/) 는 python 기반의 메타 빌드 시스템으로 노드 네이티브 모듈을 빌드하기 위해서 사용되어 왔다.

## 변경된
* process
    - process.stdin.on('keypress') 내부 API에 기본적으로 생성되지 않습니다.
    - process.stdin.pipe(dest) 가 자동으로 process.stdin.resume() 를 호출합니다.

* cluster
    - `cluster.fork()` 은 더 이상 `child_process.fork()` 가 반환한 개체를 반환하지 않습니다. 그것이 필요하면 `cluster.fork().process` 를 사용하십시오.
    - cluster 개체 'death' 이벤트는 'exit' 로 변경되었습니다.
    - `kill()` 메서드는 `destroy()` 로 변경되었습니다.
    - `CLUSTER_WORKER_ID` 환경 변수 `CLUSTER_UNIQUE_ID` 로 변경되었습니다. 이것만 사용해야 하는 것은 아닙니다.
    - worker는 마스터와의 연결이 문제로 인해 유실되면 자신을 종료합니다.

* http
    - `http.Server` 은 CONNECT 메소드를 요구하면 'upgrade' 이벤트가 아니라 'connect' 이벤트를 생성합니다.
    - `http.ServerResponse` 는 Date: 헤더를 기본적으로 보냅니다. 이것을 막으려면 response.sendDate 을 false 로 설정합니다.
    - `http.ClientRequest` 은 CONNECT 메소드에 대한 응답을 받으면 'response' 가 아니라 'connect' 이벤트를 생성합니다.

* child_process
    - child_process.fork() 의 arguments 및 options 인자는 옵션되었습니다.
    - 자식 프로세스가 종료하면 'exit' 이벤트가 문제없이 생성됩니다. 이건 이전과는 달리 모든 표준 입출력이 닫히기까지 기다리지 않습니다.
    - 'close' 이벤트가 추가되었습니다. 그것은 자식 프로세스가 종료하고 모든 표준 입출력이 닫힐 때 생성됩니다.

* readline
    - rl.createInterface() 의 인자는 rl.createInterface(options) 의 options 의 일부가 되었습니다. 그러나 이전 rl.createInterface(input, output, completer) 스타일도 사용할 수 있습니다.

* url
    - url.parse() 는 IPv6 주소를 파싱하게 되었습니다.
    - url.parse() 는 구분 기호를 버리는 것이 아니라 이스케이프 하도록 되었습니다.
    - url.format() 는 auth 섹션을 이스케이프하게 되고 url.parse() 는 그것을 해독하게 되었습니다.

* fs
    - path.exists() 및 path.existsSync() 가 fs.exists() 및 fs.existsSync() 에 있습니다.
    - fs.symlink 의 type 인수 'junction' 를 지정할 수 있습니다 (Windows에만 해당).
    - fs.realpath 및 fs.lstat 가 Windows에서 Unix처럼 작동하도록 합니다.

* console
    - console.timeEnd 레이블이 없으면 예외를 throw하도록 합니다.

* buffer
    - SlowBuffer 는 Buffer 를 상속하게 되었습니다. 이러한 프로토타입을 변경하는 모듈은 Buffer.prototype 에 적용하는 것만으로 충분합니다.
    
## 추가된
* buffer
    - 'utf16le' 인코딩.

* child_process
    - child_process.fork() 의 `silent` 옵션 - stdout 및 stderr 를 부모 프로세스와 공유하지 않습니다.
    - child_process.fork() 한 자식 프로세스. disconnect() 하여 자식 프로세스가 성공적으로 완료하게 됩니다.
    - child_process.spawn() 의 `stdio` 옵션 - 자식 프로세스의 표준 입출력 (파일 디스크립터)를 구성할 수 있습니다.
    - child_process.spawn() 의 `detached` 옵션 - 자식 프로세스 그룹 리더합니다 ( [문서](http://nodejs.org/api/child_process.html#child_process_child_process_spawn_command_args_options) ).
    - child.send() 는 net.Server 및 net.Socket 를 두번째 인자로 보낼 수 있습니다.

* cluster
    - 'fork', 'online', 'listening' 및 'setup' 이벤트.
    - Worker 개체가 (마스터에서는) cluster.workers 또는 (작업자에서는) cluster.worker 로 제공되게 되었습니다.
    - cluster.fork() 에 env 옵션 인자가 추가되었습니다.
    - cluster.setupMaster() 및 cluster.settings.
    - cluster.disconnect() 및 worker.disconnect().
    - 내부적으로 사용되었다 workerID 이 worker.id 로 추가되었습니다.
    - worker.suicide 플래그가 설정되어 있으면, 작업자가 끊기거나 종료하거나 하면 의도하지 않은 종료로 보고됩니다.

* crypto
    - crypto.getDiffieHellman()
    - cipher.setAutoPadding() 및 decipher.setAutoPadding().
    - crypto.createCredentials() 의 ciphers 옵션.

* domain
    - [http://nodejs.org/api/domain.html](http://nodejs.org/api/domain.html)]를 참조하십시오.

* fs
    - fs.appendFile() 및 fs.appendFileSync().
    - wx, wx+, ax 및 ax+ 모드가 fs.open() 및 fs.openSync() 에 추가되었습니다.

* http
    - server.close() 옵션 인자로 콜백 함수가 추가되었습니다.
    - http.ServerResponse 의 sendDate 속성
    - http.request() 및 http.get() 는 url.parse() 에 의해 해석되는 URL을 인자로 받을 수 있게 되었습니다.

* https
    - https.request() 및 https.get() 에 ciphers 및 rejectUnauthorized 옵션이 추가되었습니다.

* net
    - net.connect(options [connectionListener).
    - server.close() 옵션 인수로 콜백 함수가 추가되었습니다.
    - 모든 파일 기술자를 수신하기 위한 server.listen({fd : someNumber}).

* process
    - process.abort()
    - process.hrtime() 나노(nano)초까지 지원하는 타이머.

* querystring
    - querystring.parse(str, sep] [eq], [options]).

* stream
    - setEncoding() 에 'utf16le' 및 'ucs2' 인코딩을 지정할 수 있습니다.

* tls
    - [세션 협상 공격을 막기](http://nodejs.org/api/tls.html#tls_client_initiated_renegotiation_attack_mitigation) 위한 tls.CLIENT_RENEG_LIMIT 및 tls.CLIENT_RENEG_WINDOW.
    - tls.connect(options [secureConnectionListener).
    - tls.connect() 의 ciphers , rejectUnauthorized 및 socket 옵션.
    - cleartextStream.getCipher() 는 공개 API가 되고 문서화되었습니다.

* zlib
    - dictionary 옵션.