# Markdown

- 텍스트 기반의 가벼운 마크업(markup)언어
    
    → 마크업(markup) : 태그(tag)를 이용하여 문서의 구조를 나타내는 것
    
- 문서의 구조와 내용을 같이 쉽고 빠르게 적고자 탄생 ← 탄생 이유, 장점
- 노션에서 사용하는 방식 (매터모스트 에서도 가능)

Github 문서의 시작과 끝!

- [README.](http://README.MD)md 파일을 통해 오픈 소스의 **공식 문서** 작성
- 개인 프로젝트의 **소개 문서** 작성
- 매일 학습한 **내용 정리**
- 마크다운을 이용한 **블로그 운영**

# Git 이란

⇒ 분산 **버전 관리 프로그램!!**

→ 개발 현업에서 git의 대항마는 없는가?? ex) “Vue3” ↔ “React”

→ 원래 대항마로 “Bit keeper”가 있었음

→ 라이센스 문제가 발생

→ Unix 운영체제를 만든 회사인 “GNU”의 오픈소스 Git

→ 모두 Git으로 넘어옴

→ Git 만이 주력으로 살아남음

- 버전 : 컴퓨터 소프트웨어의 특정 상태
- 관리 : 어떤 일의 사무를 유지
- 버전 관리 : 컴퓨터의 특성 상태들을 관리하는 것?

→ 우리는 **버전 관리**를 알고 있다.

ex) 레포트 최종 → 레포트 최종 최종 → 레포트 찐 최종

→ 어떤게 진짜 최종이지?

→ **파일에 날짜와 시간을 적자!!**

→ but 모든 파일을 다 가지면 용량을 매우 많이 차지함.

⇒ **수정 사항만 가지고 빽업 할 수 있다면?? : 스냅샷 방법**

**버전 관리 프로그램** ⇒ **파일 히스토리를 저장하는 도구!!**

→ **최종파일과, 변경사항들만 저장**

- **코드의 히스토리(버전)을 관리하는 도구**
- **개발 되어온 과정 파악 가능**
- **이전 버전과의 변경 사항 비교 및 분석**

분산

중앙 집중식 버전 관리

→ 원격 저장소에서 최신 파일만 받아서 파일을 관리

→ 컴퓨터에서 작업을 하다 원격저장소에 문제가 생기면 더 이상 작업 불가

분산 버전 관리

→ 원격 저장소에서 최신파일과 히스토리를 모두 복제해서 pc로 가져옴

→ 원격 저장소에 문제가 생겨도 작업이 가능함

→ 히스토리의 용량이 큰 문제가 있을 수 있다. (큰 파일을 넣었다가 삭제한 경우 : 히스토리에 남아 있음) 

→ 두 컴퓨터가 파일 병합 시 충돌이 발생할 수 있음

원격저장소의 서버 (대표적인) 

1. GitLab
2. GitHub
3. Bitbucket

⇒ Git 은 버전 관리 시스템이고, GitHub는 버전 관리를 위한 웹 호스팅 서비스 이다. (다름)

→ Git(커피), GitHub(커피 숍)

# 정리 !!

1. 분산 버전 관리 : 과거 특정 시점으로 되돌아가거나, 한번에 여러 버전으로 개발자들이 동시에 작업 가능하다 ← (나중에.. 배울 브랜치 기능)
2. 성능 : 이전에 있었던 모든 버전 관리 프로그램보다 성능이 월등히 빨랐다.
    
    대용량 프로젝트를 효율적으로 관리 가능!
    
3. 커뮤니티 : 오픈소스 소프트웨어, → 커뮤니티 기반으로 개발이 누구나 참여 가능, 활발했다.
4. 공개 저장소 : 사용자들이 공개 저장소(github)를 이용해서 프로젝트를 공유,
    
    프로젝트 관리/ 팀 개발.. 용이
    

# Github

1. Git을 이용한 버전관리
2. **Github를 이용한 포트폴리오**
    
    데일리 커밋(하루하루 성실히 산 지표) → 잔디
    
    프로젝트 설명과 링크(핀)
    
    포트폴리오 현황을 작성 (뱃지 개념의 카드)
    

# CLI 

GUI와 CLI

- CLI : Command Line Interface ↔ GUI : Graphic User Interface
- GUI : 그래픽을 통해 사용자와 컴퓨터가 상호 작용하는 방식
- CLI : 명령어를 통해 사용자와 컴퓨터가 상호 작용하는 방식

why CLI

- GUI는 CLI에 비해 사용하기 쉽지만 단계가 많고 컴퓨터의 성능을 더 많이 소모
- 수 많은 서버/ 개발 시스템이 CLI를 통한 조작 환경을 제공

기본적인 명령어

- touch - 파일을 생성하는 명령어
- mkdir - 새 폴더를 생성하는 명령어
- ls (-al) - 현재 작업 중인 디렉토리의 폴더/ 파일 목록을 보여주는 명령어
- cd - 디렉토리 변경
- start, open - 파일/ 폴더 열기
- rm (-R) - 지우기 (재귀적으로 지울 시  : -R)

```bash
touch // 파일을 생성하는 명령어
mkdir // 새 폴더를 생성하는 명령어
ls (-al) // 현재 작업 중인 디렉토리의 폴더/ 파일 목록을 보여주는 명령어
cd // 디렉토리 변경
start or open // 파일/ 폴더 열기
rm [-R] //지우기 (재귀적으로 지울 시  : -R)
```

절대 경로 VS 상대 경로

절대 경로

- 루트 디렉토리 부터 목적 지점까지 거치는 모든 경로를 전부 작성한 것
- 윈도우 바탕 화면의 절대 경로 - C:/Users/ssafy/Desktop

상대 경로

- 현재 작업하고 있는 디렉토리를 기준으로 계산된 상대적 위치를 작성한 것
- 현재 작업하고 있는 디렉도리가 C:/Users 일 때
    
    → 윈도우 바탕 화면으로의 상대 경로는 ./ssafy/Desktop
    
- ./ : 현재 작업하고 있는 폴더
- ../ : 현재 작업하고 있는 폴더의 부모 폴더

→ 상대 경로를 사용하는 것 = 같은 지역에서 지역 번호를 생략하는 것

<실습>

1. 현재 디렉토리 출력
2. sample 디렉토리 생성
3. sample 로 작업디렉토리 이동
4. 현재 디렉토리 출력
5. red, orange, white 파일 추가
6. red 파일에 "빨강" 내용 추가
7. orange 파일에 "주황" 내용 추가
8. 현재 디렉토리 출력
9. white 파일 삭제
10. 현재 디렉토리 출력

```bash
pwd // 1.
ls -al
mkdir sample // 2.
cd ./sample // 3.
pwd // 4.
ls -al
touch red orange white // 5.
vi red // 6.                    echo "빨강" > red // 덮어쓰기
[i]                             echo "빨강" >> red // 추가
"빨강"                          cat red // 파일출력
[Esc]    
:wq
vi orange // 7.                 echo "주황" > orange
[i]                             echo "주황" >> orange // 추가
"주황"                          cat orange // 파일출력
[Esc]
:wq
pwd // 8.
ls -al
rm white // 9.
pwd  // 10.
ls -al
```
## Git 기본기

- README.md
    - 프로젝트에 대한 설명 문서
    - Github 프로젝트에서 가장 먼저 보는 문서
    - 일반적으로 소프트웨어와 함께 배포
    - 작성 형식은 따로 없으나, 일반적으로 마크다운을 이용해 작성
- [README.md](http://README.md) 생성하기
    - 새 폴더를 만들고 [README.md](http://README.md) 파일을 생성해 주세요
    - 이 파일을 버전 관리하며 Git을 사용해 봅시다.
        
        → 특정 버전으로 남긴다 = “커밋(commit) 한다”
        
- 커밋은 이 3가지 영역을 바탕으로 동작
    1. Working Directory : 내가 작업하고 있는 실제 디렉토리
    2. Staging Area :  커밋(commit)으로 남기고 싶은, 특정 버전으로 관리하고 싶은 파일이 있는 곳
        
        → **일부분만 커밋하고 싶을때**
        
        - 워킹 디렉토리 골라서 커밋하고 싶을 때..!
        
        → **충돌을 해결할 때**
        
        - 협업 과정에서 여러 사람이 파일을 작업하게 되는데… 수정사항이 겹치는 영역에 대해서 … Staging Area를 통해 충돌을 해소
        
        → **커밋을 다시 고치고 싶을 때**
        
        - 로그 메시지만 고치는 게 아니라, 파일을 수정해서 다시 커밋(버전을 수정)하고 싶다면 ‘commit —amend’
    3. Repository : 커밋(commit) 들이 저장되는 곳

- git add : untracted file(Working Directory) → added file(Staging Area)
- git commit [-m message] : added file(Staging Area) → committed(Repository)

## Repository

- 특정 디렉토리를 버전 관리하는 **저장소**
    
    ```bash
    git init // 명령어로 로컬 저장소를 생성(레포지토리 생성)
    git add [file_name]
    git commit [-m 'memo']
    git log
    git status
    ```
    
- **.git** : 디렉토리에 **버전 관리에 필요한 모든 것**이 들어있음

## 외부 Repository 에 push

```bash
git remote add origin {remote repository}
git push -u origin master
```
번외 : 백준허브 써보자, 소스트리
