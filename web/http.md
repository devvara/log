# HTTP(Hypertext Transfer Protocol)

웹에서 데이터를 주고받는 데 사용되는 응용 계층 통신 프로토콜이다. 클라이언트와 서버 간의 요청과 응답을 처리하는 방식으로 웹 페이지 뿐만 아니라 파일, 데이터, 비디오 등 다양한 자원을 전송하는 데 사용된다. HTTP는 상태가 없는 프로토콜로, 서버가 두 요청 사이에 어떠한 데이터(상태)도 유지하지 않는다.

## HTTP 구조

HTTP는 요청-응답 프로토콜이다. 클라이언트가 웹 브라우저를 통해 특정 웹 서버에 접속할 때, 브라우저는 서버에 HTTP 요청을 보내고 서버는 이에 대한 응답을 반환한다. 

교환 정보는 크게 세부분으로 나뉜다.

1. Request Line(요청): HTTP 메서드, URI(Uniform Resource Identifier), HTTP 버전 등이 포함
2. Headers(헤더): 요청과 응답에 대한 메타데이터를 포함한다. 사용자의 브라우저, 요청된 페이지의 호스트 이름, 콘텐츠 유형 등
3. Body(본문): 실제로 전송되는 데이터 (* 모든 요청과 응답이 본문을 가지는 것은 아님, 예 GET)

## HTTP 메서드

HTTP 메서드는 서버에 어떤 동작을 수행할지를 나타내는 데 사용한다.

- GET: 서버에서 자원을 조회하는 데 사용, 데이터를 가져오기만 하고 데이터를 변경하지 않는다. 
- POST: 서버에 데이터를 생성하도록 요청
- PUT: 서버에 있는 자원을 대체하거나 업데이트
- DELETE: 서버의 지정된 자원을 삭제
- HEAD: GET 요청과 비슷하지만, 본문을 반환하지 않고 헤더 정보만 가져온다.
- OPTIONS: 타겟 리소스에 대해 통신 옵션을 설명하는 데 사용

## HTTP 메서드 멱등성(Idempotence)

HTTP 메서드의 멱등성(Idempotence)은 같은 요청을 여러번 보내도 결과가 동일하다는 의미이다. 메서드가 서버의 상태를 어떻게 변경하느냐에 따른다.

HTTP 메서드 중 멱등성으로 간주되는 것

- GET: 서버의 데이터를 가져오는 데 사용되며 데이터를 변경하지 않아 여러번 수행해도 서버의 상태는 변경되지 않는다.
- HEAD: GET과 유사, 서버의 상태를 변경하지 않는다.
- PUT: 서버에 데이터를 업로드해 기존 자원을 대체한다. 같은 데이터를 여러번 PUT 요청을 하면 첫 번째 요청 이후에는 서버의 상태가 계속 같기 때문에 멱등하다.
- DELETE: 특정 리소스를 삭제한다. 첫 번째 DELETE 요청이 성공한 후 이후 요청에는 변화를 일으키지 않기 때문에 멱등핟. 

## HTTP 상태

서버는 클라이언트의 성공여부를 상태코드로 알려준다.

- 200(OK): 요청이 성공적으로 처리
- 301(Moved Permanently): 요청한 리소스가 영구적으로 이동
- 404(Not Found): 서버가 요청한 리소스를 찾을 수 없음
- 500(Internal Server Error): 서버 내부에서 오류 발생

## HTTP 버전

- HTTP/0.9
  출시: 1991년
  특징: 
  - 단순한 텍스트 기반 프로토콜
  - 오직 GET 요청만 지원, HTML 같은 하이퍼텍스트 문서만 요청하고 전송 가능
  - 요청과 응답 모두 헤더 없이 시작행만을 가지며, 서버는 문서 전송 후 연결을 바로 종료

- HTTP/1.0
  출시: 1996년
  특징:
  - 헤더 정보를 포함하여 메타 데이터 전송을 지원
  - GET, POST, HEAD 같은 새로운 메서드 도입
  - 상태 코드를 통한 에러 응답 처리 기능 추가
  - 요청과 응답 후 연결이 종료되는 '비연결성', 매 요청마다 새로운 연결이 필요(단점)

- HTTP/1.1
  출시: 1997년
  특징:
  - 가장 널리 사용되는 버전
  - 지속 연결(persistent connections)을 지원하여 연결 overhead를 줄임
  - 파이프라이닝(pipelining) 기능이 추가됨 여러 요청과 응답을 동시에 처리할 수 있음
  - 캐싱 정책, 호스트 이름을 요청 헤더에 포함하는 등 더욱 세밀한 기능이 추가
  - 청크 전송 인코딩(데이터를 여러 부분으로 나누어 순차적으로 전송), 컨텐츠 협상(클라이언트와 서버간의 가장 적합한 리소스 버전 결정) 같은 기능이 추가되어 유연한 데이터 전송 가능

- HTTP/2
  출시: 2015년
  특징:
  - HTTP/1.1 기능 개선, 성능 향상에 중점을 두고 설계
  - 하나의 연결에서 여러 요청과 응답을 동시에 병렬 처리할 수 있는 멀티플렉싱을 지원
  - 서버 푸시 기능을 통해 클라이언트의 요청을 기다리지 않고 서버에서 능동적으로 리소스를 보낼 수 있다.
  - 헤더 압축을 통해 프로토콜 오버 헤드를 줄임
  - 보안을 강화하기 위해 HTTPS를 표준으로 사용하는 경향이 강화되었다.

- HTTP/3
  출시: 개발중
  특징:
  - UDP 기반 QUIC 프로토콜을 사용하여 TCP의 연결 지연 문제 해결
  - 더 나은 멀티플렉싱과 콘텐츠 복구 기능을 제공