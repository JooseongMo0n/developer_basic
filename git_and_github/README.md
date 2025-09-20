# Git & GitHub 사용법

## 1. Git & GitHub 정의

**Git:** Project의 분산 버전 관리 시스템(Distributed Version Control System)으로,<br>
내 컴퓨터에서 코드나 파일의 변경 이력을 추적∙관리할 수 있다.

**GitHub:** Git 저장소를 온라인(Cloud)에서 관리하고 협력할 수 있게 해주는 서비스(Platform)이다.<br>
local repository에 있는 project를 cloud에 저장하고, project 을 다른 사람과 공유함으로써 협력시 사용할 수 있다.

<br>

<!--  -->

## 2. Git 기초 사용법(Local)

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

<br>

### git 활용하기

- `git status` (상태 확인)

  - 현재 작업 폴더의 상태와 Staging Area의 상태를 보여준다.
  - 어떤 파일이 수정∙추가∙Commit 되었는지 등을 한눈에 확인할 수 있다.

- `git log` (이력 확인)

  - 지금까지 생성된 모든 commit 목록을 시간 순서대로 보여준다.
  - 각 commit의 작성자, 날짜, commit message 등을 확인할 수 있다.

- `git diff` (변경 내용 비교)

  - 두 commit 사이, 또는 작업 폴더와 commit 사이의 변경 내용을 비교하여 어떤 코드가 추가되고 삭제되었는지 상세히 보여준다.
  - `git diff`: 수정은 했지만 아직 `add`하지 않은 파일의 변경 내용을 보여준다.
  - `git diff --staged`: `add`는 했지만 아직 commit하지 않은 파일의 변경 내용을 보여준다.

- `git restore`

  - 작업 중인 파일을 이전 상태로 되돌린다.
  - `git restore <file name>`: 수정 사항을 취소하고 파일의 원래 내용으로 되돌린다.
  - `git restore --staged <file name>`: staging area에 있는 파일을 staging 전 상태로 되돌린다.

- `git reset` (commit)
  - commit 자체를 되돌리는 강력한 기능이다. 가장 최근 commit을 취소하거나, 특정 commit 시점으로 project 전체를 되돌릴 수 있다.

<br>

<!--  -->

## 3. 독립적인 작업 흐름 (branch)

**branch:** 특정 commit을 가리키는 가벼운 이동 포인터로, 독립적인 개발 흐름을 관리하기 위한 기능이다. <br>

- branch 생성 및 이동

  - `git checkout -b <branch_name>` (새로운 branch 생성)

    - 새로운 branch를 만들고, 해당 branch로 이동한다.
    - 예: `git checkout -b feature/login`

  - `git branch` (branch 목록)

    - local에 존재하는 branch 목록을 보여주고, 현재 내가 위치한 branch에는 별표(\*)를 표시한다.

  - `git checkout <existing_branch>`
    - 이미 존재하는 다른 branch로 이동할 때 사용한다.
    - 예: `git checkout main`

- branch 동기화 및 merge

  - `git push origin <branch_name>`

    - 작업한 local branch를 GitHub에 업로드한다.
    - 예: `git push origin feature/login`

  - `git pull origin <branch_name>`

    - GitHub에 있는 branch의 최신 변경 내용을 local로 가져온다.

  - `git merge <branch_name>`
    - 현재 위치한 branch에 다른 branch의 변경 내용을 합친다.
    - 예: main 브랜치 이동 후, `git merge feature/login`을 실행하면 feature/login의 변경 내용이 main에 합쳐진다.

- branch 삭제
  - `git branch -d <branch_name>`
    - local branch를 삭제한다.
    - d는 'delete'의 약자로, merge가 완료된 branch만 안전하게 삭제한다.
    - 예: `git branch -d feature/login`

<br>

<!--  -->

## 4. GitHub와 Git 연동하기

Local Repository와 Remote Repository 연결

1. GitHub에 new repository를 만들고 주소를 복사한다.

2. `git remote add origin <GitHub 저장소 주소>` 명령어를 입력하여 local repository의 별명(origin)을 등록하여 연결한다.

- `origin`은 remote repository를 가리키는 별명이다. local repo에 remote repo를 등록할 때, default 이름으로 orgin이 붙는다.
- 예를 들어, `git clone https://github.com/user/project.git` 명령어를 입력하면 remote repo 주소인 `https://github.com/user/project.git`이 `origin`으로 등록된다.
- 매번 긴 URL을 사용하는 대신 간단한 이름으로 참조하기 위해 사용한다.

3. git push (코드 올리기)

- local repository의 commit된 내용을 remote repository (GitHub)로 업로드한다.
- `git push origin main` 명령어를 통해 origin repository의 main branch로 코드를 보낸다.

4. git pull (코드 가져오기)

- remote repository의 최신 변경 내용을 내 컴퓨터로 다운로드 한다.
- `git pull origin main` origin repository의 main branch에 있는 최신 코드를 가져온다.
- local에 있는 project를 최신화할 때 사용한다.
- project를 진행하며 수시로 실행하게 된다.

5. git clone (project 폴더 가져오기)

- 새로운 project에 참여하거나, 다른 사람이 이미 만들어 놓은 project를 local computer에 다운로드할 때 가장 먼저 수행한다.
- project를 진행하며 한 번만 실행하게 된다.

<br>

<!--  -->

## 5. 협업하기

- main branch 최신화: 협업하여 project를 진행하는 경우 main branch를 최신화하여(pull) 개발을 시작한다.
- 독립된 branch 사용: project를 진행하며 맡은 기능을 개발할 때, main에서 개발하는 것이 아닌 별도의 branch를 생성해 개발한다.

  - 1. branch 생성(local)
  - 2. code 작성 및 commit(local)
  - 3. remote branch 최신화(remote -> local)

    - 협업 환경에서는 다른 사람이 main이나 develop을 update했을 수 있기 때문에, push 전 pull하여 최신화를 맞추는 게 안전함.
    - 다만 여기서 바로 git pull을 쓰면 충돌이 나기 쉬워 보통은 rebase를 많이 사용한다.
    - `git fetch origin`
    - `git rebase origin/develop`
    - (만약 여기서 충돌이 나면 해결 후 `git rebase --continue`)

  - 4. remote repo(GitHub)에 Push(local -> remote)
  - 5. Pull Request (PR) 생성
    - 팀 내 경험이 많은 개발자가 PR의 code를 검토 후 main branch와 merge한다.
    - 독립 branch를 main branch에 merge하면, local과 remote에 있는 독립 branch를 삭제한다.

업데이트 예정...
