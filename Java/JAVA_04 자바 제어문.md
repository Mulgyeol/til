# Java Programming 초급
## 자바언어의 구조와 기본 문법
### 04. 자바 제어문

#### 01. 자바 제어문
1. 조건 제어문
    - switch
        - case는 char, byte, short, int 가능
        - case문 끝에 break 문이 없다면?
            - break문이 나타나거나, switch 블록이 끝날 대까지 다음 case 문에 대한 문장을 차례대로 수행해야 함
            ```Java
                package firstProject;

                import java.util.*;

                public class Condition2 {
                    public static void main(String[] args) {
                        Scanner sc = new Scanner(System.in);
                        int month = sc.nextInt();
                        switch(month) {
                        case 3:
                        case 4:
                        case 5:
                            System.out.println(month + "월은 봄입니다.");
                            break;
                        case 6:
                        case 7:
                        case 8:
                            System.out.println(month + "월은 여름입니다.");
                            break;
                        case 9:
                        case 10:
                        case 11:
                            System.out.println(month + "월은 가을입니다.");
                            break;
                        case 12:
                        case 1:
                        case 2:
                            System.out.println(month + "월은 겨울입니다.");
                            break;
                        }
                        sc.close();
                    }
                }
            ```
            
2. 반복 제어문
    - for
        - for(초기식; 조건식; 증감식){
            //for 반복문에 대한 제어는 for 예약어 뒤에 있는 괄호에 작성되며, 세미콜론에 의해 초기식, 조건식, 증감식으로 구성됨
        }
        - 초기식 : 반복 횟수 제어하기 위한 카운터를 초기화, 반복이 시작되기 전에 한 번만 실행됨
        - 조건식 : true이면 내용을 수행
        - for 블록 내 선언된 변수는 for 블록 내부에ㅓ만 사용함
        - for 블록을 포함하는 메서드 내에서 선언된 변수와 같은 이름으로 선언할 수 없음
        - for 블록 내의 변수는 외부에서 호출이 불가능함
        ```Java
            package firstProject;

            public class For {
                public static void main(String[] args) {
                    for(int i = 0; i <= 10; i++) {
                        for (int j = 0; j <= i; j++) {
                            System.out.print("*");
                        }
                        System.out.println("");
                    }
                }
            }
        ```
    - while
    - do-while
        - 조건식이 false라도 반복문을 최소한 한 번은 실행함

3. 이동 제어문
    - break
        - switch 문에서 쓰일 경우, 수행을 중단하고 switch 블록을 종료할 때 사용
        - 반복 문에서 쓰일 경우, 수행을 중단하고 반복문 자체를 종료할 때 사용
    - continue
        - 반복문(for, while) 문에서 현재 단계의 수행을 생략하고 다음 단계로 계속 진행함
    - return
        - 메서드의 수행을 종료하고 메서드가 호출된 곳으로 제어를 이동시킴