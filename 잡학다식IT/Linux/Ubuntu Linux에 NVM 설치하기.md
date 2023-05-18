# ✔️NVM

nvm은 node.js 버전 매니저다.

nvm을 사용하면 쉽고 빠르게 node.js 버전을 설치하고 

사용하고 있는 node.js 버전을 설치된 node.js 버전 중 다른 버전으로 바꿀 수도 있다.

nvm은 POSIX-compliant shell이면 다 동작한다.

Windows에서도 사용할 수 있는데, git bash를 사용하거나 WSL를 통해 사용할 수 있다.

그 외에는 nvm-windows를 따로 설치하거나 몇 가지 방법이 추가로 있는 것으로 알고 있다.

자세한 정보는 깃허브에서 확인할 수 있다.

나는 ubuntu 20.04 LTS 버전에서 nvm을 설치할 것이다.

## 📌설치 & 업데이트

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```
```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

위 명령어를 실행하면(둘 중 하나로) nvm을 설치 혹은 업데이트가 가능하다.

wget과 curl을 명령어를 실행할 수 있어야 한다.

혹시라도 없으면

```bash
sudo apt get wget
```
혹은
```bash
sudo apt get curl
```

실행해서 설치하자.

nvm 설치 후

```bash
command -v nvm
```

위 명령어를 입력하여 출력으로 nvm이 나오는지 확인하거나

```bash
nvm -v
```

입력하여 nvm 버전을 확인하여 설치됐는지 확인할 수 있다.

### 👉trouble shooting

nvm을 설치 후에 `nvm -v` 를 입력했을 때 `nvm: command not found` 커맨드를 찾을 수 없거나 아무런 반응이 없는 경우가 있을 수 있다.

나는 nvm 명령어를 인식하지 못했다.

간단히 터미널을 껐다 켠후 다시 버전 확인을 해보거나  아니면 `source ~/.bashrc` 를 명령줄에 입력하면 해결할 수 있다.

나는 bash이어서 이 명령어를 썼지만 zsh나 다른 shell을 쓰는 경우 다른 명령어를 입력해야 한다.

https://github.com/nvm-sh/nvm#troubleshooting-on-linux

여기서 자세히 확인할 수 있다.

## 📌자주 사용하는 명령어

- 최신 버전의 노드 다운로드

```bash
nvm install node # "node" is an alias for the latest version
```

nvm에서 `node` 를 최선 버전의 노드 alias로 갖고 있다.

- 특정 버전을 다운로드

```bash
nvm install 14.7.0 # or 16.3.0, 12.22.1, etc
```

설치된 버전이 사용하는 노드의 기본 버전이 된다.

- 설치 가능한 노드 버전 확인

```bash
nvm ls-remote
```

`nvm ls-remote --lts` 옵션을 추가하면 long term support 버전만 확인해볼 수 있다.

내가 설치한 노드 버전들을 확인하고 싶으면 `-remote` 를 빼주자.

- 노드 사용하기

```bash
nvm use node
```

기본으로 정해진 버전의 노드를 사용하게 된다.

특정 버전을 실행하고 싶으면 추가로 버전을 명시하면 특정 버전을 사용할 수 있다.

- 설치된 노드가 어느 경로에 있는지

```bash
nvm which 12.22
```

- 기본으로 사용되는 노드 버전 바꾸기
```bash
nvm alias default v14.20.0
```

기본으로 사용할 노드 버전을 바꿀 수 있다.

일단 이 정도만 알고 있어도 사용하는데 크게 문제가 없을 것 같다.

자세한 정보는 nvm 깃허브 링크를 남길테니 여기서 확인해보시길 바랍니다.

https://github.com/nvm-sh/nvm

