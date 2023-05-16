# ✔️NVM

nvm은 node.js 버전 매니저다.

nvm을 사용하면 쉽고 빠르게 node.js 버전을 설치하고 

사용하고 있는 node.js 버전을 설치된 node.js 버전 중 다른 버전으로 바꿀 수도 있다.

nvm은 POSIX-compliant shell이면 다 동작한다.

대표적으로 unix, macOS, windows WSL에서도 동작한다.

https://github.com/nvm-sh/nvm#intro

자세한 정보는 깃허브에서 확인할 수 있다.

나는 ubuntu 20.04 LTS 버전에서 nvm을 설치할 것이다.

## 📌설치 & 업데이트

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```
```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

위 명령어를 실행하면 nvm을 설치 혹은 업데이트가 가능하다.

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
nvm -v
```

입력하여 nvm 버전을 확인하여 설치됐는지 확인할 수 있다.

### 👉trouble shooting

nvm을 설치 후에 `nvm -v` 를 입력했을 때 `nvm: command not found` 커맨드를 찾을 수 없거나 아무런 반응이 없는 경우가 있을 수 있다.

나는 nvm 명령어를 인식하지 못했다.

간단히 껐다 켜서 버전 확인을 해보거나  `source ~/.bashrc` 를 명령줄에 입력하면 해결할 수 있다.

나는 bash shell이어서 이 명령어를 썼지만 zsh나 다른 shell을 쓰는 경우 다른 명령어를 입력해야 한다.

https://github.com/nvm-sh/nvm#troubleshooting-on-linux

여기서 자세히 확인할 수 있다.

