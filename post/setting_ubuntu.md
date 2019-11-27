# VM 포트 설정
VM(Oracle VM VirtualBox)에 설치 했다면 NAT Network로 설정 해서 포트 포워딩을 해야 한다.
아래 순서대로 따라 하면 된다.

1. 환경 설청 창을 열기 : 파일 -> 환경설정 (Ctrl + G)
2. 네트워크 항목 선택
3. 새 NAT 생성
![새 NAT 생성](./img/nat_setting01.PNG)
4. 생성된 NAT 더블 클릭 하여 포트 포워딩 설정
![포트포워딩](./img/nat_setting02.PNG)
---
# Ubuntu 셋팅
#### 설치가 끝났으면 우분투 업데이트와 업그레이드를 해야 한다.
```
sudo apt-get update
sudo apt-get upgrade
```

### SSH Server 설치
우분투에 `SSH Server`를 설치 하여 외부에서 접속 가능 하도록 셋팅 하자.
우분투 명령 프롬프트 창에 아래와 같이 입력 한다.
```
sudo apt-get openssh-server
```

### SSH 접속
```
터미널에서 ssh [user name]@[host name] 을 입력하면 연결 가능 하다.
사용자 이름이 zman 이고 주소가 0.0.0.0 이라면 아래와 같이 입력 한다.
ssh zman@0.0.0.0
```

### NPM, NodeJS 설치
```
sudo apt-get install npm
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
```
### MongoDB 설치 및 실행
```
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -

sudo apt-get install gnupg

wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -

echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list

sudo apt-get update

sudo apt-get install -y mongodb-org

echo "mongodb-org hold" | sudo dpkg --set-selections
echo "mongodb-org-server hold" | sudo dpkg --set-selections
echo "mongodb-org-shell hold" | sudo dpkg --set-selections
echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
echo "mongodb-org-tools hold" | sudo dpkg --set-selections

npm install mongoose

sudo service mongod start

```
