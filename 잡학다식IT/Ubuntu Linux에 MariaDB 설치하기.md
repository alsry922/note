
포스팅하는 Ubuntu 버전은 20.04 LTS 버전입니다. 참고하시기 바랍니다.

# ✔️MariaDB

MariaDB는 오픈 소스의 관계형 데이터베이스 관리 시스템(RDMBS)입니다.

MySQL과 동일한 소스 코드를 기반으로 하며, GPL v2 라이센스를 따릅니다.

여담이지만,

MySQL을 오라클에서 사고 나서 MySQL을 무료로 사용할 수 있도록 만들고자 했던 개발자들이 오라클의 상업 라이센스에 반발하여 나와 만든 RDBMS라고 들었습니다.

역시 수업은 중요한 건 기억 안 나고 재밌는 잡담만 기억이 나는 법인 것 같습니다.

# ✔️MariaDB 설치하기

우선 우분투 패키지 저장소에서부터 미리 업데이트할 패키지 리스트를 받아옵니다.

```bash
sudo apt update
```

mariadb-server를 설치합니다.

```bash
sudo apt install mariadb-server
```

기본적으로 mariadb 설치 후 mariadb가 기본적으로 실행됩니다.

mariadb가 실행중인 상태인지 확인합니다.

```bash
sudo systemctl status mariadb
```

혹시라도 실행중이 아니라면 mariadb를 실행합니다.

```bash
sudo systemctl start mariadb
```

MariaDB 계정과 보안 설정 등을 하는 스크립트를 실행합니다.

```bash
sudo mysql_secure_installation
```

root 비밀번호 입력여부
![[images/잡학다식IT/Ubuntu Linux에 MariaDB 설치하기/1.png]]

root 비밀번호 변경 여부
![[images/잡학다식IT/Ubuntu Linux에 MariaDB 설치하기/2.png]]

anonymous 사용자 삭제 여부
![[3.png]]

원격 root 로그인 비허용 여부
![[4.png]]

testdb 삭제 여부
![[5.png]]

변경 내용 즉시 반영 여부
![[6.png]]

설정이 완료됐다면 mariadb가 잘 실행중인지 다시 확인해봅니다.

```bash
sudo systemctl status mariadb
```

MariaDB 10.3부터 root user 인증이 비밀번호 인증 말고 `unix_socket` 인증으로 세팅되어 있다고 합니다.

보안성이 높아지지만 외부 프로그램에 관리 권한을 허용해야 하는 경우 복잡해질 수 있다고 합니다.

하지만 root 계정의 인증 방식이나 인증 세부 정보를 변경하는 것을 추천하지 않습니다.

구성 파일  `/etc/mysql/debian.cnf`  자격 증명을 변경하면 처음에는 작동하지만 나중에 패키지 업데이트가 이루어지면 위 내용을 덮어쓸 수도 있습니다.

그래서 추천하는 방법은 root 계정 말고, 관리자 권한을 가지고 비밀번호로 인증할 수 있는 새로운 관리자 계정을 추가하는 것입니다.

```bash

GRANT ALL ON *.* TO ['admin']@'localhost' IDENTIFIED BY ['password'] WITH GRANT OPTION;
FLUSH PRIVILEGES;

exit
```

괄호 친 부분이 계정 이름과 비밀번호입니다. 적절히 바꿔서 설정합니다.

새로 생성한 계정과 비밀번호로 접근이 가능한지 확인합니다.

```bash
sudo mysql -u admin -p;
```

# ❓참조

https://www.digitalocean.com/community/tutorials/how-to-install-mariadb-on-ubuntu-20-04
https://blogger.pe.kr/885

https://jjeongil.tistory.com/1965
https://it.gwangtori.com/42
https://velog.io/@shin6949/mariaDB-%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%B4%88%EA%B8%B0-%EC%84%A4%EC%A0%95-Ubuntu#%EC%99%B8%EB%B6%80-ip%EC%97%90%EC%84%9C%EC%9D%98-%EC%A0%91%EC%86%8D%EC%9D%84-%ED%97%88%EC%9A%A9%ED%95%98%EA%B3%A0-%EC%8B%B6%EC%9D%80-%EA%B2%BD%EC%9A%B0
https://www.nemonein.xyz/2019/07/2254/

하이디 sql, workbench
https://allonsyit.tistory.com/14
https://enjoydevelop.tistory.com/108