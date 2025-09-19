# Git & GitHub 사용법

## 1. Git & GitHub 정의

- Git: Project의 분산 버전 관리 시스템(Distributed Version Control System)으로,<br>
  내 컴퓨터에서 코드나 파일의 변경 이력을 추적∙관리할 수 있다.

- GitHub: Git 저장소를 온라인(Cloud)에서 관리하고 협력할 수 있게 해주는 서비스(Platform)이다.<br>
  Git을 다른 사람과 공유함으로써, 협력시 사용할 수 있다.

<br>

## 2. Git 사용법(Local)

### git 시작하기

- git init (저장소 초기화)
  - project 폴더를 Git 저장소로 만든다.
  - `git init` 명령어를 입력하면 폴더 안에 `.git`이라는 숨겨진 폴더가 생성되며, 이때부터 버전 관리를 할 수 있다.
- git add (변경 사항 Staging)
  - project에서 변경된 파일들을 Staging Area에 추가한다.
  - `git add <file name>` 명령어로 변경된 파일을 Staging Area에 추가할 수 있다.
  - `git add .` 명령어는 모든 변경 파일을 한 번에 Staging Area에 추가한다.
- git commit (변경 사항 확정)
  - Staging Area에 있는 파일들의 변경 이력들을 하나의 "commit" 단위로 확정하고 .git에 추가한다.
  - `git commit -m "commit message"` 명령어를 통해 어떤 변경을 했는지 명확한 메시지와 함께 commit을 생성한다.
  - commit은 하나의 논리적인 작업 단위로 만드는 것이 중요하다.
    - good commit: 로그인 기능 개발 관련 파일들만 모아 commit, 오타 수정 관련 파일들만 모아 commit
    - bad commit: 로그인, 오타 수정, 네트워크 설정 파일이 섞임

### git 활용하기

<br>

## 3. GitHub와 Git 연동하기

- Local Repository와 Remote Repository 연결
  - GitHub에 new repository를 만들고 주소를 복사한다.
  - `git remote add origin <GitHub 저장소 주소>` 명령어를 입력하여 local repository의 별명(origin)을 등록하여 연결합니다.
  - git push (코드 올리기)
    - local repository의 commit된 내용을 remote repository (GitHub)로 업로드한다.
    - `git push origin main` 명령어를 통해 origin repository의 main branch로 코드를 보낸다.
  - git pull (코드 가져오기)
    - remote repository의 최신 변경 내용을 내 컴퓨터로 다운로드 한다.
    - `git pull origin main` origin repository의 main branch에 있는 최신 코드를 가져온다.

<br>

## 4. 협업하기 (branch & clone)
