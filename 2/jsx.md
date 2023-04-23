# JSX

### 학습 키워드

* React에서 JSX를 사용하는 목적
* Syntactic sugar
* React.createElement
* React Element
* React StrictMode
* VDOM(Virtual DOM)이란?
  * DOM이란?
  * DOM과 Virtual DOM의 차이
* Reconciliation(재조정) 과정은 무엇인가?



### 강의 내용

* XML-like syntax extension to ECMAScript
* 문자열도, HTML도 아니고 JSX라 하며 JavaScript를 확장한 문법
  * [“JSX 없이 React 사용하기”](https://ko.reactjs.org/docs/react-without-jsx.html)&#x20;
  * [“ES6 없이 React 사용하기”](https://ko.reactjs.org/docs/react-without-es6.html)



[Babel](https://babeljs.io/repl)로 확인 가능

* “Presets”에서 “**react**”를 체크 or “Plugins”에서 “**@babel/plugin-transform-react-jsx**”를 추가
* **/\* @jsx \{{customName\}} \*/** 주석을 추가하면 "**customName**"을 사용할 수 있다.



JSX 두개 이상의 엘리먼트는 무조건 하나의 엘리먼트로 감싸져 있어야 한다

* fragment 태그
* `add(1, 2) add(3, 4)`와 같다고 볼 수 있다. `add(1, 2); add(3, 4);`로 변경이 되어야 한다.
* Virtual DOM에서 컴포넌트 변화를 감지해 낼 때 효율적으로 비교할 수 있도록 **컴포넌트 내부는 하나의 DOM 트리 구조로 이루어져야 한다**는 규칙

Browser html parser가 생각남

JSX는React.createElement(component, props, ...children)  syntax sugar



JSX 대신 React.createElement를 써서 React Element 트리를 갱신하는데 쓸 수 있다.



\_jsx 17버전 jsx-runtime



preact h()



VDOM(Virtual DOM)



### React에서 JSX를 사용하는 목적

* React.createElement(component, props, ...children) 함수에 대한 문법적 설탕을 제공
* JSX는 JavasScript를 XML과 비슷하게 확장한 문법, JavaScript 코드 안에서 UI 관련 작업을 할 때 시각적으로 더 도움이 된다.
  * 또한 React에 도움이 되는 에러 및 경고 메세지를 표시할 수 있게 해준다.



### Syntactic sugar

Vue를 공부할 때 처음으로 들어본 말이다. vue는 양방향 데이터 바인딩이 가능해서 v-model이라는 syntax sugar를 사용한다.

syntac sugar란 문법 설탕이라 번역되고, 읽거나 사용하는 사람들에게 편하게 디자인된 문법이라는 뜻을 갖고 있다.

위에서 배운 JSX도 React.createElement 함수에 대한 syntax sugar이다.



### React.createElement

React 요소를 만들 수 있다. JSX 작성의 대안으로 사용된다.

```javascript
React.createElement(
  type, // tag name string | React component(a function, a class, or a special component like Fragment)
  [props], // object or null
  [ ... children] // Zero or more child nodes
);

```

[https://react.dev/reference/react/createElement](https://react.dev/reference/react/createElement)



### React Element

브라우저 DOM 엘리먼트와 달리 React 엘리먼트는 일반 객체이며(plain object) 쉽게 생성할 수 있다. React DOM은 React 엘리먼트와 일치하도록 DOM을 업데이트한다.

[https://ko.legacy.reactjs.org/docs/rendering-elements.html](https://ko.legacy.reactjs.org/docs/rendering-elements.html)



### React StrictMode

* 개발 초기에 구성 요소의 일반적인 버그를 찾을 수 있다.
* 내부 구성 요소 트리에 대한 추가 개발 동작 및 경고를 활성화하는 데 사용
  * 구성 요소는 불순한 렌더링으로 인한 버그를 찾기 위해 [추가 시간을 다시 렌더링](https://react.dev/reference/react/StrictMode#fixing-bugs-found-by-double-rendering-in-development)
  * 구성 요소는 효과 정리 누락으로 인해 발생하는 버그를 찾기 위해 [추가 시간 동안 효과를 다시 실행](https://react.dev/reference/react/StrictMode#fixing-bugs-found-by-re-running-effects-in-development)
  * [더 이상 사용되지 않는 API 사용에 대해](https://react.dev/reference/react/StrictMode#fixing-deprecation-warnings-enabled-by-strict-mode) 구성 요소를 확인



### VDOM(Virtual DOM)이란?

#### DOM이란?

* DOM(문서 객체 모델, The Document Object Model) 은 HTML, XML 문서의 프로그래밍 interface 이다.
* DOM은 문서의 구조화된 표현을 제공하며 프로그래밍 언어가 DOM 구조에 접근할 수 있는 방법을 제공한다.
* DOM 은 **동일한 문서를 표현하고, 저장하고, 조작하는 방법을 제공**한다. DOM 은 웹 페이지의 객체 지향 표현이며, 자바스크립트와 같은 스크립팅 언어를 이용해 DOM 을 수정할 수 있다.

[https://developer.mozilla.org/ko/docs/Web/API/Document\_Object\_Model/Introduction](https://developer.mozilla.org/ko/docs/Web/API/Document\_Object\_Model/Introduction)



#### DOM과 Virtual DOM의 차이

* Virtual DOM (VDOM)은 UI의 가상적인 표현을 메모리에 저장 (실제 저장을 하는 느낌보다는 가상 객체를 생성한다. )하고 ReactDOM과 같은 라이브러리에 의해 DOM과 동기화하는 프로그래밍 개념
* 이 방식이 React의 선언적 API를 가능하게 한다. 원하는 UI의 상태를 알려주면 DOM이 그 상태와 일치하도록 하고 이러한 방식은 앱 구축에 사용해야 하는 어트리뷰트 조작, 이벤트 처리, 수동 DOM 업데이트를 추상화한다.
* Virtual DOM은 특정 기술이라기보다는 패턴에 가깝기 때문에 사람들마다 의미하는 바가 다르다.

[https://ko.legacy.reactjs.org/docs/faq-internals.html](https://ko.legacy.reactjs.org/docs/faq-internals.html)



처음 프론트엔드 개발자로 면접 준비로 VDOM을 공부했을 때는 막연히 브라우저 렌더링을 더 적게 할 수있게 VDOM이 도와준다고 공부를 했었다. 특히 Reflow(Layout), Repaint(paint) 과정이 오래 걸리고 이 부분을 적게 실행할 수 있어 성능 최적화 할 수 있다 말했고 지금 기억해 보면 면접관이 정말로 VDOM을 사용하면 성능이 좋아지냐는 말에 정확히 대답하지 못했던 기억이 있다.\
\
브라우저 자체에서도 더티 비트 시스템을 사용해서 최적화된 방법을 사용하고 코드를 어떻게 수정하고 사용하느냐에 따라서 최적화가 진행될 수 있다.\
\
아직도 정확히 뭐라 대답해야 할지 모르겠다.. 좀 더 조사 및 공부를 진행해서 정리해둬야겠다.

[https://yozm.wishket.com/magazine/detail/1338/](https://yozm.wishket.com/magazine/detail/1338/)



### Reconciliation(재조정) 과정은 무엇인가?

위에 작성한것처럼 VDOM과 DOM을 동기화하는 프로그래밍 개념이다.\
state나 props가 갱신되면 render() 함수는 새로운 React 엘리먼트 트리를 반환한다. 만들어진 트리에 맞게 가장 효과적으로 UI를 갱신할 필요가 있다.



### 비교 알고리즘 (Diffing Algorithm) <a href="#the-diffing-algorithm" id="the-diffing-algorithm"></a>

* 엘리먼트의 타입이 다른 경우
  * 두 루트 엘리먼트의 타입이 다르면, 이전 트리를 버리고 완전히 새로운 트리를 구축
* DOM 엘리먼트의 타입이 같은 경우
  * 두 엘리먼트의 속성을 확인하여, 동일한 내역은 유지하고 변경된 속성들만 갱신
* 같은 타입의 컴포넌트 엘리먼트
  * 새로운 엘리먼트의 내용을 반영하기 위해 현재 컴포넌트 인스턴스의 props를 갱신

#### Keys <a href="#keys" id="keys"></a>

자식들이 key를 가지고 있다면 key를 통해 기존 트리와 이후 트리의 자식들이 일치하는지 확인
