---
title:  "AJAX,GET,POST,FormData"
excerpt: "AJAX"

categories:
  - node.js
tags:
  - [자바스크립트,javascript,node.js]
  
toc: true
toc_sticky: true
 
date: 2022-03-23
last_modified_at: 2022-03-23
---

# 서버로 요청을 보내는 코드 
- ajax 요청 시 axios 라이브러리를 사용하는게 편하다. 
- html에 코드를 삽입해서 추가적인 스크립트를 추가한다. 
- get은 pomise를 지원하기 때문에 try catch를 사용한다. 
- post는 데이터를 함께 보낼 때 사용한다. 
- axios는 이미지나 다른 컨텐츠를 보내고 싶을 때는 formData에 담아서 보내야 한다. 

## encodeURIcontent , decodeURocontent
- 창에 한글을 입력했을 때 해석하지 못해서 오류가 나는 것을 처리해주기 위해서 사용한다. 

## HTML 태그에 데이터를 저장하는 방법 
- 서버의 데이ㅓ를 프론트엔드로 내려줄 떄 사용 
- 태그 속성으로 data-속성명
- 사용할 수 있는 데이터는 공개된 데이터만 사용이 가능하다. 
- 누구나 해당 데이터를 꺼내볼 수 있어야 하기 때문에 