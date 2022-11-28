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
- dynamic 키워드를 통해 할당된 값에 따라 형태 변환이 가능

```dart
    dynamic name;
    name = 'nico';
    name = 123;
    name = true;

    if(name is String){
        // 이 조건문 안에서는 name이 String 이라는걸 인식함
    }
    // 바깥으로 나오면 name에 값이 할당되지 않으면 어떤 형태인지 모름
```

## 1.3 Nullable Variables
- 해당 변수에 null이 올 수도 있다고 암시해줌

```dart
    String nico = 'nico';
    nico = null;        // impossible...

    String? nano = 'nano';
    nano = null;        // possible...

    if(nano != null){
        nano.isNotEmpty;
    }

    nano?.isNotEmpty;   // 위의 조건문과 동일함
```