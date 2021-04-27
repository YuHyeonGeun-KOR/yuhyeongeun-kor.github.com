---
title:  "Javascript 의 기초"
excerpt: "자바스트립트에서 제공하는 명령어와 문법들을 알아보자"

categories:
  - javascript
tags:
  - [code,javascript]

toc: true
toc_sticky: true
 
date: 2021-04-27
last_modified_at: 2021-04-27
---

# Javascript : 자바스크립트 의 기초
자바스크립트에서 제공하는 math의 여러가지 함수들을 알아보았다.

``` javascript
Math.pow(3,2);       // 9,   3의 2승 
Math.round(10.6);    // 11,  10.6을 반올림
Math.ceil(10.2);     // 11,  10.2를 올림
Math.floor(10.6);    // 10,  10.6을 내림
Math.sqrt(9);        // 3,   3의 제곱근
Math.random();       // 0부터 1.0 사이의 랜덤한 숫자
```

## 문자열
``` 
alert('coding');
alert("coinng");
```
브라우저에게 알릴때 '' , ""로 감싸져 있는 부분은 문자열이라는 것을 알리는 것이다.
```
alert('coinng'");
```
위 처럼 작성이 되어도 '까지 문자열로 인식하고 오류없이 출력된다.

```
alert('coinng\'");
```
위의서의 \는 해석되어 지기를 \바로뒤에 나오는 문자 1개를 문자열로 인식하겠다 라는 것을 의미한다.

```
//문자와 문자를 더할떄는 아래와 같이
alert("coding"+" everybody");
//결과 : coding everybody

//문자의 길이를 구할때는 문자 뒤에 .length 를 붙입니다.
alert("coding everybody".length);
//결과 : 16
```

## 변수의 사용법
```
var a = 1;
alert(a+1);  //2
 
var a = 2;
alert(a+1);  //3

var first = "coding";
alert(first+" everybody");

//변수 a에 coding ,변수 b에 everybody를 활당하는 방법은 아래와 같다.
var a = 'coding', b = 'everybody';
alert(a);
alert(b);
```

## === , == 의 사용법
```
//== 사용하기

alert(1==2)             //false
alert(1==1)             //true
alert("one"=="two")     //false 
alert("one"=="one")     //true

//===사용하기
alert(1=='1');              //true
alert(1==='1');             //false
```

밑의 경우에는 좌변과 우항이 엄격하게 같다라는 의미이고 이는 변수의 자료형까지 일치하는지 확인하기 때문에 아래의 문장 같은 경우에는 숫자 1 과 문자열 1은 데이터의 자료형이 일지 하기 않기 때문에 false가 출력된다. 

그렇다면 참과 거짓의 관계에서는 어떠한지 알아보았다.

```
alert(null == undefined);       //true
alert(null === undefined);      //false
alert(true == 1);               //true
alert(true === 1);              //false
alert(true == '1');             //true
alert(true === '1');            //false
 
alert(0 === -0);                //true
alert(NaN === NaN);             //false
```
null이라는 것은 값이 없다라는 것이고 undefined는 값이 정의되지 않았다는 것이다. 



## 조건문 예시 
다른 언어와 구조적인 차이가 크지 않기에 아래의 코드를 확인하면서 어떻게 사용되는지를 확인해 보려고 한다. 


```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8"/>
</head>
<body>
    <script>
        id = prompt('아이디를 입력해주세요.');
        if(id=='egoing'){
            password = prompt('비밀번호를 입력해주세요.');
            if(password==='111111'){
                alert('인증 했습니다.');
            } else {
                alert('인증에 실패 했습니다.');
            }
        } else {
            alert('인증에 실패 했습니다.');
        }
    </script>
</body>
</html>
```


## 함수(fuction)

## 추가될 예정입니다. 