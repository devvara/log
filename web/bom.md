# 브라우저 객체 모델(Browser Object Model)

BOM은 브라우저에 의해 제공되는 객체의 집합으로, 자바스크립트가 브라우저 창, 문서, 환경, 브라우저의 특정 기능과 상호 작용할 수 있게 한다. 

BOM은 웹 표준의 일부가 아니기 때문에 브라우저마다 자체적인 구현과 확장을 할 수 있어 같은 BOM API가 서로 다른 브라우저에서 다르게 작동할 수 있거나 일부 기능은 특정 브라우저에서만 지원하는 것일 수 있다.

### window 객체

- BOM의 최상위 객체로, 브라우저 창이나 프레임
- 브라우저 컨텍스트 내에서 실행되는 자바스크립트 코드에 대한 글로벌 객체로 작용

### document 객체

- 현재 브라우저 창에 로드된 웹페이지
- DOM의 진입 점 역할
- HTML 문서의 내용과 구조를 조작할 수 있는 메서드와 속성

### location 객체

- 현재 페이지의 URL
- URL을 조작하는 다양한 속성과 메서드 제공
- location.href, location.hostname, location.search, location.pathname, location.hash 등의 속성을 통해 접근
- location.reload(), location.replace() 등의 메서드로 페이지 리로드 하거나 이동

### history 객체

- 브라우저 세션 히스토리 목록 관리
- history.back(), history.forward(), history.go() 메서드로 이전/다음 페이지로 이동
  
### screen 객체

- 사용자의 화면(디스플레이) 정보
- screen.width, screen.height, screen.colorDepth 등의 속성을 통해 화면의 해상도와 색상 깊이 정보 제공

### navigator 객체

- 브라우저 환경 정보 제공
- navigator.appName, navigator.appVersion, navigator.userAgent, navigator.platform, navigator.geolocation 등의 속성을 통해 브라우저와 운영 시스템 정보 획득