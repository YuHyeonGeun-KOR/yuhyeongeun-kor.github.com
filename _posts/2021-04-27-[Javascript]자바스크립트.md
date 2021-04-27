---
title:  "Javascript 튜토리얼"
excerpt: "자바스크립트를 처음으로 시작해 본다"

categories:
  - javascript
tags:
  - [code,javascript]

toc: true
toc_sticky: true
 
date: 2021-04-27
last_modified_at: 2021-04-27
---

# Javascript : 자바스크립트 실행방법과 실습환경

HTML을 만들고 자바스크립트를 실행하는데에는 메모장으로 파일을 만들면된다. 


``` javascript
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8"/>
    </head>
    <body>
        <script>
            alert('Hello world');
        </script>
    </body>
</html>

```

위의 언어에서 alert 문은 자바스크립트 언어이고 그 이외의 문장들은 HTML의 언어이다.

해당 파일을 메모장에 작성 후에 sample.html의 이름으로 파일형식은 모든파일로 저장을 하였다.

그리고 해당 파일을 실행 해보면 helloWorld 라는 문구가 출력되는 것을 브라우저 상에서 확인할 수 있었다. 

# 콘솔 사용법
브라우저상에서 F12를 누른면 개발자 도구가 등장하게 된다. 

해당 창에서 Console창에 자바스크립트 언어를 입력하면 즉석으로 확인할 수 있다. 

만약 메모장파일에 console.log('Hello world') 를 입력하게 되면 콘솔창에 Hello world 가 작성되고 이는 알림창을 지속적으로 띄우는 것은 번거로운 환경을 제공하기 때문에 이를 이용하지 않으려고 할때 사용한다. 