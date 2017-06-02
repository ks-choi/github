# Github 사용 방법

깃허브 처음 사용하면서 했던 내용들을 개인적으로 보려 간략하게 정리합니다.  
windows 기준으로 작성합니다.

## Git 설치

[Git](https://git-scm.com/) 로 이동하여 우측 하단의 "Downloads for Windows"를 선택하여 설치 파일을 다운받습니다. 현재의 버전은 2.11.1 이네요.  
다운로드 받은 "Git-2.11.0-64-bit.exe" 파일을 실행하여 설치 합니다. 설치관련 설정을 하는 스텝 중 **Adjusting your PATH environment** 에서 전 Git을 프롬프트에서 사용할 것이므로 가운데 **Use Git from the windows Command Prompt** 를 선택하였습니다.  
설치가 완료되면 [Win] + [R] 을 눌러 실행창을 열고

    cmd

를 입력하여 프롬프트를 띄웁니다.  
프롬프트에 다음과 같이 입력하면 설치된 버전이 표시됩니다. 설치는 이상없었는데 **git** 이라는 명령어를 알 수 없다라고 나온다면 재부팅을 한번 해보시기 바랍니다.

    git --version

## Github 가입

[Github](https://github.com/) 로 이동하면 첫 화면에 바로 입력란이 나오는데 회원가입 정보를 입력하는 곳입니다.  
제일 위부터 이름, 이메일, 암호인데 이름은 **https://github.com/[이름]/[저장소명]** 형식으로 URL이 부여되어 영문자 소/대와 숫자, 하이픈(-)만 입력할 수 있습니다.  
**Sign up for GitHub** 를 누르면 Step.2 로 이동되는데 지불관련 내용입니다. 일정 금액($7/월)을 지불하면 저장소를 비공개로 설정가능합니다.  
마지막 스텝에서는 Github 사용계획 등의 정보를 입력받는 화면이니 적절히 선택하고 Submit을 누르면됩니다.  
그럼 입력했던 이메일로 이메일주소 확인 링크가 포함된 메일이 발송됩니다. 링크를 선택하여 최종 완료 단계를 마치게 됩니다.

## Github Repository 생성/삭제

### 생성

[Github](https://github.com/) 로그인 한 후 우측 중앙에 **New repository** 버튼을 누릅니다.  
저장소명과 설명, 공개여부, 기본 README파일 생성 여부를 설정할 수 있습니다. 공개여부는 위 가입에서도 언급했지만 금액을 지불해야 비공개로 설정할 수 있습니다.

### 삭제

삭제하려는 repository로 이동합니다. 상단 탭 중 **Settings** 탭을 누른 후 이동되는 화면에서 제일 밑에 있는 **Delete this repository** 를 선택합니다.  
입력란이 하나 나오는데 삭제 하려는 저장소명을 입력한 후 **I understand the consequences, delete this repository** 버튼을 선택하면 삭제됩니다.

## Github Repo 관리

### 소스 업로드

처음 업로드 할 경우 다음 순서를 따릅니다.

 1. 프롬프트 창에서 업로드할 프로젝트 폴더로 이동합니다. (바탕화면의 "컴퓨터" 같은 탐색기로 프로젝트 폴더로 이동한 후 [쉬프트] + [마우스 우클릭] 하여 "여기서 명령 창 열기" 를 선택해도 됩니다.)

    c:\> cd "이동할 폴더 경로"

    예)
    cd c:\repo\github-guide

 2. 프롬프트 창에서 아래 코드를 입력하여 신규로 생성한 저장소와 연결시킵니다.

    // git 연동을 위한 초기화
    git init

    // 사용자 정보 설정
    git config --global user.name "<이름>"
    git config --global user.email <이메일>

    // github 원격 저장소 경로 등록
    git remote add origin <URL>
    예)
    git remote add origin https://github.com/ks-choi/github

 3. 파일을 추가하고 업로드 합니다.

    // Stage에 추가 (업로드 할 파일을 등록한다고 생각하면 됨)
    git add <filename>
    예 1) 특정파일: git add README.md
    예 2) 전체파일: git add *

    // Local에 추가
    git commit -m "<메시지>"
    예) git commit -m "first commit"

    // Remote Repository에 업로드
    git push origin master

## Git CLI 정리

    // 프로젝트를 처음 생성했을 때 초기화
    git init

    // 원격서버에서 파일 다운
    git clone <URL>

    // 파일 상태 확인
    git status

    // 커밋 로그 확인
    git log

    // commit 하기 위한 파일 추가
    git add <파일 또는 경로>

    // local에 저장
    git commit -m "<메시지>"

    // 원격서버로 commit 내용 보냄
    git push origin master

    // local에서 복원
    git checkout <파일 또는 경로>

    // 파일 차이점 확인
    git diff [HEAD] // (기본)최신 HEAD와 비교
    git diff HEAD~2 // 2번째 전 HEAD와 비교
    git diff <대상1> <대상2> // 대상1과 대상2 비교. 대상2가 더 최신이어야 함.

    // 브랜치 생성
    git branch [옵션] <브랜치명> // 옵션 : [-d:삭제]

    // 브랜치 변경
    git checkout <브랜치명> // 기본은 mater를 바라보고 있음. 브랜치 생성과 변경을 동시에 하고 싶다면 "git checkout -b <브랜치명>" 를 사용

    // 브랜치 확인
    git branch // 브랜치 목록이 나오며 현재 브랜치는 * 로 표기됨

    // 브랜치 master에 적용(합치기)
    git checkout master // 마스터로 이동
    git merge <브랜치명> // master와 브랜치 합침

## .md(mark down)파일 마크업 관련

 1. [tchap markdown-cheatsheet](https://github.com/tchapi/markdown-cheatsheet/blob/master/README.md)
 2. [나무위키](https://namu.wiki/w/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4)

## 참고

 1. [git-scm](https://git-scm.com/book/ko/v2) : Git 관련 전체 설명



| 1 | 사용 안 함
|---|------------
| 2 | SMS(12원)
|---|------------
| 3 | LMS(30원)
