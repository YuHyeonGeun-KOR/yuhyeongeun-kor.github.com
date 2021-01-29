---
title:  "BOJ 2290 : LCD Test"
excerpt: "지민이는 새로운 컴퓨터를 샀다. 하지만 새로운 컴퓨터에 사은품으로 온 LC-디스플레이 모니터가 잘 안나오는 것이다. 지민이의 친한 친구인 지환이는 지민이의 새로운 모니터를 위해 테스트 할 수 있는 프로그램을 만들기로 하였다.."

categories:
  - BaekJoon
tags:
  - [code,Python]

toc: true
toc_sticky: true
 
date: 2021-01-29
last_modified_at: 2020-01-29
---

# BOJ 2290 : LCD Test 문제  


이번 문제를 해결 하기 위해서 다음과 같이 접근하였다.  

1. 숫자별로 출력의 규칙을 찾아서 해당 배열의 공식에 따라 List에 저장한다.
2. 1을 생각 해보았더니 너무 복잡하고 간결하지 않아 다시 생각하기로 했다.
3. 입력받은 숫자를 String으로 변환후 하나씩 리스트에 담는다.
4. 저장된 list에서 숫자를 하나씩 받아오고 해당 숫자에 해당하는 함수를 따로 구현하여 저장후 출력한다.

위의 순서로 코드를 구현하였고 구현한 코드는 아래와 같다. 
숫자별로 함수가 따로 존재하여 코드의 길이에 유의한다.
``` py
import sys
input = sys.stdin.readline

s, n = map(int, input().split())

n_list = []
for i in str(n):
    n_list.append(i)


result = [[] for i in range(0,2*s+3)]


def one(s,result):
    for i in range(0,2*s+3):
        if i % (s + 1) == 0 :
            result[i].append(" "*(s+2))
            result[i].append(" ")
        elif  i < s + 1:
            result[i].append(" "*(s+1))
            result[i].append("|")
            result[i].append(" ")
        else:
            result[i].append(" "*(s+1))
            result[i].append("|")
            result[i].append(" ")
    return result

def two(s,result):
    for i in range(0,2*s+3):
        if i % (s + 1) == 0 :
            result[i].append(" ")
            result[i].append("-" * s)
            result[i].append(" ")
            result[i].append(" ")
        elif  i < s + 1:
            result[i].append(" " * (s+1))
            result[i].append("|")
            result[i].append(" ")
        else:
            result[i].append("|")
            result[i].append(" " * (s+1))
            result[i].append(" ")            
    return result

def three (s,result):
    for i in range(0,2*s+3):
        if i % (s + 1) == 0 :
            result[i].append(" ")
            result[i].append("-" * s)
            result[i].append(" ")
            result[i].append(" ")
        else:
            result[i].append(" " * (s+1))
            result[i].append("|")
            result[i].append(" ")
    return result

def four (s,result):
    for i in range(0,2*s+3):
        if i  == 0 :
            result[i].append(" " *(s+2))
            result[i].append(" ")
        elif  i < s + 1:
            result[i].append("|")
            result[i].append(" " * (s))
            result[i].append("|")
            result[i].append(" ")
        elif i  == (s+1):
            result[i].append(" ")
            result[i].append("-"*s)
            result[i].append(" ")
            result[i].append(" ")
        elif  i > s + 1 and i % (s + 1) != 0:
            result[i].append(" " * (s+1))
            result[i].append("|")
            result[i].append(" ")
        else:
            result[i].append(" " * (s+2))
            result[i].append(" ")
        
    return result


def five(s,result):
    for i in range(0,2*s+3):
        if i % (s + 1) == 0 :
            result[i].append(" ")
            result[i].append("-" * s)
            result[i].append(" ")
            result[i].append(" ")
        elif  i > s + 1:
            result[i].append(" " * (s+1))
            result[i].append("|")
            result[i].append(" ")
        else:
            result[i].append("|")
            result[i].append(" " * (s+1))
            result[i].append(" ")            
    return result

def six(s,result):
    for i in range(0,2*s+3):
        if i % (s + 1) == 0 :
            result[i].append(" ")
            result[i].append("-" * s)
            result[i].append(" ")
            result[i].append(" ")
        elif  i > s + 1:
            result[i].append("|")
            result[i].append(" " * (s))
            result[i].append("|")
            result[i].append(" ")
        else:
            result[i].append("|")
            result[i].append(" " * (s+1))
            result[i].append(" ")            
    return result

def seven(s,result):
    for i in range(0,2*s+3):
        if i == 0 :
            result[i].append(" ")
            result[i].append("-" * s)
            result[i].append(" ")
            result[i].append(" ")
        elif  i % (s + 1) == 0 :
            result[i].append(" " * (s+2))
            result[i].append(" ")
        else:
            result[i].append(" " * (s+1))
            result[i].append("|")
            result[i].append(" ")            
    return result

def eight(s,result):
    for i in range(0,2*s+3):
        if i % (s + 1) == 0 :
            result[i].append(" ")
            result[i].append("-" * s)
            result[i].append(" ")
            result[i].append(" ")
        else:
            result[i].append("|")
            result[i].append(" " * (s))
            result[i].append("|")
            result[i].append(" ")          
    return result

def nine(s,result):
    for i in range(0,2*s+3):
        if i % (s + 1) == 0 :
            result[i].append(" ")
            result[i].append("-" * s)
            result[i].append(" ")
            result[i].append(" ")
        elif  i < s + 1:
            result[i].append("|")
            result[i].append(" " * (s))
            result[i].append("|")
            result[i].append(" ")
        elif  i > s + 1:
            result[i].append(" " * (s+1))
            result[i].append("|")
            result[i].append(" ")        
        else:
            result[i].append("|")
            result[i].append(" " * (s))
            result[i].append("|")
            result[i].append(" ")          
    return result

def zero(s,result):
    for i in range(0,2*s+3):
        if i == 0 or i == 2*(s+1):
            result[i].append(" ")
            result[i].append("-" * s)
            result[i].append(" ")
            result[i].append(" ")
        elif  i < s + 1 or i > s + 1:
            result[i].append("|")
            result[i].append(" " * (s))
            result[i].append("|")
            result[i].append(" ")
        elif  i > s + 1:
            result[i].append(" " * (s+1))
            result[i].append("|")
            result[i].append(" ")        
        else:
            result[i].append(" " * (s+2))
            result[i].append(" ")          
    return result

for i in range(0,len(n_list)):
    if n_list[i] == '1':
        one(s,result)
    elif n_list[i] == '2':
        two(s,result)
    elif n_list[i] == '3':
        three(s,result)
    elif n_list[i] == '4':
        four(s,result)    
    elif n_list[i] == '5':
        five(s,result)  
    elif n_list[i] == '6':
        six(s,result)      
    elif n_list[i] == '7':
        seven(s,result)     
    elif n_list[i] == '8':
        eight(s,result)  
    elif n_list[i] == '9':
        nine(s,result) 
    elif n_list[i] == '0':
        zero(s,result)        

for i in range(2*s+3):
        r  = "".join(result[i])
        print(r)
```

위의 입력은 

```
3 1234567890
``` 
이었고 그에 대한 결과는 아래와 같았다. 

```
       ---   ---         ---   ---   ---   ---   ---   ---
    |     |     | |   | |     |         | |   | |   | |   |
    |     |     | |   | |     |         | |   | |   | |   |
    |     |     | |   | |     |         | |   | |   | |   |
       ---   ---   ---   ---   ---         ---   ---
    | |         |     |     | |   |     | |   |     | |   |
    | |         |     |     | |   |     | |   |     | |   |
    | |         |     |     | |   |     | |   |     | |   |
       ---   ---         ---   ---         ---   ---   ---
```


단순 구현문제였기 때문에 만들어 놓은 함수를 재사용하면서 조건에 따른 줄만 바꿔주면서 시간을 좀더 단축시키려고 해보았다. 더 좋은 코드가 있으면 참고하여 포스팅 하도록 하겠다.