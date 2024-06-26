# Browser Storage

## 쿠키(Cookies)

- 웹 서버와 클라이언트 간의 상태 정보를 저장
- 웹 서버가 응답으로 쿠키를 클라이언트에게 전달하면, 이후 클라이언트의 모든 요청에 쿠키 정보가 포함되어 서버로 전송
- 사용자 인증에 포함되는 세션 관리, 설정 등 서버가 필요로 하는 정보를 저장할 때 적합
- HTTP 요청 시 쿠키 데이터가 포함되므로 잘못 사용 시 네트워크 트래픽 증가 가능
- 만료일 설정 가능
- 보안(XSS 공격에 취약)을 위해 HTTPOnly 속성을 사용하여 스크립트를 통한 쿠키 접근을 방지(서버만 가능하게)
- 용량: 4KB
- 사용 예시: 사용자 인증 토큰 저장

## 로컬 스토리지 (LocalStorage)

- 브라우저에 영구적으로 데이터 저장
- 도메인별 별도 로컬 스토리지 생성
- 키-값 쌍을 사용하여 데이터 저장/검색
- 클라이언트 측에만 데이터가 저장되므로 서버에 부담 없음
- 용량: 5MB
- 사용 예시: 장바구니 상품 유지, 오프라인 웹앱 데이터 저장, 언어 설정

## 세션 스토리지(SessionStorage)

- 브라우저 세션(탭이 활성화된 경우) 동안에만 데이터 저장, 탭이 닫히면 데이터 삭제
- 동일한 웹 페이지도 브라우저 탭마다 데이터 격리 가능, 충돌 없음
- 세션 종료 시 데이터가 사라져 영구적인 정보 저장에는 부적합하다.
- 클라이언트 측에만 데이터가 저장되므로 서버에 부담 없음
- 용량: 5MB
- 사용 예시: 입력폼 데이터