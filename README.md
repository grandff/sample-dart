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
- js와 ts의 constant 와 다름
- final은 실행 중에 값이 결정되는 반면, const는 컴파일시 값이 결정됨
- 이 파일을 컴파일할 때 기계어로 번역될 때 값이 결정됨

```dart
    const name = 'nico';
    name = '12';    // impossible... 마찬가지로 값을 할당을 못함

    const API = '121212';
```


## 2.0 Basic Data Type
- String, boole, int, double ...
- num 은 int도 될 수 있고, double도 될 수 있음

## 2.1 Lists
```dart
    var numbers = [1,2,3,4];
    List<int> numbers2 = [1,2,3,4]; // 위와 동일함

    numbers.add(1); // 요소 추가
    numbers.first;  // 첫번째 요소
    numbers.last;   // 마지막 요소
```

```dart
    var giveMeFive = true;
    var numbers = [1,2,3,4, if(giveMeFive) 5];  // list 안에 조건문 등을 통해 요소 삽입 가능
    print(numbers);
```

## 2.2 String Interpolation
```dart
    var name = 'nico';
    var greeting = 'Hello everyone, my name is $name, nice to meet you!';
    print(greeting);
```
- string안에 변수를 넣고 싶으면 $를 붙이면 됨
- single quote, double quote 상관 없음

```dart
    var name = 'nico';
    var age = 10;
    var greeting = 'Hello everyone, my name is $name and I\'m ${age+2}, nice to meet you!';
    print(greeting);
```
- ${}를 통해 연산 가능

## 2.3 Collection For
```dart
    var oldFriends = ['nico','lynn'];
    var newFriends = ['lewis', 'ralph', 'darren', for(var friends in oldFriends) "Yes $friend"];
    print(newFriends);
```
- for loop로 똑같이 배열안에 데이터 입력 가능

## 2.4 Maps
- js, ts의 map, python의 dictionary와 비슷함

## 2.5 Sets
- 모든 값이 유니크할 떄 sets 사용

```dart
    var numbers = {1,2,3,4};
    numbers.add(1);
    print(numbers); // 값은 바뀌지 않음
```

## 3.0 Defining a Function
- void는 리턴 값 없음
- 그 외는 선언한 타입에 맞는 값 리턴

```dart
    void sayHello(String name){
        print("Hello $name nico to meet you! ");
    }

    String sayHello(String name){
        return "Hello $name nice to meet you!";
    }

    String sayHello(String name) => "Hello $name nice to meet you!";    // arrow function 가능. 대신 한줄만 쓸때 가능.

    num plus(num a, num b) => a+b;
```

## 3.1 Named Parameters
- 파라미터를 넘길 때 특정 파라미터의 이름을 명시해서 넘기고 싶은 경우 사용

```dart
    String sayHello({String name='anon', int age = 99, String country = 'wakanda'}){    // 매개변수에 {} 추가. 대신 기본 값 설정을 해줘야함
        return "Hello $name, you are $age, and you come from $country";
    }

    void main(){
        print(sayHello(
            age : 12,
            country : 'cuba',
            name : 'nico'
        ));
    }
```

- default value를 설정 안하고 무조건 값을 받아와야 한다면 required 사용

```dart
    String sayHello({required String name, required int age, required String country}){
        ...
    }
```

## 3.3 Optional Positional Parameters
- 값이 없을 경우 처리

```dart
    String sayHello(
        String name,
        int age,
        [String? country = 'cuba']  // not required 설정. default value 는 필수.
    ) => 'Hello $name, you are $age years old from $country';

    void main(){
        var results = sayHello('nico', 12);
        print(results);
    }
```

## 3.4 QQ Operator
- ?? / ?= 같은 연산자로 null 처리

```dart
    // BAD
    String capitalizeName(String? name) => name.toUpperCase();  // arguments에 ?를 붙여서 null이 오면 toUpperCase가 작동안하므로 오류남
    // GOOD
    String capitalizeName(String? name) => name?.toUpperCase() ?? 'ANON';

    void main(){
        capitalizeName('nico'); // NICO
        capitalizeName(null);
    }
```

```dart
    String? name;
    name ??= 'nico';
    name ??= 'another'; // error.. 위에서 이미 null처리를 했으므로 다시 null이 나올 수 없음

    // 만약 하려면?
    name = null;
    name ??= 'another';
```

## 3.5 Typedef
- type을 직접 alias를 지정해서 만들 수 있음

```dart
    typedef ListOfInts = List<int>;

    ListOfInts reverseListOfNumbers(ListOfInts list){
        var reversed = list.reversed;
        return reversed.toList();
    }

    void main(){
        print(reverseListOfNumbers([1,2,3]));
    }
```

## 4.0 Your First Dart Class
- class는 type을 명시해야함
- 같은 이름을 가진 경우를 제외하고 class 안에서 this를 쓰는걸 권고하진 않음

```dart
    class Player{
        String name = 'nico';
        final String firstName = 'test';    // 수정불가
        int xp = 1500;

        void sayHello(){
            print("My name is $name");
        }
    }

    void main(){
        var player = Player();
        print(player.name);
        player.name = 'lalala';
        print(palyer.name);
        player.firstName = 'test2';     // error...
        player.sayHello();
    }
```


## 4.1 Constructors
- constructors 이름은 class와 동일해야함

```dart
    class Player{
        final String name;
        int xp;

        Player(this.name, this.xp); // this로 현재 class에 선언된 변수에 넣는다고 명시함        
    }

    void main(){
        var player = Player("nico", 1500);
        var player2 = Player("lynn", 2000);
    }
```

## 4.2 Named Constructor Parameters
- arguments를 너무 많이 쓰고 순서대로 나열하면 복잡해짐
- 함수에서 했던 것 처럼 명칭을 정해서 사용 가능함
- required 또는 default value 설정 중 하나를 해야함

```dart
    class Player{
        final String name;
        int xp;
        String team;
        int age;

        Player({required this.name, required this.xp, required this.team, required this.age});
    }

    void main(){
        var player = Player(
            name : "nico",
            xp : 1200,
            team : "blue",
            age : 21
        );
    }
```

## 4.3 Named Constructor
- class 안에 특정 명칭을 정한 생성자 사용 가능

```dart
    class Player{
        final String name;
        int xp, age;    // 같은 타입의 변수인 경우 한줄로도 가능함
        String team;

        Player({required this.name, required this.xp, required this.team, required this.age});  // 이건 클래스를 생성할 떄 호출되는 생성자

        // named Constructor 추가
        Player.createBluePlayer({
            required String name, required int age
        }) : this.age = age, this.name = name, this.team = 'blue', this.xp = 0; // : 이후에 들어오는 값들로 생성자 초기화

        Player.createRedPlayer(String name, int age) : this.age = age, this.name = name, this.team = 'red', this.xp = 0;    // named 안쓰고도 가능함
    }

    void main(){
        var player = Player.createBluePlayer(
            name : "nico",
            age : 21
        );

        var player2 = Player.createRedPlayer(
            "nico",
            21
        );
    }
```

## 4.5 Cascade Notation
- 생성자로 초기화한 변수 값을 변경하기 위해 cascade notation 사용

```dart
    class Player{
        final String name;
        int xp, age;  
        String team;

        Player({required this.name, required this.xp, required this.team, required this.age});  

        void sayHello(){
            print("My name is $name");
        }
    }

    void main(){
        var nico = Player(name : "nico", xp : 1200, team : "red")
            ..name = "las"
            ..xp = 120000
            ..team = "blue";

        // 아래처럼도 가능
        var potato = nico
            ..name = "las"
            ..xp = 120000
            ..team = "blue"
            ..sayHello();
    }
```

## 4.6 Enums
- flutter에서 많이 사용하게 될거임

```dart
    enum Team {red, blue};  // text 형태로 쓸 필요는 없음

    class Player{
        final String name;
        int xp, age;  
        Team team;

        Player({required this.name, required this.xp, required this.team, required this.age});  
    }

    void main(){
        var nico = Player(name : "nico", xp : 1200, team : Team.red);
        var potato = nico
            ..team = Team.blue;
    }
```