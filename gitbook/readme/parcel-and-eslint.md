# Parcel & ESLint

### 학습 키워드

* Bundler(번들러)
  * Parcel
* Lint(린트)
  * ESLint



### Parcel

[Parcel 공식문서](https://parceljs.org/)

Zero Configuration 번들러, 지금은 build tool로 얘기하고 있다.

**참고**

* [https://github.com/ahastudio/til/tree/main/parcel](https://github.com/ahastudio/til/tree/main/parcel)
* [https://github.com/ahastudio/til/tree/main/vite](https://github.com/ahastudio/til/tree/main/vite)

package.json 파일에 source 속성 추가

```json
"source": "./index.html",
```

```json
npm i -D parcel-reporter-static-files-copy
touch .parcelrc
```

```json
{
  "extends": ["@parcel/config-default"],
  "reporters":  ["...", "parcel-reporter-static-files-copy"]
}
```



빌드 + 정적 서버 실행

```sh
npx parcel build

npx servor ./dist
```

### ESLint

* 스타일 통일
* 잠재적 문제 발견
* 베스트 프랙틱스 추천

#### .vscode/settings.json파일 추가

```json
{
    "editor.rulers": [
        80
    ],
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "trailing-spaces.trimOnSave": true
}
```
