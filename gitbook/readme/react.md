# React

### 학습 키워드

* React란?
* React 컴포넌트
* React 리렌더링
* IoC(Inversion of Control)
* Library vs Framework



### React란?

[React 공식문서](https://ko.reactjs.org/)

[**React Beta 문서**](https://beta.reactjs.org/) **- 권장**

#### 리액트의 특징

* 가상 돔
* 단방향 데이터 바인딩
* JSX
* 선언형 프로그래밍
* 컴포넌트 기반



React로 작업하는 프로세스

* [Thinking in React](https://beta.reactjs.org/learn/thinking-in-react)를 참고 [한국어](https://ko.reactjs.org/docs/thinking-in-react.html)
  * 1단계: UI를 컴포넌트 계층 구조로 나누기
  * 2단계: React로 정적인 버전 만들기
  * 3단계: UI state에 대한 최소한의 (하지만 완전한) 표현 찾아내기
  * 4단계: State가 어디에 있어야 할 지 찾기
  * 5단계: 역방향 데이터 흐름 추가하기

[React 코어 개발자가 쓴 React에 대한 이해를 돕는 글](https://overreacted.io/ko/react-as-a-ui-runtime/) (필독!)



### React 리렌더링

* [React는 컴포넌트를 언제 다시 리렌더링 할까요?](https://velog.io/@surim014/react-rerender)
* [왜 리액트에서 리렌더링이 발생하는가.](https://medium.com/@yujso66/%EB%B2%88%EC%97%AD-%EC%99%9C-%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%97%90%EC%84%9C-%EB%A6%AC%EB%A0%8C%EB%8D%94%EB%A7%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94%EA%B0%80-74dd239b0063)
* [React 렌더링 동작에 대한 (거의) 완벽한 가이드](https://velog.io/@superlipbalm/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior)



* **컴포넌트의 상태**가 변경될 때마다 렌더링을 예약
  * 렌더링 **예약**은 이 작업이 즉시 수행되지 않는다는 것을 의미 (적합한 순간을 찾는다)
* 컴포넌트의 **render 함수가 호출**된다는 것을 의미할 뿐만 아니라, **props 변경 여부와 관계없이 모든 하위 컴포넌트들이 리렌더링** 된다는 것을 의미
* 제대로 구조화되어 있지 않은 경우, **상위 노드를 업데이트하면 모든 자식들의 render 함수를 실행**해야 하기 때문에 예상보다 훨씬 더 많은 자바스크립트를 실행하게 될 수 있다.

#### props가 변경될 때, React 컴포넌트가 업데이트되지 않는 이유 <a href="#props-react" id="props-react"></a>

* props가 `setState`를 통해 올바르게 업데이트되지 않음
* props에 대한 참조가 동일하게 유지

#### 리렌더링을 최적화하는 방법 <a href="#undefined" id="undefined"></a>

* 컴포넌트의 업데이트 시점 제어하기
  * React.memo
  * key 속성을 설정하기
* 컴포넌트의 구조를 데이터가 사용되는 곳에 더 가깝게 배치



### IoC(Inversion of Control)

제어의 역전 예전 자바 스프링을 배웠을 때 많이 들었는데 정확히 이해를 못했었다..\
**Framework의 주요한 특징**이고 **React는 IoC를 통해 상태와 업데이트가 얽힌 복잡한 상황을 간단히 선언형 UI로 구성** 한다고 한다 아직 자세히는 이해가 안가지만 좀 더 공부해서 이해를 해둬야 겠다..

### Library vs Framework

예전 강의에서 들었던 기억으로는 Framework은 반제품으로 비유를 해주셨고 Library는 망치나 톱등 제품을 만들 때 쓰는 도구로 비유를 해주셨다.

Framework는 뼈대나 기반구조를 뜻하고, 제어의 역전 개념이 적용된 대표적인 기술이다.

Library는 단순 활용가능한 도구들의 집합을 말한다.

Framework 와 Library의 차이점은 제어 흐름에 대한 주도성이 누구/어디에 있는가 있다. 즉, 어플리케이션의 흐름을 누가 쥐고 있느냐에 달려 있다.

Framework는 전체적인 흐름을 스스로 쥐고 있으며 사용자는 그 안에서 필요한 코드를 넣는다 반면 Library는 사용자가 전체적인 흐름을 만들며 Library를 가져다 쓰는 것이라고 할 수 있다.

