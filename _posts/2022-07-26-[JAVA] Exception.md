---
title:  "[JAVA] Exception"
excerpt: "JAVA의 Exception 대하여"

categories:
  - java
tags:
  - [java, Exception]
  
toc: true
toc_sticky: true
 
date: 2022-07-26
last_modified_at: 2022-07-26
---
# Exception

- 예외 : Exception

### 개발자가 처리하기 힘든 예외(Error)와 처리할 수 있는 예외(Exception)

- Error + Exceptions —> Throwable(최상위 객체)
- Error → 프로그램 수정 안되는 것들
- Exception → 프로그램으로 수정이 가능한 것들 (예외를 처리한다 라고 하는 범주내에 있는 것들)

## Exception

### 1. 컴파일 시 발생하는 예외  = CheckedRxception

- RuntimeException을 제외한 예외들

### 2. 코드를 실행했을 때 발생하는 예외  = RuntimeException

- NullPointerException
- ArrayIndexOUtofBoundException
- ClassCastException
- ArithmeticException …. 등등

### 예외 관련 키워드

- 직접처리
    
    ```java
    try{
    	//예외와 관련있는 코드를 감싼다. 
    		Scanner sc = new Scanner(new File("a.txt"));
    		String line = sc.nextLine();
    }
    
    catch (예외타입 변수명) {  
    // try 블럭에서 예외가 발생했을 때 어떤 예외를 처리할 지 
    // 예외타입을 명시한다.
    		예외처리 구문 .....												 
    	
    }
    ```
    
    ```java
    try {
    			FileReader fr = new FileReader("a.txt");
    			int ch = fr.read();
    			System.out.println("읽은 내용 : " + ch);
    		
    			//랜덤값이 0일 경우 ArithmeticExceptions이 발생
    			//예이처리 코드가 업서 비정상 종료됨
    			System.out.println(1/new Random().nextInt(2));
    		} 
    		catch(FileNotFoundException e) { 
    			System.out.println("a1.txt 파일이 존재하지 않아 예외 발생하였음");
    		} 
    		catch(IOException ie) {
    			System.out.println("파일 읽는 중 예외 발생함");
    		} 
    		catch(ArithmeticException ae) {
    			System.out.println("0으로 나누었음...");
    		}
    		System.out.println("프로그램 정상 종료됨..");
    
    ```
    
    위의 코드를 순서를 바꿔보면 다음과 같다. 
    
    ```java
    try {
    			FileReader fr = new FileReader("a.txt");
    			int ch = fr.read();
    			System.out.println("읽은 내용 : " + ch);
    		
    			//랜덤값이 0일 경우 ArithmeticExceptions이 발생
    			//예이처리 코드가 업서 비정상 종료됨
    			System.out.println(1/new Random().nextInt(2));
    		} 
    		catch(IOException ie) {
    			System.out.println("파일 읽는 중 예외 발생함");
    		} 
    		catch(FileNotFoundException e) { //에러발생
    			System.out.println("a1.txt 파일이 존재하지 않아 예외 발생하였음");
    		} 
    		catch(ArithmeticException ae) {
    			System.out.println("0으로 나누었음...");
    		}
    		System.out.println("프로그램 정상 종료됨..");
    	}
    ```
    
    IoException을 상속받는 FilNoeFoundException이기 때문에 아래에 코드에 도달할 일이 없어서 
    
    에러가 발생한다. 
    
    - try{} catch () {}
    - try{} finally{}
    - try{} catch(){} finally {}
- FInaly
    - 무조선 실행 : 예외 발생 여부와 상관없이 수행한다.
    - 
- 간접처리
    - throws
    
    ```java
    static void callFour() {
    		System.out.println(1/0);
    	}
    	static void callThree() throws ArithmeticException{
    		System.out.println(1/0);
    	}
    	static void callOne() {
    		try {
    			FileReader fr = new FileReader("a.txt");
    		} catch (FileNotFoundException e) {
    			e.printStackTrace();
    		}
    	}
    	static void callTwo() throws Exception{ //FileNotFoundException , IOException{
    		FileReader fr = new FileReader("a.txt");
    		fr.read();
    	}
    	public static void main(String[] args) {
    //		callOne();
    //		FileReader fr = new FileReader("a.txt"); // 문제점을 알려줄테니까 처리해줘
    		// runtime예외는 호출한 쪽으로 무조건 에러를 던집니다. , check는 직접 던져줘야됩니다. 
    		callThree(); // 런타임 예외는 선택옵션을 준다. 
    		try {
    			callTwo();	
    			callFour();
    		} catch (Exception e) {
    			e.printStackTrace();
    		}
    		
    	}
    ```
    
- 예외를 인위적으로 만들 때
    - throw
    - throw 예외객체 , throw new 예외객체 생성();
    - 사용자 정의 예외
        - 상속 받아서 쓰면된다!
        
        ```java
        class userException extends Exception // 컴파일 시 발생하는 예외 , checkedException
        class userException extends RuntimeException // 런타임 시 발생하는 예외 , UncheckedException
        
        ```
        

### 자원 정리

- 1.7버전 부터는 AutoCloseable을 이용해서 자동 close를 활용한다.
- try-with-resource- block
- 아래의 코드는 AutoCloseable을 사용하지 않고 모든 입력에 대하여 닫기위한 코드다

```java
fr = new FileReader("a.txt");
br = new BufferedReader(fr);
			
fw = new FileWriter("acopy.txt");
bw = new BufferedWriter(fw);
			
```

만약 위의 코드중에 첫번째 라인에서 오류가 났다고 가정하자.

그러면 아래에 있는 br, fw ,bw는 아직 열리지 않은 상태다. 

```java
	if (br != null) {
				try {
					br.close();
				} catch (IOException e) {
					e.printStackTrace();
				}
			}
			if (fr != null) {
				try {
					fr.close();
				} catch (IOException e) {
					e.printStackTrace();
				}
			}
```

위의 코드를 보면 br은 닫기를 완료 할 것이고 fr은 열리지 않아 아직 null이기 때문에 NullPointerException이 발생할 것이다. 

따라서 이에 대한 조건문으로 처리를 해줘야 한다. 

### 파일 하나 복사하는데 이렇게 많은 코드가 필요하다고??

- 그래서 자바는 1.7 버젼부터 Autocloseable을 지원한다.

```java
class MyCloseable implements AutoCloseable {
	public void close() {
		System.out.println("MyCloseable - close 호출됨...");
	}
}
public class Test11 {
	public static void main(String[] args) {
		try (
//				MyCloseable mc = new MyCloseable();
				FileReader fr = new FileReader("a.txt");
				BufferedReader br = new BufferedReader(fr);
				FileWriter fw = new FileWriter("acopy.txt");
				BufferedWriter bw = new BufferedWriter(fw);
		) {
			// 작업진행...
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}
```

try 옆에 () 안에는 AutoCloseable 객체를 넣으면  finally 부분에서 처리해줬던 close를 try구문이 끝날때 호출시켜준다. 

이때 MyCloseable이 정상적으로 작동하려면 Autocloseable 의 상속을 받아야 하기 때문에 implements를 통해 상속관계를 만들어준다.