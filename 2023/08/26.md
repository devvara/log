#### 2023.8.26 | Flutter - Riverpod

#### Riverpod

Riverpod는 Flutter에서 사용하는 상태 관리 라이브러리 중 하나이다. Flutter 외에 Dart 프로젝트에서도 사용할 수 있지만, 주로 Flutter 앱 개발에서 널리 사용된다. Riverpod는 Provider라는 Flutter 상태 관리 라이브리러 개발자에 의해서 만들어 졌으며 Provider에서 발생한 문제점과 제약사항을 개선하는 목적을 가지고 만들어 졌다. 

#### Riverpod는 다음과 같은 특징을 가지고 있다.
1. 트리의 어느 곳에서나 상태에 접근 가능하다.
2. 불변성을 지원한다.
3. Provider간 의존성을 쉽게 설정할 수 있다.
4. 타입 안전성을 지원한다.

#### Riverpod 기본 사용법
1. Provider 선언: 상태를 제공할 `Provider`를 선언한다.
2. Provider 사용: `Comsumer` 위젯 또는 `watch` 메서드를 이용하여 Provider 상태를 사용한다.
3. 상태 업데이트: 상태를 변경하려면 `ProviderContainer`를 사용하거나 `StateNotifier`와 같은 다른 메커니즘을 사용한다.

````dart
import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';

// Provider 선언
final counterProvider = StateProvider<int>((ref) {
  return 0;
});

void main() {
  runApp(
    ProviderScope(
      child: MyApp(),
    ),
  );
}

class MyApp extends ConsumerWidget {
  @Override
  Widget build(BuildContext context, ScopedReader watch){
    // Provider 사용
    final count = watch(counterProvider).state;

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('Riverpod Counter')),
        body: Center(
          child: Text('Count: $count'),
        ),
        floatingActionButton: FloatingActionButton(
          onPressed: () {
            // 상태 업데이트
            context.read(counterProvider).state++;
          },
          child: Icon(Icons.add),
        ),
      ),
    );
  }
}

````