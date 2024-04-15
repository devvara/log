# 블록(block) 요소와 인라인(inline) 요소

웹 페이지에서 요소들이 어떻게 배치되고 표현하는지를 결정하는 중요한 요소 유형

## 블록 요소(Block Elements)

대표적인 블록 요소: <div>,<p>,<h1>,<form>,<table>,<ul>,<dl>,<pre> 등

- 새 줄에서 항상 시작한다.
- 부모 요소의 전체 가로 폭을 차지한다.
- 'width', 'height'와 같은 크기 속성을 지정할 수 있다.
- 상하좌우 마진(margin), 패딩(padding)을 적용할 수 있다.


## 인라인 요소(Inline Elements)

대표적인 인라인 요소: <span>,<a>,<img>,<em>,<strong>,<input>,<label> 등

- 같은 줄에서 시작한다.
- 내용의 크기만큼만 공간을 차지한다.
- 'width', 'height'를 직접 조절할 수 없으며, 상하마진(margin), 패딩(padding)은 일부 브라우저에서 예상과 다르게 동작할 수 있다.
- 웹 브라우저에 의해 가상으로 생성되는 라인 박스 내에 배치된다. 테스트나 다른 인라인 요소와 같은 흐름으로 배치된다.

## 인라인 블록(Inline Block)

`disply: inline-block` 속성은 인라인 요소처럼 같은 줄에 배치되면서 블록처림 'width','height', 마진, 패딩을 모두 적용할 수 있다. 