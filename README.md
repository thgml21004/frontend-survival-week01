# Node 세팅
* * *

```
# Node 설치 여부 확인
node -v

# NVM 설치 여부 확인
nvm --version

# 설치 안되어 있으면 NVM 설치
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash

# 환경 변수 새로고침 ( bashrc 안된다면 zshrc - mac OS 기본 쉘에 따라서)
source ~/.bashrc
source ~/.zshrc

# Node 버전 확인 및 설치 가능 버전
nvm ls-remote

# 특정 버전 설치(20버전 설치함)
nvm install 20

# Node 버전 확인
node -v
```

# TypeScript 세팅
* * *

```
# my-app 폴더 생성
mkdir my-app

# 코딩 프로그램 열기 (vsCode / webstorm)

# npm 패키지 설치 (package.json 파일 생성 됨)
npm init -y

# .gitignore 파일 생성
# 복붙
/node_modules/
/dist/
.parcel-cache

# TypeScript 도구 설치
npm i -D typescript

# 타입스크립트 컴파일러 초기화 (tsconfig.json 파일 생성 됨)
npx tsc --init

# tsconfig.json 파일에서 jsx 주석 풀기
"jsx": "react-jsx",

```

# ESLint 설정
* * *

```
# ESLint 설치 (^8.32.0 버전 설치 함)
npm i -D eslint

# 설정 초기화 (eslint.config.mjs 파일 생성 됨)
npx eslint --init

# 설정 초기화 실행 시 선택한 답
problems
javascript => esm
React
Yes => typescript
Browser
Yes
npm

# .eslintignore 파일 생성
/node_modules/
/dist/
.parcel-cache
```

# React 설치
* * *

```
# 리액트 설치
npm i react react-dom

# types 도구 설치
npm i -D @types/react @types/react-dom
```

# 테스팅 도구 설치
* * *

```
# 테스팅 도구 설치
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom@5.16.4

# jest.config.js 파일 생성 (경로 안에 내용 복붙)
https://github.com/megaptera-kr/textbook/blob/main/usestore-ts-example/jest.config.js
```

# Parcel 설치
* * *

```
npm i -D parcel
```

# 명령어 세팅
* * *

```
# package.json 파일 명령어 수정 (scripts 명령어 복붙)
  "scripts": {
    "start": "parcel --port 8080",
    "build": "parcel build",
    "check": "tsc --noEmit",
    "lint": "eslint --fix --ext .js,.jsx,.ts,.tsx .",
    "test": "jest",
    "coverage": "jest --coverage --coverage-reporters html",
    "watch:test": "jest --watchAll"
  },

# "main": "index.js" > "source": "index.html"로 변경

# 파일생성 및 코드 작성
index.html
src/main.tsx
src/App.test.ts
```

# 현재 버전에 맞게 수정해야 되는 부분
* * *

```
# package.json lint 명령어 수정
# 기존 {js,jsx,ts,tsx}를 체크해야되지만 파일이 생성되어 있지 않다면 오류가 나기 때문에 생성된 파일의 확장자만 작성 
"lint": "eslint --fix src/**/*.{ts,tsx}",

# jest.config.js 파일에서 ./jest.setup 삭제

# eslint.config.mjs 파일에서 세팅 변경
import globals from 'globals';
import pluginJs from '@eslint/js';
import tseslint from 'typescript-eslint';
import pluginReact from 'eslint-plugin-react';

export default [
  { files: ['**/*.{js,mjs,cjs,ts,jsx,tsx}'] },
  { languageOptions: { globals: globals.browser } },
  pluginJs.configs.recommended,
  ...tseslint.configs.recommended,
  pluginReact.configs.flat.recommended,
  {
    settings: {
      react: {
        version: 'detect',
      },
    },
    rules: {
      'react/react-in-jsx-scope': 'off',
    },
  },
];
```


# 명령어 실행
* * *

```
# test 실행
npm run test

# eslint 실행
npm run lint

# 화면 실행
npm run start

# 빌드 실행
npm run build
```


