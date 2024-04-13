# 웹 브라우저의 렌더링 과정

웹 브라우저의 렌더링 과정은 사용자가 웹 페이지에 접속했을때 HTML, CSS, Javascript 와 같은 코드를 시각적인 요소로 변환하는 단계를 말한다.

## CRP(Critical Rendering Path) 중요 렌더링 경로

웹 페이지가 처음 표시될 때까지의 중요한 단계를 이야기 한다. 사용자에게 첫 화면이 빨리 표시되도록 하는 데 중점을 둔 렌더링 과정의 핵심 부분이다. 

![Critical Rendering Path](https://raw.githubusercontent.com/devvara/support-repo/master/media/images/log/web-api/browser-rendering.png)

<br/>

1. HTML 파싱 및 DOM 트리 구축
   브라우저가 HTML 문서를 읽고 DOM 트리를 생성한다. 이 트리는 웹 페이지의 구조적 표현으로, 각 HTML 요소를 노드로 포함한다.
2. CSS 파싱 및 CSSOM 트리 구축
   동시에 CSS 정보를 읽고 처리하여 CSSOM 트리를 구축한다. CSSOM 트리는 웹 페이지의 각 요소에 적용될 스타일 정보를 포함한다.
3. 렌더 트리 생성
   DOM과 CSSOM이 준비되면, 브라우저는 이 두 트리를 결합하여 렌더 트리를 생성한다. 렌더 트리는 화면에 실제로 표시될 요소들을 포함하며, 각 요소의 시각적 속성을 담고 있다.
   (* 시각적 속성만 포함되며 head, script, display: none인 요소들은 제외된다.)
4. 레이아웃(레이아웃 처리)
   렌더 트리가 완성되면, 각 요소의 정확한 위치와 크기를 계산하는 레이아웃 과정이 이루어진다. 페이지 각 요소가 화면 상에서 어디에 위치할지를 정하는 단계이다.
5. 페인팅(화면에 표시)
   요소들의 위치와 크기가 결정되면, 페인팅 과정을 통해 이 요소들을 화면에 그린다. 이때 색상, 이미지, 텍스트 등의 시각적 디테일이 적용된다.
6. 합성(다양한 레이어 합성)
   페인팅 단계까지 여러 레이어로 구성된 요소들을 하나의 페이지로 합성하여 최종적으로 사용자에게 표시한다.

<br/>

![Critical Rendering Path](https://raw.githubusercontent.com/devvara/support-repo/master/media/images/log/web-api/browser-rendering-layout.png)

- 왼쪽이 DOM 트리, 오른쪽이 랜더 트리

CRP를 최적화 하는 것은 웹 페이지의 로딩 속도를 개선하는데 매우 중요하며, 사용자 경험을 크게 향상 시킬 수 있다. 
