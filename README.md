# 프로젝트 개요

터미널, Docker, Git, GitHub를 직접 활용해 개발 워크스테이션을 구성하고, 누구나 비슷한 환경을 다시 만들 수 있도록 재현 가능한 개발 환경을 익히는 것이 목적입니다.

## 실행 환경

- OS: Windows 11
- Shell: bash
- Terminal: WSL Ubuntu, VS Code 통합 터미널
- Docker: 29.9.2
- Git: 2.53.0

## 수행 항목 체크리스트

- [x] 터미널 조작
- [x] 권한 실습
- [x] Docker
- [ ] Dockerfile
- [ ] 포트
- [ ] 마운트
- [ ] 볼륨
- [ ] Git
- [ ] GitHub

## 터미널 조작 로그 기록

### 현재 위치 확인

```
developer@****:/mnt/c/Users/****/dev-workstation$ pwd
/mnt/c/Users/****/dev-workstation
```

### 목록 확인 (숨김 파일 포함)

```
developer@****:/mnt/c/Users/****/dev-workstation$ ls -al
total 0
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 .
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov  7 17:36 README.md
```

### 생성 (폴더 + 이동 + 빈 파일)

```
developer@****:/mnt/c/Users/****/dev-workstation$ mkdir practice
developer@****:/mnt/c/Users/****/dev-workstation$ cd practice
developer@****:/mnt/c/Users/****/dev-workstation/practice$ touch test.txt
```

### 파일 내용 확인

```
developer@****:/mnt/c/Users/****/dev-workstation/practice$ cat test.txt
```

### 복사

```
developer@****:/mnt/c/Users/****/dev-workstation/practice$ cp test.txt test_copy.txt
```

### 이동/이름 변경

```
developer@****:/mnt/c/Users/****/dev-workstation/practice$ mv test_copy.txt test_rename.txt
```

### 이동 / 복사 (디렉토리)

```
developer@****:/mnt/c/Users/****/dev-workstation/practice$ cd ..
developer@****:/mnt/c/Users/****/dev-workstation$ cp -r practice practice_copy
```

### 이름 변경 (폴더)

```
developer@****:/mnt/c/Users/****/dev-workstation$ mv practice_copy practice_rename
```

### 목록 확인

```
developer@****:/mnt/c/Users/****/dev-workstation$ ls -la
total 0
drwxrwxrwx 1 developer developer 4096 Nov  7 17:55 .
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov  7 17:36 README.md
drwxrwxrwx 1 developer developer 4096 Nov  7 17:47 practice
drwxrwxrwx 1 developer developer 4096 Nov  7 17:52 practice_rename
```

### 삭제 (파일 + 폴더)

```
developer@****:/mnt/c/Users/****/dev-workstation$ rm practice/test_rename.txt
developer@****:/mnt/c/Users/****/dev-workstation$ rm -r practice_rename
```

### 최종 목록 확인

```
developer@****:/mnt/c/Users/****/dev-workstation$ ls -la
total 0
drwxrwxrwx 1 developer developer 4096 Nov  7 18:11 .
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov  7 17:36 README.md
drwxrwxrwx 1 developer developer 4096 Nov  7 18:11 practice
```

## 권한 실습 (Permissions)

### 파일 권한 변경

- **대상:** `test_file.txt`
- **목표:** 소유자만 읽고 쓸 수 있도록 설정 (`600`)

```
# [변경 전]
$ ls -l test_file.txt
-rw-r--r-- 1 developer developer 0 Nov  7 18:45 test_file.txt

# [명령어 실행]
$ chmod 600 test_file.txt

# [변경 후]
$ ls -l test_file.txt
-rw------- 1 developer developer 0 Nov  7 18:45 test_file.txt
```

### 디렉토리 권한 변경

- **대상:** `test_folder`
- **목표:** 모든 사용자가 읽고, 쓰고, 이동할 수 있도록 설정 (`777`)

```
# [변경 전]
$ ls -ld test_folder
drwxr-xr-x 2 developer developer 4096 Nov  7 18:44 test_folder

# [명령어 실행]
$ chmod 777 test_folder

# [변경 후]
$ ls -ld test_folder
drwxrwxrwx 2 developer developer 4096 Nov  7 18:44 test_folder
```

## Docker 설치 및 기본 점검

### 버전 확인

```
developer@****:/mnt/c/Users/****$ docker --version
Docker version 29.9.2, build a82e528
```

### 데몬 동작 확인 (docker info)

```
developer@****:/mnt/c/Users/****$ docker info
Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 29.9.2
 Storage Driver: overlayfs
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 24
 Total Memory: 15.25GiB
 Name: docker-desktop
```

➡️ Containers / Images 항목이 정상 출력되어 데몬이 동작 중임을 확인

## Docker 운영/검증 로그

### 이미지 실행 (자동 pull + run)

```
developer@****:/mnt/c/Users/****$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete
d5e71e642bf5: Download complete
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.
```

### 이미지 목록 (docker images)

```
developer@****:/mnt/c/Users/****$ docker images
IMAGE                ID             DISK USAGE   CONTENT SIZE   EXTRA
hello-world:latest   c567b231f656   25.9kB       9.49kB         U (In Use)
```

### 컨테이너 목록 (docker ps -a)

```
developer@****:/mnt/c/Users/****$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                     NAMES
4401b585a9e0   hello-world   "/hello"   18 seconds ago   Exited (0) 17 seconds ago  pensive_mahavira
```

### 컨테이너 로그 (docker logs)

```
developer@****:/mnt/c/Users/****$ docker logs 4401b585a9e0
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

### 자원 사용량 (docker stats)

```
developer@****:/mnt/c/Users/****$ docker stats --no-stream
```

➡️ 실행 중인 컨테이너가 없어 출력 없음 (hello-world는 즉시 종료되는 컨테이너)
