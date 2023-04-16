# Testing Library

### 학습 키워드

* Jest
* Describe-Context-It 패턴
* React Testing Library



### Jest

거의 모든 것을 갖춘 테스팅 도구

#### 참고

* [BETTER SPECS](https://www.betterspecs.org/) → 베스트 프랙티스 모음 안되는 문법이 있지만 참고용
*  [Given-When-Then](https://megaptera.notion.site/Given-When-Then-c4b62b46710942a181a6d477e502e458)

```typescript
function add(x: number, y: number): number {
  return x + y;
}

test('add', () => {
  expect(add(1, 2)).toBe(3);
});
```

### Describe-Context-It 패턴

**Describe**에는 설명할 테스트 대상을 명시

**Context**는 테스트 대상이 놓인 상황을 설명

**It**은 테스트 대상의 행동을 설명

```typescript
const context = describe;

describe('add 함수는', () => {
    context('두 개의 양수가 주어졌을 때', () => {
        it('두 숫자의 합을 리턴한다.', () => {
            expect(add(1, 2)).toBe(3);
        });
    });
});
```

### React Testing Library

[React Testing Library 공식문서](https://testing-library.com/docs/react-testing-library/intro)

[jest-dom](https://testing-library.com/docs/ecosystem-jest-dom/)

```
 “F/E 테스트 = only React 컴포넌트 테스트”가 되는 상황은 최대한 피하는 게 좋다
 본질에 집중하지 못하고 너무 많은 테스트 코드를 작성할 위험이 있다.
```



```typescript
import {render, screen} from '@testing-library/react';
import Greeting from './Greeting';

test('Greeting', () => {
	render(<Greeting name='world' />);

    screen.getByText('Hello, world!');

    screen.getByText(/Hello/);

    expect(screen.queryByText(/Hi/)).not.toBeInTheDocument();
});
```
