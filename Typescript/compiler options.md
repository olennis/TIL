```jsx
{
    "compilerOptions": {
        "strict": true,
        "module": "commonjs",
        "moduleResolution": "node",
        "lib": ["es2015","es2016","es2017","es2018","es2019","es2020"],
        "target": "ES5",
        "outDir": "./dist",
        "esModuleInterop": true
    },
    "exclude": ["node_modules"],
    "include": ["src/**/*"]
}
```

- strict : 말 그대로 엄격하게 타입을 검사, true로 해야 타입스크립트를 쓰는 이유가 있다.
- module : 웹브라우저에서 동작 시는 amd, Node에서 동작 시는 commonjs
- moduleResolutionmodule : 키의 값이 commonjs면 node로 설정하고 amd이면 classic으로 설정
- lib : 몇 버전까지의 자바스크립트를 사용할 수 있게 할지 적는다.(이런 기능 덕분에 바벨 대신 ts를 쓰면 됩니다.)
- target : 해당 버전으로 트랜스파일 된다. 대부분 ES5로 설정.
- outDir : 타입스크립트가 자바스크립트로 컴파일될때 저장되는 폴더의 url 설정 *ex, tsc 명령어를 입력하면 ./dist 폴더에 변환된 js 파일들이 생김*
- esModuleInteroptrue : true로 설정 해놓으면 export default가 없는 라이브러리도 * as 를 사용하지 않고 불러올 수 있다.
    
    ```jsx
    *import * as React from 'react;//(false)
    import React from 'react;//(true)*
    ```
    
- include , exclude: include는 컴파일 대상, exclude는 컴파일에 제외되는 대상을 말한다.
    - **src/****/*.ts**은 src 디렉터리는 물론 src의 하위 디렉터리에 있는 모든 파일을 컴파일 대상으로 포함한다는 의미**

참고블로그 : [https://velog.io/@chkim132/TS-타입스크립트](https://velog.io/@chkim132/TS-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8)