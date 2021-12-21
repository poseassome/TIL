# Git
Git은 기존 파일과 변경된 내용을 분리해서 저장한다.
<br/>
그냥 파일 덮어쓰기가 아니기에 문제가 생기면 특정 시점으로 되돌아가는게 가능하다.
***

## Git 개요
버전 관리 시스템 (VCS: Version control system)
>1) ### SVN(Subversion)<Br/>
    중앙집중식<Br/>
    기능이 완성된 형태로 commit<br/>
    - 전체 통합 공간

>2) ### Git<Br/>
    분산형 버전 관리<Br/>
    개발자별 commit history (=개발자별로 보내기할 때 기록이 남는다.)<Br/>
    개발자 repository와 서버 repository를 독립적으로 운영
    - 전체 통합 공간이 있고 개인 사용자별 저장 공간이 따로 있다.
<br/>

#### 1. 특징<br/>
  대부분의 명령을 로컬에서 실행<br/>
  원격 저장소의 정보가 필요할 때만 연결(pull, push)<br/>
  오프라인 환경에서도 commit<br/>
    - 일반 파일 관리
      : 무엇이 수정되었는지 차이를 알 수 없다, 용량 증가
    - 소스 코드 관리
      : history관리기능(차이가 무엇이고 수정이유를 log로 남김)
        / 타임머신 기능(현재 파일들은 안전한 상태로 과거 상태 그대로 복원가능 <-> 반대도 가능)

#### 2. 설치 <br/>
  MacOS의 경우 낮은 버전이 설치되어 있는 경우 있음.<br/>
      - homebrew에서 확인
      - brew install

#### 3. 사용<br/>
  무조건 시작 명령어는 git

  1. 설치 확인<br/>
  `git --version`

  2. 사용자 정보 설정<br/>
      - 사용자 구분을 위한 git 설정<br/>
        `--global` 옵션으로 모든 프로젝트에 설정 적용
      - 콘솔 실행<br/>
        git > git CMD 또는 git bash
      - 사용자 설정<br/>
        `git config --global user.name "사용자 이름"`<br/>
        `git config --global user.email "메일 주소"`
      - 설정확인<br/>
        `git config --list`<br/>
        `git config user.name`
***

## 저장소(Repository)

### 저장소 생성
  1) 로컬 저장소로 저장할 폴더 생성 *(파일탐색기에서 보기-숨긴항목 체크)*
  2) 사용할 폴더 이동 *(cd 디렉토리 경로)*
  3) 새로운 저장소 생성
    `git init`
  4) 해당 폴더에 **.git** 폴더 생성 확인

### .git
  프로젝트 관리를 위한 파일
  해당 프로젝트에만 적용할 config 파일 등
***

## 상태확인

### 상태 확인 <br/>
  - `git status`

### on branch master
  - master라는 기본 가지(branch)

### No commits yet
  - commit한 내역 없음
***

## 주요 명령
### `add`
: 커밋할 목록에 추가<br/>
### `commit`
: commit(히스토리의 한 단위) 만들기<br/>
### `push`
: 현재까지의 내용을 Github에 전달<br/>
<Br/>
Working Directory |add | Index(Stage) |commit | Head Repository
----|:----:|----|:----:|----
작업폴더 |→| 준비영역 |→| 저장소

작업한 내용을 중간에 있는 임시 저장소에 두고<br/>
작업 내용이 확정이 되면 저장소에 저장한다.

추가 *(Untracked files)* 또는 변경 *(Modified files)* 하고자 하는 파일을<br/>
인덱스에 기록 *(Stage)* 후 Staging된 목록만 저장소에 `commit`한다.
***

## 실습
1) 사용할 폴더에 <u>"test.txt"</u> 파일 생성
2) 파일 목록 확인 : "`ls`" 또는 "`dir`" (git은 리눅스 기반이라 ls 사용 가능)
3) 상태 확인(수시 확인) : `git status`
4) 파일을 인덱스에 스테이지 : `git add [파일명]`
5) 전체 파일 스테이지 : `git add .`
6) 상태 확인(수시 확인) : `git stauts`
    스테이지 취소 : `git rm --cached [파일명]`
7) "Changes to be committed."에서 staged 파일 확인
8) 확정 : `git commit -m [설명]`
9) `git commit -a` : add와 commit을 동시에 진행
10) `git log` : history 확인
<br/>
<br/>

### add 취소
  - 선택한 파일 : `git reset HEAD  [파일명]`
  - 전체 파일 : `git reset HEAD`
<br/>
<br/>

### git commit 취소
#### 1) commit을 취소하고 해당 파일들은 staged 상태로 working directory에 보존
    $ git reset -soft HEAD^
#### 2) commit을 취소하고 해당 파일들은 unstaged 상태로 working directory에 보존
    $ git reset --mixed HEAD^   (기본 옵션)
    $ git reset HEAD^           (위와 동일)
    $ git reset  HEAD~2         (마지막 2개의 commit을 취소)
#### 3) commit을 취소하고 해당 파일들은 unstaged 상태로 working directory에서 삭제
    $ git reset --hard HEAD^
<br/>

  ||-soft|-mixed|-hard
  :----:|----|----|----
  **index**|보존<br/>(add한 상태, staged 상태)|취소<br/>(add하기 전 상태, unstaged 상태)|취소<br/>(add하기 전 상태, unstaged 상태)
  **working directory**|보존 (모두 보존)|보존 (기본 옵션)|삭제 (모두 취소)

<br/>

### commit 메시지 변경하기
- `git commit --amend`
- `git commit --amend -m "수정할 commit message"`
***