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

## 1.4 Final Variables
- 수정 불가능한 변수 선언
- 선언과 동시에 값이 할당되야함
- var 대신해서 사용함
  
```dart
    final name = 'nico';
    name = 'nico';      // impossible...

    final String name2 = 'nico';    // possible...
```

## 1.5 Late Variables
- var 또는 final 앞에 붙어야함
- 값 할당을 나중에 할 수 있음
- final은 한번만 할당하고 끝이지만, late를 쓰면 나중에 할당하고 그 값을 변경하지 않게 할 수 있음

```dart
    late final name;
    // do something, go to api ...
    print(name);        // 나중에 할당될줄 알기 때문에 해당 함수는 실행되지 않음
    name = 'nico';
    print(name);        // possible... 값이 할당되어있기 때문에
    name = '12';        // impossible... still final variable
```

## 1.6 Constant Varaibles

## 1.7 Recap