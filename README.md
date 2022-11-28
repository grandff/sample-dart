# Sample-Dart
dart 기본 강의

## 1.0 Hello World
- main 함수가 들어가야함(없으면 오류 발생)
- semicolon 을 꼭 붙여야함

## 1.1 The Var Keyword
- var가 기본 키워드
- 별도로 형태르 지정해주지 않아도 할당된 값에 따라 자동 설정
- 그게 싫으면 직접 형태를 지정하는 변수 사용(String 등)
- dart에서 권장하는건 var로 쓰라고 함

```dart
    var name = 'test';
    name = 1;   // this is error..

    String name2 = 'test2';
```

## 1.2 Dynamic Type