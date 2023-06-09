# 03-file

## qna

## q-01

파일명으로 파일 정보를 검색할 때 사용하는 함수는?

    1. fstat()
    2. stat()
    3. inode()
    4. fopen()

## a-01

### 2. stat()

    - pathname에 지정한 파일의 정보를 검색
    - 읽기/쓰기/실행 권한 상관없이 검색 가능
    - 디렉터리에대한 읽기 권한 필요

## q-02

매크로를 이용해 파일의 종류를 검색하려고 한다. 일반 파일인지 알아내는 매크로는?

    1. S_ISLNK(m)
    2. S_ISCHR(m)
    3. S_ISFIFO(m)
    4. S_ISREG(m)

## a-02

### 4. S_ISREG(m)

    - S_ISLNK(m)
        - 심벌릭 링크 파일 확인
    - S_ISCHR(m)
        - 문자 장치 특수 파일 확인
    - S_ISFIFO(m)
        - FIFO 파일 확인

## q-03

access() 함수를 사용해 jo.txt 파일이 존재하는 확인하려고 한다. 올바르게 사용한 것은?

    1. access("jo.txt", R_OK)
    2. access("jo.txt", W_OK)
    3. access("jo.txt", IS_OK)
    4. access("jo.txt", F_OK)

## a-03

### 4. access("jo.txt", F_OK)

    - R_OK
        - 읽기 권한 확인
    - W_OK
        - 쓰기 권한 확인

## q-04

chmod() 함수를 사용해 jo.txt 파일의 권한을 소유자만 읽고 쓸 수 있도록 설정하려고 한다. 올바르게 설정한 것은?

    1. chmod("jo.txt", S_ISUSR | S_IWGRP)
    2. chmod("jo.txt", S_IRGRP | S_IWGRP)
    3. chmod("jo.txt", S_IRUSR | S_IWUSR)
    4. chmod("jo.txt", S_IRWXU | S_IWUSR)

## a-04

### 3. chmod("jo.txt", S_IRUSR | S_IWUSR)

    - S_ISUSR
        - 소유자에게 읽기 권한
    - S_IWUSR
        - 소유자에게 쓰기 권한
    - S_IWGRP
        - 그룹에게 쓰기 권한
    - S_IRGRP
        - 그룹에게 읽기 권한
    - S_IRWXU
        - 그룹에게 읽기/쓰기/실행 권한

## q-05

jo.txt 파일의 하드링크로 jo.ln 파일을 만들려고 한다. 맞게 사용한 것은?

    1. symlink("jo.txt", "jo.ln")
    2. link("jo.txt", "jo.ln")
    3. lin("jo.txt", "jo.ln")
    4. symlink("jo.ln", "jo.txt")

## a-05

### 2. link("jo.txt", "jo.ln")

    - 링크는 이미 있는 파일이나 디렉터리에 접근할 수 있는 새로운 이름을 의미
    - 같은 파일이나 디렉터리이지만 여러 이름으로 접근할 수 있게 하는 것
    - 하드 링크
        - 파일에 접근할 수 있는 파일명을 새로 생성하는 것
        - 기존 파일과 동일한 inode 사용
        - 하드 링크 생성시 inode에 저장된 link count 증가
        - link() 함수
            - 첫 번째 인자로 oldpath
            - 두 번째 인자로 newpath
    - 심벌릭 링크
        - 기존 파일에 접근할 수 있는 다른 파일 생성
        - 기존 파일과 다른 inode 사용
        - symlink() 함수
            - 첫 번째 인자로 target
            - 두 번째 인자로 linkpath
        - lstat() 함수
            - 심벌릭 링크 자체의 파일 정보 검색 함수
            - 심벌릭 링크를 stat() 함수로 검색하면 원본 파일에 대한 정보가 검색된다는 점 주의

## q-06

명령행 인자로 받은 파일의 크기를 알려주는 프로그램을 작성하시오.

## a-06

### ./file_size.c

## q-07

명령행 인자로 받은 파일의 종류를 출력하는 프로그램을 작성하시오.

## a-07

### ./file_type.c

## q-08

명령행 인자로 받은 파일의 정보를 추출해 다음 예와 같이 출력하는 프로그램을 작성하시오.

    파일명: a.c
    inode 번호: xxxxxxx
    파일 종류: 일반 파일
    접근 권한: 100644
    UID: 1000

## a-08

### ./file_info.c

## q-09

명령행 인자로 받은 파일의 UID와 접근 권한을 다음 예와 같이 출력하는 프로그램을 작성하시오.

    a.c 1000 rw-r--r--

## a-09

### ./file_info_ln.c

## q-10

현재 디렉터리에 있는 모든 파일 및 하위 디렉터리의 이름과 inode를 출력하는 프로그램을 작성하시오.

## a-10

### ./mydir_all.c

## q-11

현재 디렉터리에서 '.'과 '..'항목을 제외하고 하위 디렉터리만 출력하는 mydir 프로그램을 작성하시오.

## a-11

### ./mydir.c

## q-12

명령행 인자로 받은 파일의 기존 접근 권한을 출력하고 접근 권한을 변경하는 프로그램을 작성하시오(문자 모드 기능 구현).

    mychmod g+w a.c

## a-12

### ./mychmod_char.c

## q-13

명령행 인자로 받은 파일의 기존 접근 권한을 출력하고 접근 권한을 변경하는 프로그램을 작성하시오(숫자 보드 기능 구현).

    mychmod 777 a.c

## a-13

### ./mychmod_num.c

## q-14

현재 디렉터리의 파일을 지정한 디렉터리로 이동시키는 프로그램을 작성하시오.

    mymv a.c dir1

## a-14

### ./mymv.c

## q-15

다른 파일 시스템에 있는 파일의 하드 링크를 생성하려면 어떤 오류 메세지가 발생하는지 확인하시오.

## a-15

### ./hard_link_error_log.txt

## q-16

명령행 인자로 받은 파일의 심벌릭 링크를 생성하고 심벌릭 링크 파일의 내용과 원본 파일의 경로를 출력하는 프로그램을 작성하시오.

    mysym a.c

## a-16

### ./mysym.c

## q-17

현재 디렉터리에서 inode가 같은 파일을 검색해 파일명을 출력하는 프로그램을 작성하시오.

## a-17

### ./search_inode.c

## q-18

현재 디렉터리에 어떤 파일의 하드 링크가 여러 개 있을 때 그중에 한 파일만 남기고 링크를 모두 끊는 프로그램을 작성하시오.

## a-18

### ./unlinker.c
