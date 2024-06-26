# API(Application Programming Interface)

인터페이스란 특정한 두 대상을 연결하거나 조작하기 위한 규칙과 규격을 나타냅니다. 우리가 생활에서 사용하는 콘센트, 휴대전화의 충전, 마우스, 키보드 등이 인터페이스이다.

소프트웨어 응용프로그램에서 인터페이스 역할을 하는 것을 API(Application Programming Interface)라고 합니다. API를 통해 다른 응용 프로그램, 서비스가 데이터를 주고 받는 기능을 할 수 있다.

## API 주요 특징

1. 표준화된 인터페이스: API는 개발자가 일관된 방식으로 서비스를 사용할 수 있도록 표준화된 인터페이스를 제공한다.
2. 언어 독립성: 다양한 프로그래밍 언어에서 API를 호출할 수 있어 특정 언어에 종속되지 않는다.
3. 모듈화 및 재사용성: API를 통해 기능을 모듈화하고 재사용할 수 있다. 코드의 중복을 줄이고 유지보수를 용이하게 한다.
4. 보안: API를 통해 서비스에 접근할 때 인증 및 권한 부여 매커니즘을 적용해 보안을 강화한다.

## API 종류

1. 웹 API: HTTP를 통해 웹 서버와 상호작용하는 API이다. RESTful API와 SOAP API, GraphQL API가 대표적이다.
2. 라이브러리 API: 특정 프로그래밍 언어의 라이브러리나 프레임워크를 통해 제공되는 API이다. Node.js에서 `fs` 모듈은 파일 시스템과 상호작용할 수 있는 API를 제공한다.
3. 운영 체제 API: 운영 체제가 제공하는 API로, Windows API는 Windows 운영 체제의 기능에 접근할 수 있게 해준다.
4. 하드웨어 API: 하드웨어 장치와 상호작용하는 API이다. GPU를 사용하는 그래픽 프로그래밍에서 OpenGL API를 사용할 수 있다.

## RESTful API (Representational State Transfer)

RESTful API는 웹 애플리케이션과 서버 간의 상호작용을 하기 위해 설계된 소프트웨어 아키텍처 스타일의 API로 웹 서비스를 만들 때 지키면 좋은 가이드 라인을 가지고 있다.

REST를 잘 지키기 위한 핵심 원칙

1. Client-Server Architecture
   클라이언트와 서버는 각각 독립적으로 운영되며 클라이언트는 사용자 인터페이스와 사용자 경험에 집중하고, 서버는 데이터 저장 및 관리에 집중한다.
2. Stateless
   서버는 각 클라이언트 요청을 별개의 것으로 간주하고, 요청간에 상태를 저장하지 않는다. 모든 필요정보는 요청에 포함되어야 한다.
3. Cacheable
   응답 데이터는 캐시될 수 있어야 한다. 이를 통해 성능을 향상시킬 수 있다. 
4. Layered System: 클라이언트는 서버가 많던 적던 서버 사이에 게이트웨이 등이 존재 여부와는 상관 없이 하나의 API 시스템을 사용할 수 있어야 한다.
5. Code on demand(Option)
   클라이언트가 원한다면 서버는 클라이언트가 실행할 수 있는 코드를 클라이어늩에 보내줄 수 있다. 
6. Uniform Interface
   RESTful한 시스템인지 아닌지를 결정하는 중요한 요소로 API 설계는 일관된 인터페이스를 가져야 한다. 리소스는 고유한 URI로 식별하고 HTTP 메서드(GET, POST, PUT, DELETE 등)를 사용하여 리소스에 대한 작업을 수행한다.

주요 구성 요소

1. 자원(Resource)
   각 자원은 고유한 URI를 통해 식별된다. 
2. HTTP 메서드(HTTP Methods)
   자원에 대한 다양한 동작을 정의하는 데 사용된다.
   - GET: 자원 조회
   - POST: 자원 생성
   - PUT: 기존 자원의 전체 업데이트
   - PATCH: 기존 자원의 부분 업데이트
   - DELETE: 자원 삭제
3. 표현(Representations)
   자원은 JSON, XML 등 다양한 형식으로 표현될 수 있다. 클라이언트와 서버는 표현 형식을 협상하여 결정한다.
4. 상태 코드(State Codes)
   요청 결과를 나타내는 데 사용된다.
   - 200: 요청 성공(OK)
   - 201: 자원 생성 성공(Created)
   - 400: 잘못된 요청(Bad Request)
   - 401: 인증 필요(Unauthorized)
   - 404: 자원 없음(Not Found)
   - 500: 서버 오류(Internal Server Error) 