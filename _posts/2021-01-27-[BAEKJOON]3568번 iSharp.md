---
title:  "BOJ 3568 : iSharp"
excerpt: "i#의 변수 선언문이 주어진다. 이때, 각각의 변수의 오른편에 있는 변수형을 모두 왼쪽으로 옮기고, 한 줄에 하나씩 선언하는 프로그램을 작성하시오."

categories:
  - BaekJoon
tags:
  - [code,Python]

toc: true
toc_sticky: true
 
date: 2021-01-27
last_modified_at: 2020-01-27
---

# BOJ 3568 : iSharp 문제

이번 문제를 해결하기 위해서 다음의 수순으로 해결해보려고 하였다.    

1. 입력을 공백기준으로 입력을 받고 첫번째 인자는 기본변수형이다.

2. 입력의 마지막에 ; 기호를 지운다.

3. 다음의 부터 나오는 입력의 문자열을 분석하여 *,[],&가 나올떄 마다 해당 문자열에 기호를 지우고 결과인 result에 해당 기호를 추가한다.

4. 기호를 전부 지우면 변수명만 남게되고 해당 변수명을 따로 저장한다. 

5. 따로 저장한 결과를 연결하여 마지막에 ;를 추가하여 리스트에 담는다.

6. 리스트를 출력한다. 


위의 순서로 코드를 구현하였고 구현한 코드는 아래와 같다. 

``` py
import sys 
input = sys.stdin.readline


declare = list(input().split())
order = []
declare[-1] = declare[-1].replace(";","")

for i in range(1, len(declare)):
    result = declare[0]

    declare[i] = declare[i].replace(",","",1)
    look = 0 
    while look >= len(declare[i]) :
        if "&" in declare[i]:
            result += "&"
            declare[i] = declare[i].replace("&","",1)
            
        elif "[]" in declare[i]:
            result += "[]"
            declare[i] = declare[i].replace("[]","",1)
            
        elif "*" in declare[i]:
            result += "*"
            declare[i] = declare[i].replace("*","",1)
        print(result)
        look +=1
    
    
    result += (" ")
    result += (declare[i])
    result += (";")
    order.append(result)

for i in range(0,len(order)):
    print(order[i])

```

위의 입력은 

```
dsafsd adsf[]&[]**&, dsaf&&&****, dsfa**&[]&&, rfsdgf**&&[]*, dasfs;  
```  

이었고 그에 대한 결과는 아래와 같았다. 

```
dsafsd&&[][]** adsf;
dsafsd&&&**** dsaf;
dsafsd&&&[]** dsfa;
dsafsd&&[]*** rfsdgf;
dsafsd dasfs;
```
처음에는 이 결과가 맞는 줄 알았다.   
(정렬시키는게 아니었다..)  
이는 while 문을 어떤걸 먼저 만나게 되냐에 따라서 자동으로 정렬되게 되어 원하는 결과가 아니었다. 
<br><br>

따라서 위의 코드를 정렬하지 않고 순서에 상관없이 추가하게 하는 코드로 재구현하였다. 

``` py
for i in range(1, len(declare)):
    result = declare[0]
    name = ""
    declare[i] = declare[i].replace(",","",1)

    j=0
    
    while  j <len(declare[i]):
        if declare[i][j] !="&" and declare[i][j] !="*" and declare[i][j] !="[" and declare[i][j] !="]" :
            name +=  declare[i][j]
        j+=1    
        
    

    for k in range(len(declare[i])-1,-1,-1):
        if declare[i][k] == "&":
            result += "&"
        elif declare[i][k] == "*":
            result += "*"
        elif declare[i][k] == "]":
            result += "[]"
        else :
            continue

```  

위와같이 변수명은 따로 저장하고 배열 끝에서 탐색하여 출력하였다. 

역시 문제는 길더라도 꼼꼼히 잘 읽어야 한다. 