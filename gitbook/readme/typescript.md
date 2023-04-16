# TypeScript

### 학습 키워드

* REPL
* TypeScript
  * Interface vs Type
  * 타입 추론
  * Union Type vs Intersection Type
  * Optional Parameter

[TypeScript 공식문서](https://www.typescriptlang.org/ko/)

REPL(read-eval-print loop)

`npx ts-node` 로 간단히 실행하면 된다.

### Interface vs Type

[타입 별칭과 인터페이스의 차이점](https://www.typescriptlang.org/ko/docs/handbook/2/everyday-types.html#%ED%83%80%EC%9E%85-%EB%B3%84%EC%B9%AD%EA%B3%BC-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)

* 확장하기
  * Interface 확장하기 `extends`
  * Type 교집합을 통하여 타입 확장하기 `&`&#x20;
* 인터페이스에 새 필드를 추가할 수 있고 타입은 생성한 뒤에는 달라질 수 없다.
* 인터페이스는 오직 객체의 모양을 선언하는 데에만 사용되며, 기존의 원시 타입에 별칭을 부여하는 데에는 사용할 수는 없다.
* **개인적 선호**에 따라 인터페이스와 타입 중에서 선택할 수 있으며, 필요하다면 **TypeScript가 다른 선택을 제안**할 것입니다. 잘 모르겠다면, **우선 interface를 사용하고 이후 문제가 발생하였을 때 type을 사용**

### 타입 추론

* [타입 추론](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html#%ED%83%80%EC%9E%85-%EC%B6%94%EB%A1%A0-types-by-inference)  &#x20;

### Union Type

* [Union Type](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html#%EC%9C%A0%EB%8B%88%EC%96%B8-unions)
  * ex) [React Types](https://github.com/facebook/react/blob/main/packages/shared/ReactTypes.js)&#x20;

### Intersection Type

* [교집합](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes-func.html#%EA%B5%90%EC%A7%91%ED%95%A9)

```typescript
type Combined = { a: number } & { b: string };
type Conflicting = { a: number } & { a: string };
```

Combined은 a와 b 두 개의 속성을 가지게 된다.

Conflicting은 `Conflicting.a: number & string`가 된다.

* [Intersection Types](https://www.typescriptlang.org/docs/handbook/2/objects.html#intersection-types)

```typescript
type Person = {
  name: string;
  age: number;
};

type Subject = {
  math: number;
  science: number;
};

type Student = Person & Subject;

let student: Student;

person = { name: 'heesu', age: 17, math: 90, science: 95 };
```

#### enerics, Utility Types, and Tips

* [Generics](https://www.typescriptlang.org/docs/handbook/2/generics.html)
* [Utility Types](https://www.typescriptlang.org/docs/handbook/utility-types.html)
* [**더 좋은 타입스크립트 프로그래머로 만드는 11가지 팁**](https://velog.io/@lky5697/11-tips-that-help-you-become-a-better-typescript-programmer)



오래된 라이브러리의 경우 d.ts 파일만 따로 패키지로 제공

* [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped)
  * [DefinitelyTyped/types](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types)
  * [DefinitelyTyped/types/react](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/react)
