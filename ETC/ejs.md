### ejs tag

- `<%` 스크립틀릿 태그 태그 안에 javascript 코드 작성, 줄 바꿈시 행마다 태그로 감싸줘야 함
- `<%=` 값 출력(html escaped)
- `<%-` 값 출력(html unescaped)
- `<%#` 주석
- `%>` 엔딩 태그

### 조건문

```jsx
<% if (num > 0) { %>
  <p>0보다 크다</p>
<% } else { %>
  <p>0보다 작거나 같다</p>
<% } %>
```

### 반복문

```jsx
<% for(let i = 0; i < 5; i++){ %>
   <p>Hello World</p>
<% }; %>
 
<% samples.forEach(function(sample){ %>
  <%- include('../../partials/sample/sample.ejs', {
    data: sample
  }); %>
<% }); %>
```
