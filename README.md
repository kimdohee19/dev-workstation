# 개발 워크스테이션 구성 및 리눅스 실습

## 1. 프로젝트 개요
터미널, Docker, Git, GitHub를 직접 활용해 개발 워크스테이션을 구성하고, 리눅스 환경에서의 기본 조작법과 권한 관리를 익히는 실습 기록입니다.

## 2. 실행 환경
- **OS**: Windows 11
- **Shell**: bash
- **Terminal**: WSL Ubuntu, VS Code 통합 터미널
- **Docker**: 29.9.2
- **Git**: 2.53.0

---

## 3. 터미널 조작 로그 기록

### 1. 현재 위치 확인
developer@****:~/dev-workstation$ pwd
/mnt/c/Users/****/dev-workstation

### 2. 목록 확인 (숨김 파일 포함)
developer@****:~/dev-workstation$ ls -al
total 0
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 .
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov  7 17:36 README.md

### 3. 빈 파일 생성 (폴더 생성 + 이동)
developer@****:~/dev-workstation$ mkdir practice
developer@****:~/dev-workstation$ cd practice
developer@****:~/dev-workstation/practice$ touch test.txt

### 4. 파일 내용 확인
developer@****:~/dev-workstation/practice$ cat test.txt

### 5. 복사
developer@****:~/dev-workstation/practice$ cp test.txt test_copy.txt

### 6. 이동/이름 변경
developer@****:~/dev-workstation/practice$ mv test_copy.txt test_rename.txt

### 7. 상위 폴더 이동 + 폴더 복사
developer@****:~/dev-workstation/practice$ cd ..
developer@****:~/dev-workstation$ cp -r practice practice_copy

### 8. 폴더 이름 변경
developer@****:~/dev-workstation$ mv practice_copy practice_rename

### 9. 목록 확인
developer@****:~/dev-workstation$ ls -la
total 0
drwxrwxrwx 1 developer developer 4096 Nov  7 17:55 .
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov  7 17:36 README.md
drwxrwxrwx 1 developer developer 4096 Nov  7 17:47 practice
drwxrwxrwx 1 developer developer 4096 Nov  7 17:52 practice_rename

### 10. 복사된 폴더 내용 확인
developer@****:~/dev-workstation$ ls practice_rename
test.txt  test_rename.txt

### 11. 삭제 (파일)
developer@****:~/dev-workstation$ rm practice/test_rename.txt

### 12. 삭제 (폴더)
developer@****:~/dev-workstation$ rm -r practice_rename

### 13. 최종 목록 확인
developer@****:~/dev-workstation$ ls -la
total 0
drwxrwxrwx 1 developer developer 4096 Nov  7 18:11 .
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov  7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov  7 17:36 README.md
drwxrwxrwx 1 developer developer 4096 Nov  7 18:11 practice


## 4. 권한 실습 (Permissions)

### 1. 파일 권한 변경 (소유자 읽기/쓰기 전용)
# [변경 전]
developer@****:~/dev-workstation$ ls -l test_file.txt
-rw-r--r-- 1 developer developer 0 Nov  7 18:45 test_file.txt

# [명령어 실행]
developer@****:~/dev-workstation$ chmod 600 test_file.txt

# [변경 후]
developer@****:~/dev-workstation$ ls -l test_file.txt
-rw------- 1 developer developer 0 Nov  7 18:45 test_file.txt

### 2. 디렉토리 권한 변경 (모든 사용자 모든 권한 허용)
# [변경 전]
developer@****:~/dev-workstation$ ls -ld test_folder
drwxr-xr-x 2 developer developer 4096 Nov  7 18:44 test_folder

# [명령어 실행]
developer@****:~/dev-workstation$ chmod 777 test_folder

# [변경 후]
developer@****:~/dev-workstation$ ls -ld test_folder
drwxrwxrwx 2 developer developer 4096 Nov  7 18:44 test_folder
