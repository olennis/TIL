### reset css?

웹 브라우저마다 다른 스타일로로 지정 되어 있는 기본 값을 초기화 하고, 이를 통해 다양한 웹 브라우저에서도 동일한 스타일이 적용되도록 함

### how to use?

- normalize
  - cdn 기법을 통해 링크로 적용 시킬 수 있음([https://cdnjs.com/libraries/normalize](https://cdnjs.com/libraries/normalize))
  - <head>태그 안에 스크립트 추가 적용
  - normalize의 특징은 기본 스타일은 남겨두고, 브라우저별로 다른 스타일만 초기화(모든 효과를 reset 하지 않음)
  - reset, nomalize의 차이
    - reset
      국내에서는 많은 기업들이 reset을 주로 사용하고 있기 때문에 익숙하다. reset은 요소의 기본스타일을 모두 초기화 시키기 때문에 내가 스타일을 주는 부분만 신경을 쓰면 되기 때문에 편리하다. 하지만 상위 또는 하위에 스타일을 적용했냐에 따라서 스타일이 달리 적용될 수 있는 복잡성이 단점으로 꼽힌다. 또 최근 업데이트버전이 없기 때문에 html의 속성이 변하게 된다면 적용이 되지 않는 점도 단점으로 꼽힌다.
    - nomalize
      nomalize는 리셋과 달리 기존 코드를 유지하고 이용한다는 측면에 있어서 reset보다는 코드의 충돌이 일어날 가능성이 적고, 간결해진다. 또한 reset과는 다르게 최근 v8.0이 나오는 등의 업데이트가 지속적으로 진행되고 있지만 아직 국내에서는 사용이 적어 reset보다는 사용하기 어색할 수 있다.
  ```jsx
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css" />
    </head>
    <body></body>
  </html>
  ```
- import
  - reset css 파일을 import시키는 방법으로도 사용 가능
