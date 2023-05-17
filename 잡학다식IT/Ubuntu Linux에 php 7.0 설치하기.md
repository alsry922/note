
apt(Advanced Package Tool)는 데비안 계열 패키지 관리자입니다.

데비안 계열 리눅스 배포판에서 소프트웨어를 설치하고 제거하는 일을 하며,

소프트웨어 패키지의 확인, 구성, 설치를 자동화함으로써 소프트웨어를 관리하는 작업을 단순하게 만들어 준다고 합니다.

# ✔️Ubuntu 소프트웨어 저장소에서 기본 php 버전 설치하기

apt 명령어를 이용하면 Ubuntu 공식 패키지 저장소(우분투 기본 리포지토리)에 올라와 있는 패키지만 설치 가능합니다.

```bash
sudo apt show php
```

apt 명령을 실행하여 ubuntu 소프트웨어 저장소에 올라와있는 php 버전을 확인할 수 있습니다.

![[Pasted image 20230517103943.png]]

우분투에서 기본으로 제공하는 php를 설치하려면

```bash
sudo apt install php
```

명령을 실행하여 설치할 수 있습니다.

# ✔️ppa를 이용한 다른 php 버전 설치하기

ppa는 Personal Package Archive로 개인 패키지 저장소를 의미합니다.

기본적으로는 런치패드에서 제공하는 우분투 공식 패키지 저장소에 있는 패키지를 다운로드 할 수 있습니다.

하지만 ppa를 사용하면 우분투 공식 패키지 저장소에 없는 서드파티 소프트웨어를 설치할 수 있습니다.

```bash
sudo add-apt-repository 저장소 이름(ppa:user/ppa-name)
sudo apt-get update
sudo apt-get install 패키지 이름
 
# 삭제를 원할 시 
sudo add-apt-repository --remove 저장소 이름
```

저장소를 추가하고 저장소로부터 설치할 수 있는 패키지 리스트를 받아온 후 원하는 패키지를 설치할 수 있습니다.

삭제하고 싶으면 `--remove` 옵션을 통해 삭제할 수 있습니다.

다른 버전의 php를 설치하기 위해 ppa를 추가합니다.

```bash
sudo add-apt-repository ppa:ondrej/php
```

![[Pasted image 20230517105154.png]]

그 다음에 다운로드 할 수 있는 패키지 리스트를 받아옵니다.

```bash
sudo apt update
```

![[Pasted image 20230517105737.png]]

이제 php 5.6, 7.x , 8.0 버전을 설치할 수 있습니다.

원하는 버전을 골라 설치합니다. 저는 7.0이 필요해 7.0을 설치했습니다.

```bash
sudo apt install php7.0
```

설치가 완료되었으면 시스템에서 사용되는 php 기본 버전을 확인해봅니다.

```bash
php -v
```

![[Pasted image 20230517110016.png]]

php 7.0이 잘 설치되었습니다.

# ✔️기본 php 버전 설정하기

지금은 php 7.0으로 기본 버전이 정해져있지만 다른 버전의 php도 설치하고 해당 버전의 php를 기본으로 사용하고 싶을 수 있습니다.

```bash
sudo update-alternatives --set php /usr/bin/php5.6
```

예를 들어 5.6 버전으로 바꾸고 싶다면 `update-alternatives` 명령어로 시스템에서 사용할 기본 php 버전을 설정할 수 있습니다.

다른 버전도 가능합니다.

바꾼 후에는 마찬가지로 `php -v` 를 실행하여 기본 버전이 잘 바뀌었는지 확인합니다.