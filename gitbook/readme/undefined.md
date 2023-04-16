# 개발 환경 세팅

### 학습 키워드

* Node.js
* NPM(Node Package Manager)
  * package.json / package-lock.json
  * node\_modules
  * npx
* ES Modules vs CommonJS



현재는 nvm을 사용하고 있는데 최근에 나온 fnm(Fast Node Manager)을 사용할 예정

[fnm (Fast Node Manager)](https://fnm.vercel.app/)

Node.js LTS(Long Term Support)을 이용

#### .gitignore

`node_modules or node_modules/ or /node_modules/`

* [https://www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore)
* [https://github.com/github/gitignore/blob/main/Node.gitignore](https://github.com/github/gitignore/blob/main/Node.gitignore)

#### dependencies & devDependencies

* dependencies - 프로그램에서 직접 쓰는 것들이 들어 간다.
* devDependencies - 개발환경에서 쓰는 것들이 들어 간다. 주로 툴(도구)로서 설치되는것들이 들어 간다.&#x20;
  * (ex. 테스트프레임워크, prettier, eslint)
* peerDependencies - 실제로 패키지에서 직접 require(import) 하지는 않더라도 호환성이 필요한 경우 명시

#### package.json / package-lock.json

npx -  npm에서 제공해주는 하나의 도구

* 패키지를 임시 설치 및 실행
* npm으로 설치할 명령어를 줄여줌
* 다른 버전의 노드 실행 가능

좀 더 자세히 -> [https://basemenks.tistory.com/232](https://basemenks.tistory.com/232)



### ES Modules vs CommonJS

#### ES Modules&#x20;

* 모듈로더를 비동기 환경에서 실행하고, import export 구문을 찾아서 파싱한다.
* 따라서 ES modules는 실행해보지 않아도 import, export 에러를 감지할 수 있다.
* 더 이상 import 할 것이 없을 때까지 import 를 찾는다.
* package.config의 "type": "module" 로 set 해주어야한다. (기본값이 아니다.)
* top-level await가 가능하다.

#### CommonJS

* default 값이다.
* require가 동기로 이루어지므로 promise나 callback을 return 하지 않는다.
* 따라서 CommonJS는 실행해보아야 import, export 에러를 감지할 수 있다.
* top-level await가 불가능하다.

#### ES Modules Code

```javascript
import esm from 'esm';
import { func } from 'esm';

export const esm = 'esm';
export default func = () => {};
```

#### CommonJS Code&#x20;

```javascript
const module = require('cjs');
const { func } = require('cjs');

module.exports = 'cjs';
module.exports.func = () => {};
```



