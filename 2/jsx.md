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



\_jsx&#x20;



VDOM(Virtual DOM)
