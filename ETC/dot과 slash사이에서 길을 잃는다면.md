```jsx
import 어떤 것 from '../../../../../../../../ ......'
```

위의 예시는 조금 극단적이긴 하지만 개발을 하다 보면 흔히 볼 수 있는 작성법이다.

위와 같은 형식은 크게 두 가지의 문제가 있는데,

1. 코드의 길이가 길어져 가독성이 떨어진다.
2. ../이 길어진다면 어디에서부터 시작인지를 알기가 어렵고, 수정이 필요 할 때 불편하다.

회사 프로젝트에서 코드를 분리하는 작업을 하다보니 뎁스가 점점 깊어지게 되었고, 닷과 슬래쉬가 날뛰고 있었다. 내가 어디에서 부터 이 요소를 import하는지 파악하기가 어렵기도 하고 어떤것이 공용으로 쓰는지 혹은 분리된 코드만 사용하는지를 알아야 업무가 더 편할 것 같아 상대경로에서 절대경로로 변경하였다.

내가 기존에 사용하던 js 환경에서는 단순히 path를 설정하기만 한 것 같은데, ts에 CRA 환경이 겹치니 ts를 컴파일 할 때, 내가 설정했던 path가 초기화 되는 이슈가 있었다. 구글링을 해보니 eject를 사용해 webpack 설정을 바꿔줘야 했지만 이렇게 되면 CRA를 사용하는 의미가 없다고 했다. 그래서 eject를 사용하지 않게 해주는

`craco(create react app configuration override)`를 설치했다.

### craco 설치

```jsx
$yarn add @craco/craco
$yarn add craco-alias
```

설치를 마치고 해야 할 일은

1. root에 craco.config.js 생성
2. root에 tsconfig.paths.json 생성
3. tsconfig.json 수정
4. package.json 수정

이 있으며, 순서는 딱히 상관이 없다.

우선은 craco를 적절히 사용하기 위해

```jsx
//craco.config.js
const CracoAlias = require("craco-alias");
module.export = {
  plugins: [
    {
      plugin: CracoAlias,
      options: {
        source: "tsconfig",
        tsConfigPath: "tsconfig.path.json",
      },
    },
  ],
};
```

과 같이 craco.config.js를 설정 해 주었다.

이후에 tsconfig.paths.json 을 생성해

```jsx
//tsconfig.paths.json
{
  "compilerOptions": {
    "baseUrl": "./",
    "paths": {
      "~src/*": ["src/*"],
			//'축약어' : ['실제 경로']
    }
  }
}
```

와 같이 설정해 주면 되는데, 구글링을 해보니 굳이 이렇게 따로 파일을 생성할 필요가 없이 tsconfig.json 파일을 수정하는 방법도 있다고 한다. tsconfig.json의 compilerOptions 값에서 똑같이 설정하면 되는 것 같지만(실제로 해보진 않았다.)

tsconfig.paths.json을 만들어 관리하는 것이 가독성이 더 좋다고 한다.(.?)

어쨌든 tsconfig.json에 extends 옵션을 주고

```jsx
//tsconfig.json
{
	"extends" : "./tsonfig.paths.json"
	"compilerOptions":{
		...
	}
}
```

package.json의 스크립트를 craco로 수정한다.

```jsx
//package.json
	"scripts": {
    "start": "craco start",
    "build": "craco build",
    "test": "craco test",
  },
```

220402 추가
업무에 적용하기 위해

```jsx

{
  "compilerOptions": {
    ...
      "~common/*": ["src/domain/common/*"]
    }
  }
}

```

위와 같이 적용 하여 보았지만 ~common이 동작하지 않는다. 원인이 뭘까..
