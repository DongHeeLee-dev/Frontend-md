# 📘 JavaScript 핵심 개념 정리

---

## ✍️ 표기법(Naming Convention)

| 표기법 | 예시 | 설명 |
|--------|------|------|
| dash-case | `main-title` | HTML/CSS에서 주로 사용 |
| snake_case | `main_title` | 일부 백엔드 언어나 상수에서 사용 |
| camelCase | `mainTitle` | JS 변수, 함수명에 주로 사용 |
| PascalCase | `MainTitle` | JS 클래스명에 주로 사용 |

---

## 💬 주석 작성

```js
// 한 줄 주석
/*
  여러 줄 주석
*/
```

---

## 🧾 데이터 타입

### 🔹 문자형 (String)
```js
let name = "홍길동";
let greeting = `안녕하세요, ${name}`;
```

### 🔹 숫자형 (Number)
```js
let score = 95;
let opacity = 0.75;
```

### 🔹 불린형 (Boolean)
```js
let isOpen = true;
```

### 🔹 undefined
```js
let temp;
console.log(temp); // undefined
```

### 🔹 null
```js
let data = null;
```

### 🔹 객체 (Object)
```js
let user = {
  name: "Jane",
  age: 30
};
```

### 🔹 배열 (Array)
```js
let fruits = ["apple", "banana", "orange"];
```

---

## 🧠 변수 선언

| 키워드 | 설명 |
|--------|------|
| `let` | 재할당 가능 |
| `const` | 재할당 불가능 (상수) |

```js
let count = 1;
const PI = 3.14;
```

⚠️ `var`는 과거 방식 → 사용 지양

---

## 🔁 함수

```js
function sayHello(name) {
  return `Hello, ${name}`;
}
```

- 함수 호출: `sayHello("Lee");`
- **익명 함수** (함수 표현식)
```js
const greet = function(name) {
  return `Hi, ${name}`;
};
```

---

## 🎯 매개변수와 인수

```js
function add(a, b) {
  return a + b;
}
add(1, 2); // 1, 2가 인수
```

---

## 🧩 메서드 & 메서드 체이닝

- 객체 안 함수 = **메서드**
```js
const user = {
  sayHi: function() {
    console.log("Hi!");
  }
};
```

- 메서드 체이닝:
```js
element.classList.add("active").classList.remove("hide");
```

---

## 📄 DOM API

```js
document.querySelector('.search');
```

- HTML 요소를 선택하는 메서드
- 요소에 이벤트 연결:
```js
element.addEventListener("click", function() {
  // 이벤트 로직
});
```

---

## ✨ 스타벅스 예제 기반 JS 흐름

```js
const searchEl = document.querySelector('.search');
const searchInputEl = searchEl.querySelector('input');

searchEl.addEventListener('click', function () {
  searchInputEl.focus();
});

searchInputEl.addEventListener('focus', function () {
  searchEl.classList.add('focused');
  searchInputEl.setAttribute('placeholder', '통합검색');
});

searchInputEl.addEventListener('blur', function () {
  searchEl.classList.remove('focused');
  searchInputEl.setAttribute('placeholder', '');
});
```

---

## 📜 조건문

```js
if (조건) {
  // 참일 때 실행
} else {
  // 거짓일 때 실행
}
```

---

## 🖱️ 스크롤 이벤트 & throttle

```js
window.addEventListener('scroll', _.throttle(function () {
  console.log('scroll!');
}, 300));
```

- **_.throttle**: 실행 횟수 제한 (lodash 필요)

---

## 🎬 GSAP 애니메이션 예시

```js
gsap.to(element, 1, {
  opacity: 0,
  display: "none"
});
```

---

## 🔁 toggle 예제

```js
const promoEl = document.querySelector('.promotion');
const toggleBtn = document.querySelector('.toggle-promotion');
let isHidden = false;

toggleBtn.addEventListener('click', function () {
  isHidden = !isHidden;
  if (isHidden) {
    promoEl.classList.add('hide');
  } else {
    promoEl.classList.remove('hide');
  }
});
```

---

## 📌 기타 문법 팁

- `document`: HTML 전체
- `setAttribute(name, value)`: HTML 속성 조작
- `scrollY`: 스크롤 위치 값
- `!` (느낌표): 반대 boolean 값

---

