
이전 포스팅과 이어집니다.

# ✔️ Git 설치하기

Git에 대해 대충 알아봤으니 Git을 설치해봅시다.

저는 windows 환경이라 git-for-windows에서 Git을 다운로드 하겠습니다.

https://gitforwindows.org/

여기서 다운로드 하실 수 있습니다.

windows에서 설치하시면 알다시피 여러 설정들을 하기 위해 next를 계속 눌러야합니다.

그런데 그냥 기본 설정으로 두고 계속 next를 눌러서 설치해도 사용하는데 별 무리가 없습니다.

Git 설치가 완료되었으면 Git bash 또한 설치되었을 것입니다.

windows 환경이지만 bash가 저는 좀 더 친숙하기도 해서 앞으로의 포스팅에서도 Git bash를 사용할 것입니다.

Git 설치가 잘 되었는지 확인하기 위해 Git bash를 열고 `git -v` 를 입력해봅니다.

![[git -v.png]]

# ✔️git config

Git을 설치했으면 Git을 사용하는 사람은 누구인지 username과 email을 설정해줘야 합니다.

해당 설정 과정을 거쳐야 나중에 commit을 남길 때 누가 이 commit을 남겼는지 알 수 있습니다.

이를 위해 특별한 계정이 필요한 것은 아닙니다. 그냥 사용하고 싶은 username과 email을 사용하면 되며, 나중에도 바꿀 수 있습니다.

저는 보통 Github에서 사용하는 username과 email로 설정합니다. 꼭 이렇게 하지 않아도 됩니다. 

하지만 email은 Github 계정을 만들 때 사용한 email로 설정하는 걸 추천합니다.

```bash
git config --global user.name "alsry922"
git config --global user.email "alsry922@gmail.com"
```

잘 설정되었는지 확인해봅니다.

```bash
git config --global --list
```

![[git config --global --list.png]]

git config 설정에는 여러 옵션이 있습니다.

`git config --system` 

`git config --global`
- ~/gitconfig 파일이 global로 적용한 설정이며, 특정 사용자(계정)의 모든 git repository에 적용됩니다.

`git config --local`
- .git/config 파일이 local로 적용한 설정이며 특정 git repository로 이동하여 local 옵션을 통해 local 설정이 가능하고 해당 git repository에서만 이 설정이 적용됩니다.

`git config` 에 대한 더 자세한 정보는 아래 주소에서 확인할 수 있습니다.

https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup

```bash
git config --global core.editor "사용할 editor"
```

위처럼 git에서 기본으로 사용할 editor를 설정할 수도 있습니다.

windows에서는 editor의 전체 경로를 입력해주어야 합니다.

# ✔️git init, git status

`git init` 명령어를 통해 현재 디렉토리를 git repository로 만들 수 있습니다.

`git init` 을 실행하면 현재 디렉토리에 .git 디렉토리가 생기며, 깃이 이 디렉토리 내의 모든 변화를 탐지하고 추적하게 됩니다.

만약 이 디렉토리가 git repo가 아니게 되도록 하고 싶다면 간단히 이 .git 디렉토리를 삭제하면 됩니다.

`git status` 명령어를 통해 현재 repo에 생긴 변화를 파악할 수 있습니다.

`git status` 를 수행한 경로가 repo가 아닌 경우 에러를 출력해줍니다.

![[git status before init.png]]

현재 디렉토리를 git repo로 만들어 줍니다.

![[git init.png]]

git init을 수행하고 .git 디렉토리가 생성되었습니다.

```bash
git status
```

![[git status after init.png]]

git repo로 만든 후 아직 아무것도 하지 않았기 때문에 commit할 변경사항이 없다고 나옵니다.

# ✔️정리

지금까지 Git 설치와 설정 및 간단한 명령어에 대해 알아봤습니다.