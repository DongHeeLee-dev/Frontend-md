# 🌱 CSS 기본 개념 + iPad 클론 프로젝트 실습 정리

## 1. 🔤 선택자(Selector) 기본

| 문법 | 의미 | 예시 |
|------|------|------|
| `.class` | 클래스 선택자 | `.btn`, `.title` |
| `#id` | ID 선택자 | `#header` |
| `tag` | 태그 선택자 | `body`, `a`, `img` |
| `.parent .child` | 자손 선택자 (띄어쓰기) | `.box img` (박스 안 모든 이미지) |
| `.parent > .child` | 자식 선택자 (>) | `.list > li` (직속 li만) |

---

## 2. 🧱 박스 모델(Box Model)

CSS에서 모든 요소는 **박스 형태**로 구성됨.

```
┌───────────────┐
│   margin      │  ← 바깥 여백
│ ┌───────────┐ │
│ │ padding   │ │  ← 안쪽 여백
│ │ ┌───────┐ │ │
│ │ │ content│ │ │
│ │ └───────┘ │ │
│ └───────────┘ │
└───────────────┘
```

| 속성 | 설명 |
|------|------|
| `margin` | 바깥 여백 |
| `padding` | 내부 여백 |
| `border` | 테두리 |
| `width`, `height` | 콘텐츠 크기 |

---

## 3. 📐 레이아웃 핵심 속성

| 속성 | 설명 |
|------|------|
| `display: flex` | 가로 정렬, 정렬 유연 |
| `justify-content` | 주 축 정렬 (가로) |
| `align-items` | 교차 축 정렬 (세로) |
| `position` | 요소 위치 지정 (`relative`, `absolute`, `fixed`) |
| `z-index` | 위로 쌓이는 순서 지정 |

---

# 💻 iPad 클론 프로젝트 CSS 실습 정리

## ✅ 공통 초기화
```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
a {
  text-decoration: none;
  color: inherit;
}
```

## ✅ 전체 페이지 래퍼
```css
.wrap {
  width: 100%;
  overflow-x: hidden;
}
```

## ✅ 헤더 스타일
```css
.header {
  width: 100%;
  padding: 20px 40px;
  position: fixed;
  top: 0;
  background-color: white;
  z-index: 10;
}
```

## ✅ 메인 비주얼 (Hero Section)
```css
.hero {
  height: 100vh;
  background: url('../images/hero.jpg') no-repeat center/cover;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

## ✅ 콘텐츠 이미지 스타일
```css
.section img {
  max-width: 100%;
  height: auto;
}
```

## ✅ 타이틀/텍스트
```css
.title {
  font-size: 48px;
  font-weight: bold;
}
.sub-title {
  font-size: 24px;
  color: #666;
}
```

## ✅ 반응형 미디어 쿼리
```css
@media screen and (max-width: 768px) {
  .title {
    font-size: 32px;
  }
  .sub-title {
    font-size: 18px;
  }
}
```

## ✅ 푸터 스타일
```css
.footer {
  background-color: #f5f5f7;
  padding: 60px 40px;
  text-align: center;
  font-size: 14px;
  color: #888;
}
```

## ✅ 클래스 네이밍 참고

| 클래스 | 역할 |
|--------|------|
| `.wrap` | 전체 래핑 |
| `.header` | 상단 네비 |
| `.hero` | 메인 비주얼 영역 |
| `.section` | 콘텐츠 섹션 |
| `.title`, `.sub-title` | 텍스트 스타일 |
| `.footer` | 하단 정보 영역 |

---

# ✅ 마무리 팁

- `flex`, `margin/padding`, `position`은 퍼블리싱의 핵심입니다.
- 클래스명은 의미 중심(`.hero`, `.title`)으로 명확하게 작성하는 습관을 들이세요.
- 필요할 때 Chrome 개발자도구에서 어떤 CSS가 적용됐는지 **실시간 확인하며 실습**하는 게 최고예요.


---

# 📱 @media와 Breakpoints (반응형 디자인 기초)

## ✅ 미디어 쿼리 기본 문법

```css
@media media-type and (condition) {
  /* CSS 속성 */
}
```

| 항목 | 예시 | 설명 |
|------|------|------|
| `media-type` | `screen`, `print`, `all` | 출력 환경 지정 |
| `condition` | `(max-width: 768px)` | 조건에 따른 스타일 적용 |
| `and` | 논리 연결자 | 여러 조건 연결 가능 |

### 📌 예시:
```css
@media screen and (max-width: 768px) {
  body {
    background-color: #f0f0f0;
  }
}
```

## ✅ 디바이스 방향 조건 (orientation)
```css
@media screen and (orientation: portrait) {
  /* 세로 모드일 때 적용 */
}

@media screen and (orientation: landscape) {
  /* 가로 모드일 때 적용 */
}
```

---

## 📁 CSS 파일 미디어 조건 연결

```html
<!-- 조건별로 다른 CSS 파일을 연결 -->
<link rel="stylesheet" href="style.css" media="screen and (max-width: 1260px)" />
```

---

## 🔁 Breakpoints (중단점)

| 디바이스 | 기준값 | 설명 |
|----------|--------|------|
| PC | ≥ 1001px | 데스크탑 뷰 |
| 태블릿 | ≤ 1000px | 중간 화면 대응 |
| 모바일 | ≤ 740px | 스마트폰 뷰 |

---

## 🎯 가상 클래스 선택자 (Pseudo-classes)

| 선택자 | 설명 |
|--------|------|
| `:hover` | 마우스를 올렸을 때 |
| `:active` | 클릭한 순간 |
| `:focus` | 요소에 포커스 되었을 때 (입력 가능 상태) |

### 📌 `focus` 관련
- `input`, `a`, `button` 등은 기본적으로 포커스 가능
- `tabindex="0"`을 추가하면 다른 요소도 포커스 가능
- `tabindex="-1"`은 포커스는 가능하지만 Tab 키로 접근 불가

> 📌 참고: [HTML 대화형 콘텐츠 목록 - MDN](https://developer.mozilla.org/ko/docs/Web/Guide/HTML/Content_categories#interactive_content)



---

# 🧩 CSS 개요 및 선언 방식 (보완 정리)

## 🔹 CSS 개요
- CSS는 HTML 요소의 디자인을 정의하는 스타일 시트 언어입니다.
- 구성: 선택자(selector) + 속성(property) + 값(value)

```css
선택자 {
  속성: 값;
}
```

## 🔹 CSS 선언 방식

| 방식 | 설명 | 예시 |
|------|------|------|
| **내장 방식** | `<style>` 태그 안에 직접 작성 | `<style> div { color:red; } </style>` |
| **링크 방식** | 외부 CSS 파일 연결 | `<link rel="stylesheet" href="main.css">` |
| **인라인 방식** | 요소에 직접 `style` 속성 사용 | `<div style="color:red;">` |
| **@import 방식** | 다른 CSS 파일을 불러옴 | `@import url("style.css");` |

※ `@import`는 렌더링 지연의 단점이 있어 실무에서는 권장되지 않음

---

# 🧩 선택자 속성과 우선순위

## 🔹 선택자 우선순위

| 선택자 | 점수 |
|--------|------|
| 인라인 스타일 | 1000 |
| ID 선택자 (`#id`) | 100 |
| 클래스 선택자 (`.class`), 속성, 가상클래스 | 10 |
| 태그 선택자 (`div`, `a`) | 1 |

→ 점수가 같을 경우 **나중에 선언된 스타일**이 우선 적용됨

## 🔹 상속 개념

- 일부 CSS 속성은 자식 요소로 자동 상속됨  
- 대표적으로 `color`, `font-family`, `line-height` 등  
- `inherit` 키워드로 강제 상속 가능

---

# 📦 CSS 속성 정리 (박스모델 중심)

## 🔹 박스모델 기본

| 속성 | 설명 |
|------|------|
| `margin` | 요소 외부 여백 |
| `padding` | 요소 내부 여백 |
| `border` | 테두리 |
| `width`, `height` | 콘텐츠 영역 크기 |
| `box-sizing` | 박스 크기 계산 방식 (`content-box`, `border-box`) |

## 🔹 표현 단위

- `px`, `em`, `rem`, `%`, `vw`, `vh` 등  
- `em`, `rem`은 상대 단위, 반응형에 유용

---

# 🎨 텍스트 관련 속성

| 속성 | 설명 |
|------|------|
| `color` | 글자 색 |
| `font-size` | 글자 크기 |
| `font-weight` | 글자 두께 |
| `line-height` | 행간 |
| `font-style` | 이탤릭 등 |

※ 글꼴에 띄어쓰기 있을 경우 `"돋움체"`처럼 따옴표로 묶기

---

# 🖼 배경 및 배치 관련 속성

## 🔹 배경

- `background-color`, `background-image`, `background-position` 등

## 🔹 위치(position)

| 속성 | 설명 |
|------|------|
| `static` | 기본값 |
| `relative` | 원래 위치 기준으로 이동 |
| `absolute` | 조상 기준으로 절대 위치 |
| `fixed` | 화면 기준 고정 |
| `z-index` | 쌓이는 순서 조절 (-값도 허용) |

※ `absolute`, `fixed`는 기본적으로 최소한의 width 사용

---

# 📐 레이아웃 - Flexbox

## 🔹 Container 속성

| 속성 | 설명 |
|------|------|
| `display: flex` | 수평 정렬 기본 |
| `flex-direction` | row / column |
| `flex-wrap` | 줄바꿈 여부 |
| `justify-content` | 주 축 정렬 |
| `align-items` | 교차 축 정렬 |
| `align-content` | 여러 줄 정렬 |

## 🔹 Item 속성

| 속성 | 설명 |
|------|------|
| `flex-grow` | 남는 공간 비율 |
| `flex-shrink` | 줄어들 비율 |
| `flex-basis` | 기본 크기 |
| `order` | 순서 변경 |

---

# ⚙️ 전환(transform) & 애니메이션

- `transition`: 부드러운 속성 변화 효과
- `transform`: 회전, 이동, 확대 등
- `animation`: keyframes 정의 → 반복 움직임 설정

---

