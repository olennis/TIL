### Mac OS 업데이트 후 git 에러

사용하던 맥북을 카탈리나에서 빅서로 업데이트를 했다. 평소에 til이나 알고리즘을 푸는 맥북은 다른 맥북이라 업데이트를 하고 난 후에 git을 사용할 일이 없었는데, 갑자기 깃을 쓰려고 하니 아래와 같은 에러가 뜨면서 git 관련 모든 명령어가 먹질 않았다.

```jsx
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```

이전에 ssh 설정을 통해 하나의 로컬에서 여러 깃헙 계정을 등록시켜놓은 상태였고, 처음엔 이 부분이 꼬였다고 생각했다. 그래서 과감히 로컬에 있는 파일들을 지운 후에 다시 하려고 했지만 그것부터가 안되는 상황이었다.

구글링을 통해 다음의 명령어를 알게 됐고

```jsx
xcode-select --install
```

터미널에서 입력 후 3-5분 정도가 소요된다.
