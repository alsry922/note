Ubuntu Linux에 MariaDB를 설치하려가 겪은 에러에 대해 포스팅하려고 합니다.

이것 때문에 거의 하루를 날렸는데, 같은 현상을 겪는 분들께 도움이 되었으면 합니다.

# ✔️MySQL 설치가 되어있었다.

기존에 MySQL을 설치한 적이 있습니다.

따라서 MySQL을 삭제하고 MariaDB를 설치하려고 하였는데, MariaDB설치가 제대로 되지 않고 자꾸 에러가 발생하였습니다.

```bash
sudo apt remove mysql-server
```

`apt remove` 를 이용해서 삭제하였는데

`apt remove` 는 패키지만 삭제하는 명령어입니다.

`apt purge` 는 패키지 뿐만 아니라 관련된 모든 구성 파일까지 삭제해줍니다.

단 두 명령 모두 사용자의 홈 디렉토리 아래에 있는 응용프로그램 파일은 건드리지 않습니다.

따라서 MySQL 완전 삭제를 위해 다음과 같이 진행하였습니다.

`apt purge` 를 이용해서 mysql을 삭제합니다.

```bash
sudo apt purge mysql-server
```

삭제 후 mysql 관련 패키지가 있는지 확인하여 있다면 마저 삭제해줍니다.

```bash
sudo dpkg -l | grep mysql*
```

❓dpkg(링크)

명령줄에 위와 같이 입력하여 관련 패키지를 확인할 수 있습니다.

mysql이 들어간 파일이나 폴더를 검색해 삭제합니다.

```bash
# 현재 및 서브 디렉토리를 검색하여 mysql가 들어간 파일을 찾는다 
find . -type f -name *mysql*
# 모든 디렉토리를 검색하여 mysql가 들어간 파일을 찾는다 
find / -type f -name *mysql*
```

❓find(링크)

type을 `d` 로 해서 파일이 아닌 디렉토리를 찾을 수도 있습니다.

`autoremove` 는 의존성 때문에 설치됐지만 지금은 쓰이지 않는 패키지들을 삭제해줍니다.

혹시라도 있을 수 잇으니 `autoremove` 를 이용해 삭제해줍시다.

```bash
sudo apt autoremove
```

이렇게 완전 삭제를 마치고 다시 MariaDB를 설치하면 될 줄 알았습니다...

# ✔️95 진행에서 설치가 멈추고 timeout 발생

```bash
sudo apt install mariadb-server
```

MariaDB 설치를 진행 중 진행도 95에서 멈춘 후에 더 이상 진행되지 않았습니다.

한참을 기다리고 나서 timeout이라고 뜬 후 설치가 마무리 되었습니다.

MariaDB 실행 상태를 확인하였습니다.

```bash
sudo systemctl status mariadb
```

확인해보니 실행중이 아닌 상태여서 MariaDB를 실행했지만 Activating 상태에서 넘어가지 않았습니다.

한참을 삭제와 설치, 검색을 반복하다가 찾은 글이 있습니다.

https://bugs.launchpad.net/ubuntu/+source/mariadb-10.1/+bug/1806263
https://askubuntu.com/questions/1216498/why-does-mariadb-installation-last-for-a-long-time
https://mariadb.com/kb/en/the-community-mariadb-troubles-only-running-after-reboot-times-out-when-try/

완전히 도움이 된 글은 런치패드의 버그 리포트였습니다.

나머지 글 들은 비슷한 증상이라고 생각되어 나중에 참고할 목적으로 남깁니다.

![[images/에러핸들링/Ubuntu Linux MariaDB 설치 에러/1.png]]

버전은 다르지만 증상은 같은 증상이었습니다.

설치에서도 문제가 있었지만 설치가 제대로 되지 않은 상태에서 MariaDB 실행 상태를 확인할 때 저 상태였기 때문입니다.

이유는 MySQL 제거 후 MariaDB를 설치했을 때 잘못된 AppArmor 프로필로 인해 MariaDB가 실행되지 않는다는 것이었습니다.

직접 /etc/apparmor.d/usr.sbin.mysqld 이 부분을 삭제하여 해결하거나(?)
	-> 이 부분은 시도해보지 않았지만 삭제하면 해결이 될 것 같습니다.

간단하게는 댓글에 있던 MySQL 완전 삭제 후 시스템을 다시 시작하면 MariaDB가 올바르게 설치된다는 것이었습니다.

따라서 MySQL 삭제 후 MariaDB를 다시 설치하였습니다,

![[images/에러핸들링/Ubuntu Linux MariaDB 설치 에러/2.png]]

드디어 설치가 완료되었습니다....ㅠㅠ

MariaDB설치와 설정 완료 포스팅을 확인해보세요

감사합니다.