---
title:  "[JAVA]  Collection Framework List"
excerpt: "JAVA의  Collection Framework List 대하여"

categories:
  - java
tags:
  - [java,  Collection Framework List]
  
toc: true
toc_sticky: true
 
date: 2022-07-27
last_modified_at: 2022-07-27
---
# Collection Framework List

# 자료구조

- 컴퓨터 과학에서 효율적인 접근 , 수정을 위한 자료의 조직 관리

## 배열

- 가장 기본적인 자료 구조
- 동일한 데이터 타입 관리
    - 타입이 다르면 매번 다른 배열 필요 → 다형성으로 해결 (담을때는 편하지만 빼낼때 타입을 확인해야함) → Generic으로 타입을 제한

## Collection Framework

- java.util 패키지
    - List :  순서가 있는 데이터의 집합 , 순서가 있으므로 중복 가능
    - Set :  순서를 유지 하지 않는 데이터의 집합 , 중복 x
    - Map : key , value 쌍으로 데이터를 관리하는 집합  , 순서 없음 , 중복 x
    
                                    Iterable
    
                             Collection    ←——— Queue
    
                                  List
    
            Vector        ArrayList        LinkedList
    
             stack
    

### Collection interface

특성에 맞게 자료를 추가 수정 삭제 조회할 수 있다는 이야기 

- 추가 : add
- 조회 : contains , equals , isEmpty ,
- 삭제 : removeAll(Collection<>c) : c에있는 걸 전부 빼라 , retainAll(Collection<> c) c에 없는거 빼라

### List

- 순서가 있는 데이터의 집합
- 순서가 있기 때문에 중복을 허락한다.
- Vector → 멀티쓰레드 동기화  느림 ,
- ArrayList → 동기화 안함 , 상대적으로 빠름

![Untitled](Collection%20Framework%20List%20d7aa2cf787c744e3a7eb6c6ff05f5003/Untitled.png)

### 배열과 ArrayList

- 배열의 장점 : 간단하고 사용이 쉽다. , 접근속도가 빠르다.
- 배열의 단점 : 크기를 변경할 수 없다 , 추가데이터는 새로운 배열을 만들고 복사해야 한다.

### ArrayList

- 선언  예시 : List<String> aList = new ArrayList<>();
    - 비어있는지 확인 : .isEmpty();
    - 요소를 받아오기 : .get();
    - value의 index 가져오기 : indexOf(””) . lastIndexOf();
    - 인덱스 범위로 subList 만들기 : aList.subList(1,4);
- add시에 길이가 모자르면 자동으로 길이를 늘려주기는 한다.
    - 하지만 내부적으로 배열로 선언되어있기 때문에 길이를 미리 설정하는것이 더 빠르다

### 

### ArrayList 삭제 시 주의사항

- index를 통해서 접근하다가 삭제를 하게 되면 인덱스가 망가지기 때문에 잘못된 결과를 가져온다.
    - →>> 그럼 뒤에서 부터 삭제하면 index가 망가지지 않겠군?
    
    ```java
    for (int i = nums.size()-1; i >= 0 ; i--) {	
            	if(nums.get(i) % 3 == 1 ) {
            		nums.remove(i);
            		i--;
            	}
            }
    ```
    
- forEach 문장 → Collection크기가 불변해야 한다.
- asList로 만들어진 List객체
    - 내부적으로 add, remove가 List를 상속받을때 재정의가 되어있지 않음
    - 찾아가보면 예외를 던지게 되어있기 때문에 바로 예외를 던짐
    - asList로 선언된 객체는 수정하는 용도로 사용해야 한다.
    

### LinkedList

- 각 요소가 다음 요소의 링크정보 가지며 연속적으로 구성될 필요가 없다.
- 각 요소를 Node로 정의한다.

### LinkedList vs ArrayList

- 특정 클래스가 좋다라고 하는게 아니라 용도에 맞게 사용
- ArrayList : 정적인 데이터 , 단순 데이터 조회용
- LinkedList :  동적인 데이터  , 삭제가 많은 작업

## 정렬

- 요소를 특정 기준에 대한 내림차순 또는 오름 차수능로 배치하는것
- **순서를 가지는 collection 들만 정렬  가능**
    - List 계열
    - Set에서는SortedSet의 자식 객체
    - Map에서는 SortedMap의 자식 객체 (Key 기준으로)

### Collections sort()

- Collections.sort(names); 처럼 사용
- 역순으로 정렬하기 위해서는 sort 이후에 reverse를 해주면된다.

정렬하기 위한 아래의 코드를 확인해보자 

```java
List<SmartPhone> phones = Arrays.asList(
    			new SmartPhone("017") , new SmartPhone("011") , 
    			new SmartPhone("017"));
    	Collections.sort(phones);
```

phones는 SmartPhoen 객체를 담는 객체 배열이다. 

그런데 Collections.sort(phones)를 하게 되면 오류가 발생한다

 **Why?**

- 정렬 기준에 대한 제시가 없다. → 정렬 기준을 제시해주어야 한다.

### 정렬 기준을 제시

```java
public class SmartPhone {
  
    String number;

    public SmartPhone(String number) {
        this.number = number;
    }

    public String toString() {
        return "전화 번호: " + number;
    }
    

}
```

위의 코드를 확인 해보면 SmartPhone class는 정렬할 수 있게 해줘야 한다. 

```java
public class SmartPhone implements Comparable{
}
```

Comparable과 상속관계를 형성하여 interface의 구현체를 만든다. 

interface를 상속했으므로 내부 메서드를 재정의 해줘야 한다. 

```java
public int compareTo(T o);

@Override
	 public int compareTo(SmartPhone o) {
		 // TODO Auto-generated method stub
		 return this.number.compareTo(o.number);
	 }
```

comparTo는 Comparable에 있는 추상 메서드 이므로 아래 처럼 SmartPhone에서 재정의 해주었다. 

번호를 기준으로 정렬하겠다는 기준을 제시해 주었기 때문에 비로소 sort함수가 작동할 수 있게 되었다.

```java
Collections.sort(phones);
```

이제 sort로 phones 객체 배열을 넘겨서 번호를 기준으로 정렬할 수 있게 되었다. 


## Comparator를 활용한 정렬

문자열의 길이를 기준으로 정렬을 하고 싶다. 

문자열의 길이를 기준으로 정렬하고 싶다면 sort 메서드를 재정의하면 된다. 

Collections.sort()에서 두번째 인자로 Comparator를 매개변수로 넣어준다.

- 두번째 인자는 Comparator의 타입으로 넣어주면된다.

```java
class MyComp implements Comparator<String>{

		@Override
		public int compare(String o1, String o2) {
			// TODO Auto-generated method stub
			return Integer.compare(o1.length() ,o2.length());
		}
      
    }
```

Comparator를 상속받은 MyComp를 sort의 매개변수로 넣어주려고 한다. 

Comparator는 interface이기 때문에 매서드의 재정의가 필요하다. 

나는 문자열로 비교할 것이기 때문에 Generic Type을 String으로 선언해주었다. 

compare 메서드의 매개변수도 역시 String타입으로 선언한다. 

그럼 이제 클래스의 객체를 생성해서 sort 메서드에 매개변수로 넣어주자 

```java
Collections.sort(names , new MyComp());
```

그런데  MyComp는 한번만 사용되는데 굳이 class로 만들어서 변수를 통해 넣어줘야 할까?

그래서 다음과 같이 코드를 수정했다. 

```java
Collections.sort(names , new Comparator<String>() {
        	
        	@Override
    		public int compare(String o1, String o2) {
    			// TODO Auto-generated method stub
    			return Integer.compare(o1.length() ,o2.length());
    		}
        });
```

- anonymous inner class
    
    MyComp라는 class는 Comparator를 상속받기 때문에 Comparator로 변수를 담을 수 있디 때문에 Comparator를 직접 객체 생성을 통해 매개변수로 넣어 줄 수 있다. 
    

### 

### 익명 클래스

- 클래스의 이름이 없는것
- 이름이 없다. (class 이름 - x)
- 객체 생성 + 클래스 내용 정의
- 선언 형식 : (클래스 | 인터페이스) () {} —> 부모이름이 적힌다.
- 이름이 없는데 어떻게 변수에 담지? → 부모클래스는 자식의 클래스를 변수로 담을 수 있기 때문에 부모의 이름으로 담는다.