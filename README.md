# JS = 동적 타입 언어

- 타입이 컴파일 타임에 결정되지 않고 런타임에 결정되는 언어
- 유연성이 높아 프로토타이핑과 빠른 개발에 우리
- 타입 안정성으로 인해 예기치 않은 오류들이 발생할 수 있음
- 디버깅 어려움 (타입오류 추적하고 수정하기 어려움)
- 유지보수 어려움 (타입 정보 명확하지 않으면, 코드 이해 및 수정 어려움)

### JS 데이터

JS=ES(ECMA 스크립트)

문자데이터

```javascript
원시형 string, number
문자데이터 표현 방식
1. 따옴표사용  '' ,  " "
2. 백틱기호 사용한 템플릿 리터럴 (어떠한 기호를 통해 데이터 생성 방법) ``
   데이터 보간 : 어떤 데이터를 문자 데이터 내에 채워넣는 용도

ex)
const string1 = "Hello"
const string3 = `Hello ${string1} ?!`

console. log(string3) // Hello Hello?!
```

배열데이터

```javascript
// Array(배열)
배열 리터럴 방식 : 기호 사용 []
```

Object (객체)

```javascript
1. new Object() 생성자 함수로 생성
ex)
const user = new Object()
user.name = 'HEROPY'
user.age = 85

2. 내부에서 this 키워드 사용
ex)
function User() {
  this.name = 'HEROPY'
  this.age = 85
}

3. {} 중괄호 리터럴 방식으로 생성

```

연산자와 구문 (객체)

```javascript
// 할당(Assignment)

let a = 3
// a = a + 2
// a += 2
-> a라는 변수에 숫자2를 더해서 다시 할당한다는 의미

// 증감(Increment & Decrement )
기호를 앞 혹은 뒤에 붙이는 것에 따라 값이 달라짐

let a = 3

console.log(++a) //4
console.log(a) // 4

console.log(a++) //3 a 뒤에 ++기호를 붙인 다음에 호출할 경우 증가된값확인
console.log(a) //4

```

논리 연산자(Logical)

```javascript
//AND 연산자
왼쪽에서 오른쪽으로 해석하면서 제일먼저 만나는 거짓데이터 반환
모두가 참이면 가장 마지막 참 데이터가 반환
ex)
console.log(1 && 2 && 0) // 0
console.log('A' && 'B' && 'C') //C

//OR 연산자
왼쪽에서 오른쪽으로 해석하면서 제일먼저 만나는 참데이터 반환
ex)
console.log( false || true) // true
console.log(0 || 1) // 1
```

Nullish 병합(/Nullish Coalescing)

```javascript
// Nulish 병합 연산자 사용하는 경우
왼쪽에서 오른쪽으로 가는 것은 동일한데 거짓과 상관없이 null 혹은 undefined
건너뛰고 그 외 모든 나머지 데이터 반환
const num2 = n ?? 7
console.log(num2) // 0
```

삼항(Ternary)

```javascript
삼항 연산자
// 조건 ? 참 : 거짓
```

# 함수(Function)

## 함수 선언문(Declaration)

function hello() {}  
-> function 키워드로 시작해 이름이 존재

## 함수 표현식(Experssion)

const hello = function() {}  
-> const, let 통해 변수 이름 지정, 할당연산자 통해 함수할당

## 호이스팅(Hoisting)

**호이스팅(Hoistiong)은 함수 선언부가 유효범위 최상단으로 끌어올려지는 현상**  
js는 코드 작성순서대로 해석하여 동작  
아래 예시코드는 함수 호출 후 함수를 선언하고 있으나 유효범위 내에 있는 경우
js의 최상단으로 올라가 동작  
 (함수 선언문에서만 동작, 표현식에서는 동작하지 않음)  
 _함수 표현식과 함수 선언에서의 함수 동작 차이를 인지_

```javascript
hello();
function hello() {
  console.log("hello~");
}
```

## 반환 및 종료

return 키워드를 통해서 js 데이터 반환
함수가 호출되면 그결과로 값이 남음
return 키워드는 함수를 종료하는 역할도 함

```javascript
function hello() {
  return "hello~";
}

console.log(hello()); // Hello~
```

## 매개변수 패턴(Parameter pattern)

### 기본값 (Default value)

인수에 값이 없는 경우 매개변수에 기본값을 할당해 함수 동작

#### 객체 구조분해 할당(Destructuring assignment)

```javascript
const user {
  name: 'HEROPY',
  age: 85
}

1. function getName(user) {
  return user.name
}


2. 객첵구조 분해 할당
function getName(user) {
  const { name } = user
  return name
}

3. user라는 매개변수 자체가 객체데이터이므로 객체데이터 자체를 매개변수에서 구조분해 (문법 간단)
function getName({ name }) {
  return name
}

console.log(getName(user))  // HEROPY

```

#### 배열 구조분해 할당(Destructuring assignment)

```javascript

const fruits = ['Apple', 'Banana', 'Cherry']

1. function getSecondItem(array) {
 return array[1]
}

2. 배열구조분해 할당
function getSecondItem([, b]) {
 return b
}
console.log(getSecondItm(fruits)) // Banana

```

#### 나머지 매개변수 (Rest parameter)

```javascript
전개 연산자를 통해 rest 매개변수는 들어오는 인수들을 받아서 배열로 저장
배열데이터의 reduce 메소드 사용
유사배열(Array-Like) 배열과 유사한 객체 데이터 함수로 들어오는 모든 인수정보 따로 지정하지 않아도 항상 사용 가능
function sum(...rest) {
  console.log(rest)
  console.lg(arguments)  // 유사배열
  rest.reduce(function (acc, cur) {
    return acc + cur
  }, 0)
}

console.log(sum(1,2)) // 3
console.log(sum(1,2,3,4)) // 10
console.log(sum(1,2,3,4,5,6,7,8,9,10)) //55

```

### 화살표함수 (Arrow function)

function과 {} return키워드 생략한 함수

```javascript
// function sum(a, b) {
//    return a + b
//  }

const sum = (a, b) => {
  return a + b;
};

const sum = (a, b) => a + b;

console.log(sum(1, 2)); // 3
console.log(sum(1, 2, 3, 4)); // 10
```

### 화살표함수 사용패턴 (Arrow function)

```javascript
화살표 함수는 변수에 할당 (함수 표현)
const a = () => {}

매개변수가 하나인 경우 소괄호 생략 가능
const b = x => {}

함수에 객체데이터를 반환하는 경우 소괄호로 감싸서 표현
const g = () => { return { a:1 }}
const h = () => ({ a:1 })

```

### 즉시실행함수(IIFE)

기본적으로 함수 호출위해 이름을 부여하지만 즉시실행함수는
별도의 이름없이 바로 실행되기 원하는 경우 익명함수로 바로 실행
즉시실행 함수 앞에는 ;(세미콜론)이 붙어있다는 것을 전제

**소괄호로 들어가는 각각의 데이터들을 즉시 실행하는 해당 함수에 매개변수로
전달 가능 -> 다양한 전역 데이터 이름 간소화 가능**

```javascript
const a = 7

const double = () => {
  consol.log(a*2)
}
double()

;(()=> {
  console.log(a*2)
}) ()

;(()=> {})()            // (F)()

*function키워드 사용하는 일반함수 사용시 즉시실행 패턴 4가지*
;(function () {})()    //  (F)()
;(function () {} ())   //  (F())
;!function () {}()    //  !(F)()
;+function () {}()   //   +F()

// 소괄호로 들어가는 각각의 데이터들을 즉시 실행하는 해당 함수에 매개변수로 전달 가능

;((a, b) => {
  console.log(a)
  console.log(b)
})(1,2)    // 1, 2 출력

```

### 콜백(Callback)

**_함수가 실행될때 인수로 들어가는 또 하나의 함수를 콜백_**  
함수가 하나의 데이터라는것을 응용해서 다른함수의 인수로 전달하면서 그것을
다른함수의 내부에서 호출하는 개념
해당하는 내용을 정확하게 필요한 위치에서 실행 가능

```javascript
*원리 이해
a, b 모두 함수 a를 실행할때 b라는 함수 인수를 넣어서 실행
함수데이터가 콜백이라는 이름의 매개변수로 들어가게 됨
함수 데이터는 소괄호를 통해 언제든지 실행가능
콘솔 로그로 A가 출력되고 콜백 b 함수가 호출되기 때문에 A, B가 순차적으로 출력

const a = callback => {
  console.log('A')
  callback()
}
const b = () => {
  console.log('B')
}

a(b) // A , B 로 출력


setTimeout 함수 예제
sum 함수의 세번째 인수 함수가 c라는 매개변수로 들어가 동작
c라는 함수가 호출될때 a+b 값을 받음 -> sum 함수가 호출될때 만들어진 세번째 인수에 해당하는 함수
a+b를 더한 값을 value라는 이름의 매개변수가 받아서 콘솔에 출력

const sum = (a, b, c) => {
  setTimeout(() => {
    c(a + b)
  } ,1000) // setTimeout 실행시 인수로 화살표 함수 실행 (콜백함수)
}

sum(1,2, value => {
  console.log(value)
})
console.log(sum(1,2)) // 3

```

## For, For of, For in 반복문

```javascript
For 반복문
for (초기화; 조건; 증감) {
  //반복 실행할 코드
}

for (let i = 0; i < 10; i += 1) {} // i = 0 으로 시작해서 10보다 작을 때 +1을 반복하는 코드
break 키워드 활용해서 반복문 종료 가능
continue 키워드 현재 반복을 종료 하고 다음 반복으로 넘어감

ex)
for (let i = 9; i > -1; i -= 1) {
  if(i % 2 === 0) {
    continue
  } // i = 8 인경우 2로 나누면 나머지값이 0이기에 현재 반복문을 종료하고 다음값인 7로 반복문 실행, 결론적으로 해당코드는 홀수값만 반환
  console.log(i) //9,7,5,3,1
}

for of 반복문

const fruits = ['Apple', 'Banana', 'Cherry']

for (let i = 0; i < fruits.length; i+=1) {
  console.log(fruits[i])
}  // 아이템의 대괄호 표기법으로 length 속성을 이용해서 인덱싱 반복실행

** 위의 내용과 동일하게 동작하는 for of 반복문
for (const a of fruits) {
  console.log(a) // a라는 변수에 할당해서 출력
}

for in 반복문
객체데이터속성 반복 in 키워드 사용

const user = {
  name: 'Heropy',
  age: 85,
  isValid: true,
  email: '41ehdgml@naver.com'
}

for (const key in user) {
  console.log(key)
  console.log(user[key]) // 대괄호표기법으로 key 속성값조회
}
// name Heropy

```

```javascript
while 반복문 조건이 거짓인 경우 반복 중단

Do while 반복문 조건이 거짓이더라도 최초 한번은 실행
do {} while ()

```

```javascript
예제) 로딩 후 이미지 출력
// 콜백
// https://www.gstatic.com/web/gallery/4.jpg

1. document.createElement로 이미지 태그를 js상에서 생성
2. imgEl src 속성에다 인수로 받은 url 정보를 할당
3. imgEl 에 addEventListener를 통해서 load 이벤트 적용 및 callback 함수 추가
4. load이벤트는 src속성에 부여되어져 있는 이미지 주소를 실제로 로드해오는 이벤트
5. 이미지 주소로 로드가 끝나면 해당하는 callback이 실행되는 구조
6. loadImage() 함수 첫번째 인수로 이미지 주소 문자데이터로 입력
7. 로드이미지 함수가 동작할 때 url정보가 들어가게 되는데 받은 url정보를 자바스크립트의 메모리 상에 만든 이미지 태그를 통해서 src속성에 추가
8. 추가된 이미지가 로드가 되면 addEventListener의 콜백함수가 실행
9. cb() 매개변수를 호출하는 시점은 이미지주소가 전부 다 로드가 끝난 상태이기 때문에 cb라는 함수의 인수로 JS 메모리상에 생성된 이미지 엘리먼트를 전달
10. innerhtml로 내부에 있는 h1태그 내용은 비워주고 append 메소드로 메모리상에 만들어져 있는 이미지 요소를 실제 내부로 밀어넣음

const loadImage = (url, cb) => {
  const imgEl = document.createElement('img')
  imgEl.src = url
  imgEl.addEnvetListener('load', () => {
    setTimeout(() => {
      cb(imgEl)
    },1000)
  })
}

const containerEl = document.querySelector('.container')
loadImage('https://www.gstatic.com/web/gallery/4.jpg', imgEl => {
  containerEl.innerHTML = ''
  containerEl.append(imgel)
})

```

```javascript
JS 모듈 활용
*Import 키워드로 JS 배열데이터 가져와 출력
예제) iPad 추천

JS 상단에 import ipads from "../data/ipads.js"
HTML에 type=module 추가
1. 변수 생성
cosnt itemsEl = document.querySelector('section.compare items') // 섹션태그의 compare 클래스의 하위 클래스 items를 itemsEl 변수로 할당
2. forEach메소드, 반복처리할 함수추가
ipads.forEach(function(ipad) {
  const itemEl = document.createElement('div')
  itemEl.classList.add('item')
  itemEl.textContent = ipad.name // ipads는 배열데이터로 forEach메소드로 반복되는 아이템을 처리하는 함수 추가, 매개변수는 반복되는 각각의 아이템, ipads를 반복하기에 ipad로 매개변수 작성, 아이패드에 정보를 출력해줄 요소를 자바스크립트를 통해서 표현
// createElement 요소를 자바스크립트를 생성하는 메소드, 인수로는 생성하고자 하는 요소에 태그 이름
//item elemenet에 item 클래스 추가
//textContent로 내용 추가

 itemsEl.append(itemEl)
})

3. 메모리상 존재하는 JS 내용 실제 요소에 추가
//찾아놓은 itemsEl이라는 요소에 append 메소드로 하나씩 밀어넣기itemsEl에 item 엘리먼트 넣기 forEach 메소드로 총 4번 반복, 4개의 아이템이라는 클래스를 가진 div요소가 items라는 클래스의 div 요소에 하나씩 들어가는 구조


4. textContent 속성과 innerHTML 속성
textContent속성은 글자 내용으로 어떠한 값을 요소 내부에 추가
innerHTML속성은 삽입하는 문자를 실제 HTML구조로 내부에 추가
```

```javascript
재귀 (Recursive)
하나의 함수에서 그 함수 자기 자신을 다시 내부에서 호출해서 사용하는 방법
재귀함수는 무한정 동작하기 때문에 필요에 따라 멈춤 필요


```

```javascript
호출 스케줄링 (Scheduling a function call)
함수에 호출을 지연하거나 혹은 반복적으로 호출할 수 있도록 만들어 주는 호출 스케줄링

ex) setTimeout 함수를 통해서 사용하고자 하는 어떤 특정한 함수의 실행시간을 지연

```

```javascript
this
일반 함수의 this는 호출 위치에서 정의
-> .call이라는 메소드를 통해서 어떤 객체 데이터가 가지고 있는 특정한 메소드를 다른 객체 데이터가 빌려와서 쓸 수 있다는 장점
화살표 함수의 this는 자신이 선언된 함수(렉시컬) 범위에서 정의

ex) 일반함수 this

const user = {
  firstName:'Donghee'
  lastName: 'Lee'
  age : 33
  getFullName: function() {
    return `${this.firstName} ${this.lastName} `
  }
}

console.log(user.getFullName()) // DongheeLee

// this는 결과적으로 user라는 객체 데이터가 되는것 user 객체 데이터에서 first name과 last name을 꺼내서 사용


eX) 화살표 함수의 this

const user = {
  firstName:'Donghee'
  lastName: 'Lee'
  age : 33
  getFullName: function() => {
    return `${this.firstName} ${this.lastName} `
  }
}

console.log(user.getFullName()) // undefined
get full name 함수의 this키워드는 자신이 선언된 함수, 내용을 감싸고 있는 외부의 또 다른 함수를 기준으로 this를 사용
하나의 객체 데이터에서 어떤 특정한 속성의 함수를 할당하게 되면 그 속성은 method라고 칭함

function user() {
  this.firstNmae = 'Neo'
  this.lastName = 'Anderson'

return {
  firstName:'Donghee'
  lastName: 'Lee'
  age : 33
  getFullName: () => {
    return `${this.firstName} ${this.lastName} `
    }
  }
}
const u = user()
console.log(u.getFullName()) // Neo Anderson

```

### 클래스

```javascript
// prototype
구글 검색 : Array mdn
기본적으로 배열 데이터에서 사용할 수 있는 각각의 속성이나 메소드들은 기본적으로 prototype 속성에 연결되어 있음
인스턴스 = 특정 클래스에서 생성된 개별적인 객체

new라는 키워드로 시작하는 함수 생성자 함수

**객체 리터럴 방식을 통해서 만드는 객체나 함수 내부에서 this라는 키워드로 각각 속성을 만들고 new라는 키워드와 함께 호출해서 생성하는 객체데이터는 사실상 같음

ex) 객체데이터를 만들어내는 User 생성 함수에 prototype으로 method를 등록해서 내부에 내장시켜 메소드를 빌려와 쓰지 않아도 됨


function User(first, last) {
  this.firstName = first
  this.lastName = last
}
User.prototype.getFullNale = function () {
  return `${this.firstName} ${this.lastName}`
}

const neo = new User('Neo', 'Anderson')

console.log(neo.getFullName()) // Neo Anderson


```

### 클래스

```javascript
// ES6 Classes
class 문법은 JS가 기존에 가지고 있던 prototype방식을 내장해서 새로운 문법으로 동작

구글 검색 : isArray mdn
class User {
  constructor() {
    this.firstName = first
    this.lastName = last
  }
  getFullName() {
     return `${this.firstName} ${this.lastName}`
  }
}


```

```javascript
// Getter, Setter
값을 얻거나 지정하는 용도의 메서드
getter와 setter는 속성처럼 사용 가능
getter는 값을 조회시 사용
할당 연산자를 통해 데이터를 할당하게 되면 setter 메소드 실행

ex)

class User {
  constructor(first, last) {
    this.firstName = first
    this.lastName = last
  }
  get fullName() {
    console.log('Getting full name!')
    return `${this.firstName} ${this.lastName}`
  }
  set fullName() {
    console.log(value)
    ;[this.firstName, this.lastName] =value.split('')
  }
}

const heropy = new User('Heropy', 'Park')

console.log(heropy,fullName)

heropy.firstName = 'Neo'

console.log(heropy.fullName)

heropy.fullName = 'Neo Anderson'
console.log(heropy)


```

```javascript
// 정적 메소드 (static methods)
prototype에 붙어있는 메소드는 prototype메소드
prototype이 붙어 있지 않는 메소드는 정적 메소드
static 키워드가 붙은 정적메소드는 클래스에서만 사용가능하고 각각의 인스턴스에서는 사용 불가

```

```javascript
// 상속 (Inheritance)
// 오버라이팅

//운송수단
class Vehicle {
  constructor(acceleration = 1) {
    this.speed = 0;
    this.acceleration = acceleration;
  }
  accelerate() {
    this.speed += this.acceleration;
  }
  decelerate() {
    if (this.spped <= 0) {
      console.log("정지");
      return;
    }
    this.speed -= this.acceleration;
  }
}

//자전거
class Bicycle extends Vehicle {
  constructor(price = 100, acceleration) {
    super(acceleration);
    this.price = price;
    this.wheel = 2;
  }
}
const bicycle = new Bicycle(300, 2);
console.log(bicycle);
//acceleration: 2 price: 300 speed:0 wheel: 2

// new Bicycle 생성자 함수를 통해 반환된 값을 할당하는 bicycle 변수는 인스턴스

// extends, super함수 키워드 사용해서 Vehicle class 연결
```

```javascript
// instanceof와 constructor
// 기본 상속코드

class A {
  constructor() {}
}
class B extends A {
  constructor() {
    spuer();
  }
}
```

```javascript
// .length
// 배열의 길이(숫자)를 반환

// .at()
// 대상 배열을 인덱싱
// 음수 값을 사용하면 뒤에서부터 인덱싱

// .concat()
// 대상 배열과 주어진 배열을 병합해 새로운 배열을 반환

//.every()
// 대상 배열의 모든 요소가 콜백 테스트에서 참(Truthy)를 반환하는지 확인

//.find()
// 대상 배열에서 콜백 테스트를 통과하는 첫 번째 요소를 반환

//.findIndex()
// 대상 배열에서 콜백 테스트를 통과하는 첫 번째 요소의 인덱스를 반환

//.forEach()
// 대상 배열의 길이만큼 주어진 콜백을 실행

//.includes()
// 대상 배열이 특정 요소를 포함하고 있는지 확인

//.join()
// 대상 배열의 모든 요소를 구분자로 연결한 문자를 반환

//.map()
// 대상 배열의 길이만큼 주어진 콜백을 실행하고, 콜백 반환값을 모아 새로운 배열반환

//.pop()
// 대상 배열에서 마지막 요소를 제거하고 그 요소를 반환
// 대상 배열 원본이 변경

//.push()
// 대상 배열의 마지막에 하나 이상의 요소를 추가하고, 배열의 새로운 길이를 반환
// 대상 배열 원본이 변경

//.reduce()
// 대상 배열의 길이만큼 주어진 콜백을 실행하고, 마지막에 호출되는 콜백의 반환값을 반환
// 각 콜백의 반환 값은 다음 콜백으로 전달

const numbers = [1, 2, 3];
const sum = numbers.reduce((acc, cur) => acc + cur, 0);
//0은 초깃값
console.log(sum); //6

//.reverse()
// 대상 배열의 순서를 반전
// 대상 배열 원본이 변경

//.shift()
// 대상 배열 첫 번째 요소 제거, 제거된 요소 반환
// 대상 배열 원본이 변경

//.slice()
// 대상 배열 일부를 추출해 새로운 배열 반환
// 두번째 인수 직전까지 추출하고, 두번째 인수를 생략하면 대상 배열의 끝까지 추출

//.sort()
// 대상 배열을 콜백의 반환 값(음수, 양수, 0)에 따라 정렬
// 콜백을 제공하지 않으면, 요소를 문자열로 변환하고 유니코드 포인트 순서로 정렬
// 대상 배열 원본이 변경
```

```javascript
// Object.assign()
// 하나 이상의 출처(Source) 객체로부터 대상(Target) 객체로 속성을 복사하고 대상 객체를 반환합니다.
```

```javascript
JSON (Javascript Object Notation)
// 데이터 전달을 위한 표준 포맷!
// 문자, 숫자, 불린, Null, 객체, 배열만 사용
// 문자는 큰 따옴표만 사용
// 후행 쉼표 사용 불가
// .json 확장자 사용

// JSON.stringify() -데이터를 JSON 문자로 변환
// JSON.parse() -JSON 문자를 분석해 데이터로 변환

```

```javascript
// 모듈(Module)이란 특정 데이터들의 집합(파일)
// 모듈 가져오기(Import), 내보내기(Export)

기본 내보내기 방식으로는 한번만 가능

```

```javascript
동기(Synchronous)와 비동기(Asynchronous)
// -동기 : 순차적으로 코드 실행 0
// -비동기 : 순차적으로 코드 실행 x

// 콜백(Callback) 패턴
내용이 복잡해지면 코드도 복잡해짐에 따라 Promise 클래스로 대체
// Promise

```

```javascript
//Async / Await
예제)
await 키워드는 async 키워드와 항상 함께 사용

const a = () => {
  return new Promise(resolve => {
    setTimeout(() => {
      console.log(1)
      resolve()
    }, 1000)
  })
}
const b = () => console.log(2)

// a().then(() => b())
const wrap =  async() => {
  await a()
  b()
}
wrap()

```
