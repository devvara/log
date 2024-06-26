# 메모리 관리

자바스크립트의 메모리 관리는 스택과 힙의 조합으로 이루어진다. 

## 메모리 생명주기

1. 메모리 할당

자바스크립트 엔진은 변수에 값을 저장하기 위해 먼저 메모리를 할당한다. 변수를 선언하고 초기화할 때 (`var a = a;`) 엔진은 숫자 2를 저장할 메모리 공간을 할당한다. 객체의 경우 (`var obj = {};`) 객체를 저장할 메모리 공간이 할당되며, 이후 속성이 추가될 때 추가적인 메모리 할당이 이루어진다.

자바스크립트의 메모리의 스택과 힙은 메모리 관리를 효율적으로 할 수 있게 해준다. 각각의 데이터 타입이 적합한 방식으로 처리되도록 한다. 원시값은 크기가 정해져 있고 관리가 간단하기 때문에 스택에 저장하는 것이 적합하고, 복잡하고 크기가 변할 수 있는 참조값은 힙에 저장하는 것이 적합하다.

- 원시값(Primitiv Values): 이 값들은 숫자, 문자열, 불린 `null`, `undefiend`와 같은 간단한 데이터 타입을 포함한다. 함수가 호출되면 원시값들은 스택에 저장된다. 원시값은 값에 의한 전달(pass by value) 방식으로 처리되기 때문에, 함수에 원시값을 인자로 전달하면 값의 복사본이 생성되어 스택에 저장된다.

- 참조값(Reference Values): 객체, 배열, 함수 등과 같은 복잡한 데이터 구조는 참조 값으로 처리된다. 이러한 값은 힙 메모리에 저장되며, 스택에는 이 객체를 가리키는 주소값(참조)이 저장된다. 따라서 함수에 객체를 인자로 전달할 때 전달되는 것은 객체의 실제 메모리 주소(참조)이다. 이는 참조에 의한 전달(pass by reference)방식으로 함수 내에서 객체를 변경하면 원본 객체에 영향을 미친다.

2. 사용(읽기 및 쓰기)

할당된 메모리 값을 저장하고 참조하는 데 사용된다. 프로그램 실행 동안 변수의 값이 읽히거나 수정될 수 있다. `a` 변수 값을 다른 값으로 변경하거나 `obj` 객체에 새로운 속성을 추가할 때 해당 메모리 주소에 쓰기 작업이 이루어진다. 

3. 메모리 해제

프로그램이 더 이상 해당 메모리를 필요로 하지 않을 때, 할당된 메모리는 해제되어야 한다. 원시 타입의 경우, 변수가 함수 내에서 선언되었다면 그 함수의 실행 컨텍스트가 종료될 때 스택에서 자동 해제 된다. 객체의 경우, 가비지 컬렉션에 의해 메모리가 자동으로 해제한다. 객체나 배열이 더 이상 접근할 수 없을 때, 즉 참조하는 변수가 더 이상 존재하지 않거나 참조가 덮어싀워질 때 가비지 컬렉터가 이를 감지하고 해제한다.

## 스택 메모리(Stack Memory)

스택 메모리는 함수의 호출과 함께 사용되는 지역 변수와 매개변수를 저장하는데 사용된다 데이터를 제거하고 수정하는 작업이 매우 빠르게 진행된다.

- 정적 메모리 할당: 스택은 컴파일 타임에 크기가 결정되는 변수들을 저장한다. 함수 내에서 선언된 원시 타입 변수들이 이 영역에 할당된다.

## 힙 메모리(Heap Memory)

힙 메모리는 더 복잡한 데이터 구조와 동적으로 할당되어야 하는 큰 데이터를 저장하는데 사용된다. 힙은 스택에 비해 유연하지만 속도가 느리다.

- 동적 메모리 할당: 힙은 실행 시간에 메모리 할당이 결정되는 객체와 배열 같은 참조 타입을 저장한다. 크기가 변할 수 있거나, 생명 주기가 함수 호출보다 길어야 하는 데이터(전역 변수, 싱글턴 객체, 종속성 주입 객체 등)도 여기에 저장된다.
- 가비지 컬렉션: 힙에 저장된 데이터는 자동으로 메모리 관리가 이루어진다. 자바스클비트 엔진의 가비지 컬렉터가 도달할 수 없는 객체를 주기적으로 검사하고, 더 이상 사용되지 않는 객체를 메모리에서 제거한다. 
- 전역 변수: 전역 변수는 애플리케이션의 전 생명주기 동안 유지되어야 하기 때문에 힙메모리 영역에 저장된다. 