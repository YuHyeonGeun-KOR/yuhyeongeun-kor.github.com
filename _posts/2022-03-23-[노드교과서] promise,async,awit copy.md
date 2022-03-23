---
title:  "[Nods.js 교과서] 프로미스, async/await"
excerpt: "프로미스와 async/await"

categories:
  - node.js
tags:
  - [자바스크립트,javascript,node.js]
  
toc: true
toc_sticky: true
 
date: 2022-03-23
last_modified_at: 2022-03-23
---

# 프로미스
- 내용이 실행은 되었지만 결과를 아직 반환하지 않은 객체
- resolve 리턴결과를 반환하지 않고 들고있다가 then을 붙이면 그때 결과를 받아올 수 있다. 
- reject 리턴값은 catch, finaly는 무조건 실행한다. 

# async/await
- 에이싱크와 어웨이트
- 프로미스 지옥을 벗어날 수 없을까
- async함수 안에 await으로 then을 대체한다. , 실행순서 오른쪽에서 왼쪽
- async 도 promise 문법이기 때문에 리턴값을 받기 위해서는 then으로 받거나 await로 받아야 한다. 
- 실패할 경우에 대한 조작은 try , catch문으로 감싸서 따로 처리해줘야 한다. 
- for await 로 프로미스들의 결과값에 대한 반복문을 사용할 수 있다. 
