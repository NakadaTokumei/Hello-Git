# Git 어렵지 않아요

## 설치
### Windows
1. [해당 링크](https://git-scm.com/)로 들어간다.
\
![Git Downloads](/img/Git%20Download.png)
2. Download For Windows를 클릭한다.
3. 다운이 전부 완료되면, 설치를 진행한다.
### Linux
- **~~나는 리눅스를 쓰고 싶은 변태가 아니라면, 굳이 볼 필요 없음~~**
#### Ubuntu
```bash
sudo apt-get update
sudo apt-get install git 
```
#### Fedora
```bash
sudo dnf update
sudo dnf install git 
```
#### openSUSE
```bash
sudo zypper update
sudo zypper install git 
```

## 작동 시작
### Git 확인
1. Git Bash 혹은 Powershell을 연다. \
![Git bash](/img/git%20bash%20확인.png)
2. 다음 명령어를 입력한 후, 버전이 제대로 출력하는지 확인하도록 한다.

```bash
git --version
```
![Git Version](/img/버전%20확인.png) 
3. 위의 이미지와 동일한 버전이 아니더라도, 버전이 출력되면, 정상적으로 설치 완료 
