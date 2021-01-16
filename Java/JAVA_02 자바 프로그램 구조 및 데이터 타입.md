# Java Programming
### 02. 자바 프로그램 구조 및 데이터 타입

#### 01. 자바 프로그램 구조
1) 자바 프로그램 구조
- 자바 프로그램은 하나의 '.java'파일에 하나의 클래스를 정의
- 클래스 내부에 실행에 필요한 변수나 메서드(또는 함수) 등을 정의


```java
public class 클래스명{ // 클래스 정의
    // 변수 정의

    // 메서드 정의
}
```

```java
//FirstClass.java
public class FirstClass{
    //public : 자바 에약어로써, FirstClass.java 파일의 클래스(FirstClass)를 외부에 공개함

    // 실행할 내용
} // 클래스에서 제공할 명령 작성

```

- 자바 프로그램에서 `클래스`는 자바프로그램의 최소 구성 단위로, 선언된 클래스 내부에 실행에 필요한 변수나 메서드 등이 정의됩니다. 이때 자바 코드는 클래스 블록({}) 안에 작성되게 됩니다.
<br>

2) 자바 주석문

- 프로그램 작성 일자나 버전, 작성자, 작성 목적, 그 밖의 프로그램 내의 부분적인 요소에 대한 설명이 필요할 때 사용
- 주석문은 컴파일 시 프로그램 코드로 인식되지 않음
    - 소스 파일의 크기는 늘리지만
    - 컴파일 결과로 얻어낸 '.class'파일의 크기에는 영향이 없음

- 종류
    - // : 단일행 주석 처리
    - /* */ : 다중행 주석 처리
    - /** */ : Javadoc(자바독)형태의 주석 처리

>
> __자바 Document 생성하기__
>
> 자바 소스 파일을 작성한 후 JDK에 포함된 javadoc이라는 명령을 사용하면 해당 자바 파일 내에서 javadoc(/** */) 주석문 내에 포함된 내용과 이 클래스 내의 여러 코드들(변수, 메서드, 생성자 정보 등)에 대한 설명이 html 문서로 제공됩니다.

```cmd
javadoc ********.java 
```

#### 02. 자바 애플리케이션 작성 및 실행
1. 자바 애플리케이션 구조
- 자바 애플리케이션은 바이트 코드로 번역된 후에 바로 실행할 수 있는 일반 프로그램
- 클래스 내에 'java'라는 명령어로 프로그램을 실행할 때 자동으로 호출되어 프로그램을 시작하는 main() 메서드를 가지고 있어야 함

```java
package testProject;

public class JavaApp {
	public static void main(String[] args) {
		
	}
}
```

2. 식별자와 예약어
- 식별자
    1. 첫문자는 A-Z, a-z, _, $, 유니코드(Unicode)로 시작해야 함
    2. 특수문자 사용 불가 ex) !, @, #, %, &, * 등
    3. 대소문자를 구별하고, 길이에 제한이 없음
    4. 예약어를 포함할 수 있으나, 예약어만을 사용할 수는 없음
    5. 숫자를 사용할 수 있으나, 첫 문자에는 숫자 사용 불가
    - __관례상 클래스 이름은 대문자로, 메서드 이름은 소문자, 변수는 소문자, 상수는 대문자로 시작__



#### 02. 자바 데이터 타입과 변수
1) 데이터 타입
    - 문자형
        - char : 2byte 유니코드 문자형
    - 정수형 : 형을 명시하지 않으면 int
        - byte : 1byte
        - short : 2byte
        - int : 4byte
        - long : 8byte
    - 실수형 : 형을 명시하지 않으면 double
        - float : 4byte
        - double : 8byte


2) 변수의 할당과 초기화
    ```java
        int var; // 변수 선언
        var = 25; // 변수 초기화

        // 한 문장으로
        int var = 25;
    ```

    - 지역(Local) 변수와 전역(Global) 변수
        - 전역변수
            - 클래스 선언부 밑에 선언된 변수
            - 여러 메서드에서 공통으로 사용 가능
        - 지역변수
            - 메서드 선언부 밑에 선언된 변수
            - 메서드 매개변수로 선언된 변수
                - 해당 변수가 선언된 메서드 내에서만 사용 가능

    - 데이터 타입의 변환 = 형변환
        - 데이터 타입의 변환은 변수의 타입을 다른 타입으로 변경하고자 할 때 `형변환 연산자`를 사용하여 변환 함
        - 작은 데이터 타입에서 큰 데이터 타입으로 : Promotion(묵시적 형변환) : 데이터 손실의 우려가 없어 자동 캐스팅
            - 예 int를 double로,
            - ```java
                int age = 25;
                double avgAge = age; // 생략 가능
              ```
            - ```java
                public class PromotionTest {

                    public static void main(String[] args) {
                        // TODO Auto-generated method stub
                            byte b1 = 127;
                            char c1 = '가';
                            int i1;
                            double d1;
                            System.out.println("자동 형변환의 결과");
                            i1 = b1;
                            System.out.println("i1 = b1의 형변환 " + i1);
                            i1 = c1;
                            System.out.println("i1 = c1의 형변환 " + i1);
                            d1 = i1;
                            System.out.println("d1 = i1의 형변환 " + d1);
                    }

                }
              ```
              ```
                자동 형변환의 결과
                i1 = b1의 형변환 127
                i1 = c1의 형변환 44032
                d1 = i1의 형변환 44032.0
              ```

        - 큰 데이터 타입에서 작은 데이터 타입으로 : Demotion(명시적 형변환) : 데이터 손실의 우려로 명시적 캐스팅
            - 더 작은 범위를 나타내는 데이터 타입으로 변환되는 경우(축소 형변환)
            - 예) 8byte의 double 형을 4byte의 int 형으로 변경 시 사용
            - ```
                double avgAge = 24.56;
                int age = (int)avgAge;
              ```

            - ``` java
                package firstProject;

                public class DemotionTest {

                    public static void main(String[] args) {
                        // TODO Auto-generated method stub
                        byte b1;
                        char c1;
                        int i1 = 128;
                        int i2 = 97;
                        double d1 = 3.14;
                        System.out.println("명시적 형변환의 결과");
                        b1 = (byte) i1;
                        System.out.println("b1 = (byte)i1의 형변환 " + b1);
                        c1 = (char) i2;
                        System.out.println("c1 = (char)i2의 형변환 " + c1);
                        i1 = (int) d1;
                        System.out.println("i1 = (double)d1의 형변환 " + i1);
                        
                    }

                }
              ```
              ```
                명시적 형변환의 결과
                b1 = (byte)i1의 형변환 -128
                c1 = (char)i2의 형변환 a
                i1 = (double)d1의 형변환 3
              ```