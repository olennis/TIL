`[Vue warn]: The client-side rendered virtual DOM tree is not matching server-rendered content. This is likely caused by incorrect HTML markup, for example nesting block-level elements inside <p>, or missing <tbody>. Bailing hydration and performing full client-side render.`

### 1st try

```jsx
<no-ssr> 태그 추가
>> nuxt version이 업그레이드 되면서
<client-only> 태그로 변경

위의 태그들 중 하나로 감싸면, 카카오맵 api를 받아올 수 없는 문제 발생
```

### 2nd try

```jsx
//node_modules/vue/dist/vue.esm.js

function hydrate (elm, vnode, insertedVnodeQueue, inVPre) {
    var i;
    var tag = vnode.tag;
    var data = vnode.data;
    var children = vnode.children;
    inVPre = inVPre || (data && data.pre);
    vnode.elm = elm;

    // Add the following lines:
    console.log('elm', elm)
    console.log('vnode', vnode)
    console.log('inVpre', inVPre)
    // ...

디버깅 하는 법이라고 했지만, 콘솔로그가 실행이 되지 않아 정확한 사용법을 모르겠다
```

###(진행중)
