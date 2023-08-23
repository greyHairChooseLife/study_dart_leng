# learn Dart

<details>
  <summary><h4 style="color: white; display: inline-block;"><span style="color: grey;">Type of Variable: </span>var vs [type] vs dynamic</h4></summary>
  <div style="background-color: #E2EADD; padding: 10px; color: black">
  
변수의 타입을 지정한다.(값은 재할당 가능한 것이 default다.)
  
1. var: 알아서 추론한다. 한번 추론 된 타입은 변하지 않는다.
2. String, int, double, boolean, ... : 하나 지정한다. 타입은 변하지 않는다. 
3. dynamic: 타입이 변경 될 수 있다. 즉, 다른 타입의 값이 재할당 될 수 있다.

기본적으로 타입을 지정해서 쓰고, 필요에 따라 dynamic을 쓰도록 하자. var같은건 쓸 일이 있을까?

> Ref: youtube 코드팩토리' [무료 프로그래밍 강의] 1시간만에 끝내는 Dart언어 기본기 https://www.youtube.com/watch?v=3Ck42C2ZCb8

  </div>
</details>

<details>
  <summary><h4 style="color: white; display: inline-block;"><span style="color: grey;">Constant Variable: </span>final vs const</h4></summary>
  <div style="background-color: #E2EADD; padding: 10px; color: black">
  
상수인 변수를 선언한다.

그러나,

1. final 변수에는 build-time, run-time에 결정되는 값을 할당 할 수 있다.
2. const 변수에는 build-time에 결정되는 값을 할당 할 수 있다. run-time에 결정되는 값을 할당 할 수 없다.

<pre style="padding-top: 0;"><code style="color: white;">
const now = Datetime.now(); // error
</code></pre>

> Ref: youtube 코드팩토리' [무료 프로그래밍 강의] 1시간만에 끝내는 Dart언어 기본기 https://www.youtube.com/watch?v=3Ck42C2ZCb8

  </div>
</details>

<details>
  <summary><h4 style="color: white; display: inline-block;"><span style="color: grey;">(non-)NULL Ability: </span>var? vs var!</h4></summary>
  <div style="background-color: #E2EADD; padding: 10px; color: black">
  
nullability 여부에 Javascript 보다 깐깐하다.

1. var?: null 가능

<pre style="padding-top: 0;"><code style="color: white;">
String name? = 'sangyeon';
name = null; // fine 
</code></pre>

2. var!: null 불가능

> Ref: youtube 코드팩토리' [무료 프로그래밍 강의] 1시간만에 끝내는 Dart언어 기본기 https://www.youtube.com/watch?v=3Ck42C2ZCb8

  </div>
</details>

<details>
  <summary><h4 style="color: white; display: inline-block;"><span style="color: grey;">Set of Variables: </span>List, Map, Set</h4></summary>
  <div style="background-color: #E2EADD; padding: 10px; color: black">
  
1. List\<Type>
2. Map\<key-type, value-type>
3. Set\<Type> : List랑 똑같은데, 중복 제거 해 준다.

> Ref: youtube 코드팩토리' [무료 프로그래밍 강의] 1시간만에 끝내는 Dart언어 기본기 https://www.youtube.com/watch?v=3Ck42C2ZCb8

  </div>
</details>

<details>
  <summary><h4 style="color: white; display: inline-block;"><span style="color: grey;"></span>enum</h4></summary>
  <div style="background-color: #E2EADD; padding: 10px; color: black">
  
  
<pre style="padding-top: 0;"><code style="color: white;">
enum Status {
  approved,
  pending,
  rejected,
}

void main() {
Status status = Status.approved;

if (status == Status.approved) {
print('승인');
} else if (status == Status.pending) {
print('대기');
} else {
print('거절');
}
}
</code></pre>

> Ref: youtube 코드팩토리' [무료 프로그래밍 강의] 1시간만에 끝내는 Dart언어 기본기 https://www.youtube.com/watch?v=3Ck42C2ZCb8

  </div>
</details>

<details>
  <summary><h4 style="color: white; display: inline-block;"><span style="color: grey;">Parameter of Function: </span>positional, optional, named</h4></summary>
  <div style="background-color: #E2EADD; padding: 10px; color: black">
  
1. positional
    : 순서대로 드간다.

2. optional
<pre style="padding-top: 0;"><code style="color: white;">
  addNumbers(int x, [int y = 0]) {
    return x + y;
  }

print(addNumbers(30)); // 30, no error occurred
</code></pre>

3. named

<pre style="padding-top: 0;"><code style="color: white;">
  int addNumbers({
    required int x,
    required int y,
    int z = 5, // optional
  }) {
    return x + y + z;
  }

  print(addNumbers(y: 30, x: 10));  // 45
</code></pre>

> Ref: youtube 코드팩토리' [무료 프로그래밍 강의] 1시간만에 끝내는 Dart언어 기본기 https://www.youtube.com/watch?v=3Ck42C2ZCb8

  </div>
</details>

<details>
  <summary><h4 style="color: white; display: inline-block;"><span style="color: grey;">Define Type: </span>typedef</h4></summary>
  <div style="background-color: #E2EADD; padding: 10px; color: black">
  
<pre style="padding-top: 0;"><code style="color: white;">
void main() {
  final int result = calc(5, 10, 20, add);

print(result); // 35
}

typedef Operation = int Function(int x, int y, int z);

int add(int x, int y, int z) => x + y + z;
int subtract(int x, int y, int z) => x - y - z;

// 이 부분의 표현력의 핵심
// 또한 operation 부분의 타입을 지정하지 않으면 리턴 타입이 dynamic하게 된다. run-time에 오류 가능성 있음.
int calc(int x, int y, int z, Operation operation) => operation(x, y, z);
</code></pre>

> Ref: youtube 코드팩토리' [무료 프로그래밍 강의] 1시간만에 끝내는 Dart언어 기본기 https://www.youtube.com/watch?v=3Ck42C2ZCb8

  </div>
</details>
