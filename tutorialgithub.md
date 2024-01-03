# Github를 활용하여 연습하기

## 들어가기 앞서...
- Github, Gitlab 등 다양한 서드파티들이 존재하나, 걱정하지 말아야할 것은 **Git 명령어는 다르지 않다.**
    - 한마디로, 지금 사용하는 명령어로 Github든 Gitlab이든 동일하게 동작한다는 의미

## 레포지터리 생성
### 레포지터리란?
- 하나의 단위인데, 간단하게 말하면, 하나의 프로젝트 단위를 의미한다.
### 방법
1. [다음 링크](https://github.com/)에 들어가서, Github에 진입한다.
![github main](/img/github%20main.png)
2. 위의 이미지대로 나왔다면, 오른쪽 위 프로필 사진을 클릭하여, 자기 프로필로 들어가도록 한다.
![github repos](/img/github%20repositories.png)
3. 이후, Repositories를 클릭하여, 위의 이미지처럼 되도록 한다. 제대로 되었다면, New 버튼을 클릭하여, 새 레포지터리를 생성하도록 한다.
![create repos](/img/github%20create%20repository.png)
4. Repository Name에 프로젝트명을 입력하고, Descritpion에는 설명을 하고, 이후 해당 레포지터리를 공개/비공개 할 것인지 선택하고, Create Repository를 클릭한다.
![create repo success](/img/create%20repo%20success.png)
5. 위에처럼 나온다면, 성공적으로 생성하는데 성공하였다.

## Git Author(작성자) 설정
```bash
git config --global user.name "{이름}"
git config --global user.email "{이메일 주소}"
```
- 다음 명령을 터미널 또는 쉘을 열어 실행한다. 이름과 이메일 주소는 자기 것으로 변경하면 된다. 밑은 예시이다.
```bash
git conig --global user.name "Nakada Tokumei"
git config --global user.email "nakada_tokumei@protonmail.com"
```
- 해당 설정된 Name과 Email로 커밋에 등록되니, 주의해서 살펴볼 것을 요망

## 로컬 Git 생성 및 원격 연결
### 진행하기 앞서...
- 우리는 위에서 레포지터리를 생성하는데 성공하였다. 하지만, 저 레포지터리는 서버에서만 저장되어있기에, 서버에 있는 레포지터리를 원격으로 제어해주도록 설정해주어야한다.
- 이번 섹션은 로컬에서 Git을 생성 후, Github와 원격으로 연결 시켜주는 작업을 해주도록 하는 과정이다.
### 방법
- 리눅스라면 bash/zsh와 같은 쉘을 윈도우라면 Powershell 혹은 Git Bash를 연다.
- 이후 프로젝트가 있는 경로로 접근한다.
![터미널 화면](/img/terminal.png)

#### Git 레포지터리 초기화
- 다음 명령어를 사용해서, 레포지터리를 초기화한다.
- 해당 명령어는 단순하게 현재 경로에 Local Repository를 초기화하는 작업이다.
```
git init
```
- 아래 이미지처럼 나온다면 정상적으로 동작
![Init Git](/img/Init%20Git.png)
##### 주의사항
- 레포지터리를 Clone하거나, 이미 생성된 Local Repository라면 생성이 되지 않는다.
#### Commit
- Git의 레포지터리 같은 경우, 변경 사항을 **Commit** 단위로 잡는다.
    - 즉, 변경사항들이 Git에 적용되는 한 번이 1 Commit이다.
- 변경사항은 자동으로 적용되는 것이 아니기에, 직접 변경사항을 적용해주도록 해야한다.

##### 예시
- [Project Manna Commits](https://github.com/NakadaTokumei/Manna/commits/main/)
- [libnopanic Commits](https://github.com/NakadaTokumei/libnopanic/commits/main/)

##### 변경사항 확인
- 해당 명령어는 변경사항 확인을 위한 명령어일 뿐이고, 필요에 따라 사용해도 되는 Optional이다.
- 해당 명령어를 입력하면, 어떤 파일들이 추가 수정되어, 적용이 되었는지 안 되었는지 확인할 수 있다.
```bash
git status
```
- Commit이 안 되어있으면, 밑에 이미지처럼 Commit이 안 되어있는 파일들이 나온다.
![git Status](/img/Git%20Status.png)

##### 변경 사항 적용
- 이 명령은 Commit을 진행할 때, 어떤 변경된 파일을 Commit에 적용할 것인지 정하는 명령어이다.
```bash
git add {파일|폴더}

git add test.txt  // test.txt만 적용
git add .         // 현재 위치해있는 폴더 전체 적용
```
- 정상적으로 추가가 되었다면, git status를 입력하였을 때, 다음과 같이 나옴
![git add](/img/git%20add.png)
##### 커밋 진행
- 이 명령은 변경 사항 적용이후, Commit 진행할 때 쓰인다.
- add는 변경 사항들을 선택한다고 생각하면 되고, Commit은 선택된 변경 사항을 히스토리에 올림으로써, 버전을 표시하는 역할이라고 표현할 수 있다.
```bash
git commit
```

- 명령어가 실행되면, 다음과 같은 화면 나옴
![Commit](/img/Commit%201.png)

- 윈도우 같은 경우 vim이 기본이라, vim 명령어 외울 필요 있음
    - i : 수정 모드
    - o : 한줄 내림 후 수정 모드
    - esc : 모드 해제
    - :wq : 저장 후 종료
    - :W : 저장
    - :q : 종료
- 리눅스 같은 경우 기본 텍스트 에디터가 다를 수 있기에, 주의 필요
- 해당 창은 메시지를 작성하는 부분으로, 제목은 필수, 설명은 Optional이다.
- \#은 주석 부분이라, 메시지는 \# 바로 다음 라인부터 적용. 밑은 예시
```bash
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
#
# Initial commit
#
# Changes to be committed:
#       new file:   ReadME.md
#       new file:   test.c
#
[Init] Repository Init # Head(제목)
                       # 무조건 한줄 비워야함
1. BlaBlaBlaBla        # Body(내용)
2. BlaBlaBla
3. BlaBlaBlaBlaBla
```

- 저장 후 종료가 제대로 된다면, 아래 이미지처럼 나와야 성공
![git Commit](/img/Commit%202.png)

#### 원격 연결 Remote
- 갑작스럽게 깃랩으로 틀어져서 당황하실 수 있지만, 당황 마시길 바랍니다.
- **\*주의\*** 해당 섹션은 제일 기본적인 토큰 인증 방식을 기반으로 작성되었음을 미리 알립니다.
##### 토큰 생성
- Git은 2021 ~ 2022년 부터 패스워드 방식의 인증방식을 제거하고, 인증 토큰 방식을 도입
- 아이디/패스워드 형식으로 아이디는 Gitlab에 있는 Username, 즉 아이디와 동일. 하지만 패스워드는 계정의 패스워드가 아닌, 생성한 토큰으로 진행해야한다.

1. 오른쪽 프로필 사진 클릭 후, Edit Profile 클릭
![Generate Token](/img/Token%20Gen%201.png)

2. 클릭 후 나오는 화면에서, Access Tokens 클릭
![Generate Access Token](/img/Token%20Gen%202.png)

3. 토큰 생성 창이 나오는데, 토큰 이름이랑 필요한 권한 클릭 후 설정 토큰 생성 (왠만하면, 권한은 read, write repo만 추천)
![Generate Access Token 3](/img/Token%20Gen%203.png)

4. 생성이 성공하면, 위에 토큰 값이 생성. 해당 토큰은 다시 볼 수 없기 때문에, 저장 필요
![Generate Access Token 4](/img/Token%20Gen%204.png)

##### Main branch 전환
- 현재 Branch를 main(master)로 설정해줘야한다.
```
git branch -M main
```

##### 원격 설정
- 이제 서버에 있는 레포지터리의 주소를 연동하여, 로컬과 원격을 연결 시켜주도록 한다.
- 기본적인 명령어는 아래와 같다.

```
git remote add origin {git repo url}
```

- url은 어려울 것 같지만, 제일 간단한 방법은 자기 레포지터리에 접근한 후, url을 복사 후 붙여넣은 다음 맨 뒤에 .git만 붙이면 된다. 밑에는 예시

```
브라우저 상 레포지터리 주소: https://github.com/NakadaTokumei/Hello-Git
원격 레포지터리 주소: https://github.com/NakadaTokumei/Hello-Git.git
```

##### 원격 레포지터리에 Push(전송)
- 다음 명령어를 통해서, 로컬에서 커밋한 내용을 원격 레포지터리에 반영할 수 있다.

```bash
git push -u origin main # 레포지터리 생성 후 처음 한번만 입력
git push                # 이후 다음과 같이 입력해도 동일하게 적용
```

- 만약 올바르게 원격 설정이 되었다면, 아이디 / 패스워드 창이 뜰 것이다.
- 아이디는 현재 Gitlab에서 사용 중인 Username, 패스워드는 아까전에 저장해둔 토큰을 붙여넣기 하면된다.
- 만약 올바르게 적용하였다면, 아래와 같이 push 진행
![Git push](/img/git%20push.png)

- 제대로 나오면, 원격 레포지터리 확인 했을 때, 적용이 된 것이 확인된다.
![rEMOTE REPO](/img/Remote%20Repo.png)

#### 레포지터리 불러오기
- 다음 명령어를 통해서, 원격 레포지터리를 로컬로 가져올 수 있다.

```
git clone {.git url}
```

- 이미 레포지터리가 구상하였기 때문에, git remote나, git init과 같은 과정을 할 필요없이, add, commit 그리고 push, 업데이트 되면 pull과 같은 방식으로 진행하면 된다.