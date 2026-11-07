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
- [ ] Docker
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

### 빈 파일 생성 (폴더 생성 + 이동)

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

### 이동 + 폴더 복사

```
developer@****:/mnt/c/Users/****/dev-workstation/practice$ cd ..
developer@****:/mnt/c/Users/****/dev-workstation$ cp -r practice practice_copy
```

### 폴더 이름 변경

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

### 파일 권한 변경 (소유자 읽기/쓰기 전용)

```
# 변경 전
developer@****:/mnt/c/Users/****/dev-workstation$ ls -l test_file.txt
-rw-r--r-- 1 developer developer 0 Nov  7 18:45 test_file.txt

# 명령어 실행
developer@****:/mnt/c/Users/****/dev-workstation$ chmod 600 test_file.txt

# 변경 후
developer@****:/mnt/c/Users/****/dev-workstation$ ls -l test_file.txt
-rw------- 1 developer developer 0 Nov  7 18:45 test_file.txt
```

### 디렉토리 권한 변경 (모든 사용자 모든 권한 허용)

```
# 변경 전
developer@****:/mnt/c/Users/****/dev-workstation$ ls -ld test_folder
drwxr-xr-x 2 developer developer 4096 Nov  7 18:44 test_folder

# 명령어 실행
developer@****:/mnt/c/Users/****/dev-workstation$ chmod 777 test_folder

# 변경 후
developer@****:/mnt/c/Users/****/dev-workstation$ ls -ld test_folder
drwxrwxrwx 2 developer developer 4096 Nov  7 18:44 test_folder
```
