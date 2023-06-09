# 01-basics

## qna

## q-01

다음 중 리눅스/유닉스 시스템 프로그래밍과 관련이 있는 표준이 아닌 것은?

    1. ANSC C 표준
    2. POSIX
    3. 다중 유닉스 명세
    4. 시스템 V 인터페이스 정의

## a-01

### 1. ANSC C 표준, 3. 다중 유닉스 명세

    - ANSC C 표준 -> ANSI C
        - American National Standards Institute 는 미국 표준 협회로 해당 협회에서 표준화한 C 언어 명세
        - C 언어 문법과 라이브러리, 헤더 파일 등을 정의
    - 다중 유닉스 명세 -> 단일 유닉스 명세
        - SUS(Single Unix Specification) 는 운영체제가 유닉스라는 이름을 사용하기 위해 지켜야 하는 표준의 총칭

## q-02

man 페이지 번호에서 시스템 호출을 나타내는 섹션 번호는?

    1. 1
    2. 2
    3. 3
    4. 5

## a-02

### 2. 2

    - 매뉴얼은 항목의 종류에 따라 섹션 구분
    - 섹션 1
        - 일반적인 명령
    - 섹션 2
        - 시스템 호출
    - 섹션 3
        - 라이브러리 함수 

## q-03

시스템 호출이 실패하면 -1을 리턴한 뒤 오류 코드를 특정 변수에 저장한다. 이 변수명은?

    1. eno
    2. error
    3. enum
    4. errno

## a-03

### 4. errno

    - 전역 변수 errno에 오류 코드를 저장
    - sys/errno.h 파일에 정의

## q-04

리눅스 기본 명령 중 패턴을 검색할 떄 사용하는 명령은?

    1. ls
    2. cat
    3. grep
    4. which

## a-04

### 3. grep

    - ls
        - 디렉터리 내용 출력
    - cat
        - 파일 내용 출력
    - grep
        - 패턴 검색
    - which
        - 파일 위치 검색

## q-05

an.c를 컴파일할 때 실행 파일명을 jo으로 하려고한다. gcc의 옵션을 바르게 설정한 것은?

    1. gcc jo.c
    2. gcc -c jo jo.c
    3. gcc -a jo jo.c
    4. gcc -o jo jo.c

## a-05

### 4. gcc -o jo jo.c

    - 옵션 c
        - 오브젝트 파일만 생성
    - 옵션 o
        - 지정한 파일 이름으로 실행 파일 생성

## q-06

시스템 호출과 라이브러리 함수의 차이점을 동작 과정 비교를 통해 설명하시오.

## a-06

시스템 호출은 커널의 해당 모듈을 직접 호출해 작업하고 결과를 리턴하는 반면 라이브러리 함수는 커널 묘듈에 접근하기 위해 함수 내부의 시스템 호출을 사용한다.

## q-07

man write 명렁을 실행했는데, write() 함수가 아니라 write 명령에 대한 매뉴얼이 출력되었다. write() 함수의 매뉴얼을 보려면 어떻게 해야 할까?

## a-07

man -s 3 write 명령어를 통해 라이브러리 함수 섹션 번호 3번을 입력하여 매뉴얼을 확인하면 된다.

## q-08

시스템 호출에서 오류가 발생하면 errono 변수에 오류의 원인을 설명하는 숫자가 저장된다. 오류 번호가 1이라면 어떤 오류일까?

## a-08

오류 번호가 1일 경우에는 #define EPERM 1 으로 헤더 파일에 정의 되어 있으며 Operation not permitted로 권한관련 오류이다.

## q-09

[예제1-1]을 수정해 errno 번호뿐만 아니라 오류 메시지도 출력되도록 코드를 수정하시오([예제 1-4] 참조).

## a-09

### ./error_out.c

## q-10

gcc로 소스 코드를 컴파일했더니 실행 파일 a.out이 만들어졌다. 실행 파일을 ex10.exe로 만들려면 어떻게 해야 할까?

## a-10

### gcc -o ex10.exe ex10.c

    - -o 옵션을 통해 실행 파일명 수정

## q-11

gcc로 소스 코드를 컴파일해 실행 파일인 ex11.exe를 만들었다. ls 명령으로 확인하면 ex11.exe가 보이는데, ex11.exe를 실행하면 파일을 찾을 수 없다고 한다. 무엇이 문제이고 어떻게 해결할 수 있는지 설명하시오.

## a-11

### gcc -c ex11.c

### gcc -o ex11.exe ex11.o

    - 바로 -o 옵션을 이용해 exe 파일을 생성할때 코드 내부에 정의되지 않은 외부 함수가 있을 경우 링크 단계를 거치지 않았으므로 에러가 발생한다. 따라서, 먼저 -c 옵션을 통해 링크 단계를 거친 오브젝트 파일을 가지고 실행파일을 생성하여 문제를 해결할 수 있다.

## q-12

[예제 1-3]에서 인자로 받은 두 정수의 뺄셈을 계산해 리턴하는 subnum() 함수를 subnum.c 파일로 만들고 Makefile을 수정해 실행 파일을 생성한 뒤 실행 결과를 확인하시오.

## a-12

### ./subnum/

## q-13

프로그램을 실행하는 도중에 정숫값 200개를 저장할 수 있도록 메모리를 할당하려면 어떻게 해야 할까?

## a-13

### ./mem.c

## q-14

명령행 인자로 정숫값(작은 수, 큰 수) 2개를 받아서 앞의 값부터 뒤의 값까지 합계를 구하는 프로그램을 작성하시오.

## a-14

### ./addnum-cmd

## q-15

명령행 인자와 getopt() 함수를 사용해 다음 명령을 처리하는 프로그램을 작성하시오.

1. 명령의 이름: ex1_15.out

2. 명령의 옵션과 동작

- 인자가 없을 경우: -h처럼 사용 가능한 옵션의 목력 출력

- -p: "Welcome Linux System Programming!" 출력

- -n: "Nice to meet" 출력

- -h: 사용 가능한 옵션의 목록 출력

## a-15

### ./cmdopt.c
