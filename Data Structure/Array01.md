# 배열(Array)
* 데이터를 나열하고, 각 데이터를 인덱스에 대응하도록 구성한 데이터 구조
* 파이썬에서는 리스트 타입이 배열 기능을 제공함

## 1. 배열이 필요한 이유
- 같은 종류의 데이터를 효율적으로 관리하기 위해 사용
- 같은 종류의 데이터를 순차적으로 저장
- 장점: 
  - 빠른 접근 가능
    - 첫 데이터의 위치에서 상대적인 위치로 데이터 접근(인덱스 번호로 접근)
- 단점: 
  - 데이터 추가/삭제의 어려움
    - 미리 최대 길이를 지정해야 함(파이썬은 제외)
    
## 2. 파이썬과 C언어의 배열 예제
- C언어 예
```
    #include <stdio.h>

    int main(int argc, char * argv[])
    {
        char country[3] = "US";
        printf ("%c%c\n", country[0], country[1]);
        printf ("%s\n", country);    
        return 0;
    }
```
- 파이썬 예
```
    country = 'US'
    print (country)
```