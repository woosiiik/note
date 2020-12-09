# Shell Script

## SSH

### 원격서버에 명령어 실행하기 (로컬에서)

ssh [server] < [원격서버에서 실행될 명령어를 가지고 있는 스크립트 파일]

```shell script
$ ssh resource02 < ./run.sh 
```

여기서 run.sh 파일은 로컬에 있는 파일이다.

## sshpass
ssh를 이용하는 위와같은 방법은 ssh접속시 비밀번호를 물어보는 경우 사용할 수 없다.  
이때는 pem파일을 이용해서 비밀번호를 입력하지 않고 접속하는 방법과, sshpass를 이용해서 비밀번호를 입력하는 방법이 있다.  
여기서는 sshpass를 이용하는 방법에 대해 설명한다.  

**sshpass설치**
```shell script
$ brew install hudochenkov/sshpass/sshpass
```

**scp로 파일 업로드**   
sshpass -p [비밀번호] scp [업로드할파일] [계정]@[IP]
```shell script
$ sshpass -p 'pass-string' scp resource2.zip woosik@10.8.28.100:~/
```

**원격서버에 명령어 실행하기**  
sshpass -p [비밀번호] ssh [계정]@[IP] < [원격에서 실행될 명령어를 가지고 있는 스크립트 파일]
```shell script
$ sshpass -p 'pass-string' ssh woosik@10.8.28.100 < woosik_up_sh.sh
```
위와 같이 하면 10.8.28.100 서버에서 로컬에 있는 woosik_up_sh.sh 파일의 내용이 실행 된다. 
