---
layout: post
title: Today_Error_Record_01
categories: [error]
tags: [error]
description: >
  [Error] Today Error 
invert_sidebar: false
---
 # ⚠️ 오늘의 에러

 ### 1) params 못 받아오는 문제

***App.js***

```jsx
<Route
  path='/manager/consultantDetail/:id'
  element={<ConsultantDetail />}
/>
```

***ConsultantList.js***

```jsx
<td onClick={() =>
  navigate(`/manager/consultantDetail/${ele.consultantSeq}`)
}>
```

***ConsultantDetail.js***

```jsx
function ConsultantDetail() {
  const { id } = useParams();
```

📌 **useParams**로 url에 포함된 값을 뽑아올때는, Route의 url에 정의해둔 변수명과 같은 이름으로 받아와서 사용해야 한다. 

👉 상세페이지에서 url에 포함된 id값과 같은 것을 뽑아서 쓸 때는, 

List페이지에서 어떤 데이터이름으로 넘겨줬느냐에 상관없이, 
App.js와 같은 최상단에서 Route의 path URL에서 정의해둔 파라미터명을 그대로 가져와서 써야 한다..

👉 id값이라고 적어놓고는, 이 api는 seq를 이용해서 가져오니까 seq로 보내고 seq로 받아야지 만 생각해서 왜 파라미터를 제대로 받아오지 못하는지 헤매었다.. 빨리 구글링해서 useParams의 기본 쓰임새를 봤으면 더 빨리 해결했을 것 같다.

### 2) Error : TextField에서 name property값을 적절히 바꿔주지 않아서, Register버튼을 눌러도 아무런 반응이 없었음

👉 위에서만 데이터 컬럼에 맞게 key를 수정하고, 밑에는 name프로퍼티의 값을 바꿔주지 않아서 등록버튼도 작동이 안되고, api요청이 제대로 가지 않고 있었음. 그런데 console창에는 특별한 오류 문구가 나오지 않아서 더 찾기가 힘들었다.. 

👉 혼자서는 한참 못찾다가, 팀원한테 도움을 요청하고자 이런 상황이다, 라고 설명하는 과정에서 스스로 발견했음. 앞으로 혼자 오류를 찾아볼때 팀원한테 설명한다~ 라고 생각하고 찾아보는 시도도 해보도록 하자!