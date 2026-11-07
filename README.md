# 개발 워크스테이션 구성 및 리눅스 실습

## 1. 프로젝트 개요
터미널, Docker, Git, GitHub를 직접 활용해 개발 워크스테이션을 구성하고, 누구나 비슷한 환경을 다시 만들 수 있도록 재현 가능한 개발 환경을 익히는 것이 목적입니다.

## 2. 실행 환경
- **OS**: Windows 11
- **Shell**: bash
- **Terminal**: WSL Ubuntu, VS Code 통합 터미널
- **Docker**: 29.9.2
- **Git**: 2.53.0

---

## 3. 터미널 조작 로그 기록
> 📌 각 항목은 미션 요구사항에 맞춰 실제 수행한 명령어를 정리한 결과입니다.

### 3.1 현재 위치 확인
$ pwd
/mnt/c/Users/******/dev-workstation

### 3.2 목록 확인(숨김 파일 포함)
$ ls -al
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov 7 17:36 README.md

### 3.3 이동, 생성, 복사, 파일 내용 확인, 빈 파일 생성
# 디렉토리 생성(mkdir), 이동(cd), 빈 파일 생성(touch), 내용 확인(cat)
$ mkdir practice
$ cd practice
$ touch test.txt
$ cat test.txt

# 파일 복사(cp) 및 이름 변경(mv)
$ cp test.txt test_copy.txt
$ mv test_copy.txt test_rename.txt
$ cd ..

### 3.4 디렉토리 복사 및 이동/이름변경
# 폴더 전체 복사(cp -r) 및 이름 변경(mv)
$ cp -r practice pratice_copy
$ mv pratice_copy practice_rename
mv: cannot stat 'practice_copy': No such file or directory
$ mv pratice_copy practice_rename

### 3.5 목록 확인 (폴더 복사/이름 변경 후 상태)
$ ls -la
drwxrwxrwx 1 developer developer 4096 Nov 7 17:55 .
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov 7 17:36 README.md
drwxrwxrwx 1 developer developer 4096 Nov 7 17:47 practice
drwxrwxrwx 1 developer developer 4096 Nov 7 17:52 practice_rename

$ ls practice_rename
test.txt  test_rename.txt

### 3.6 삭제
# 파일 및 디렉토리 삭제(rm, rm -r)
$ rm practice/test_rename.txt
$ rm -r practice_rename

# 최종 목록 확인
$ ls -la
drwxrwxrwx 1 developer developer 4096 Nov 7 18:11 .
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov 7 17:36 README.md
drwxrwxrwx 1 developer developer 4096 Nov 7 18:11 practice

---

## 4. 권한 실습 (Permissions)

### 4.1 파일 권한 변경
* **대상**: test_file.txt (소유자 읽기/쓰기 전용 설정)

# [변경 전]
$ ls -l test_file.txt
-rw-r--r-- 1 developer developer 0 Nov  7 18:45 test_file.txt

# [명령어 실행]
$ chmod 600 test_file.txt

# [변경 후]
$ ls -l test_file.txt
-rw------- 1 developer developer 0 Nov  7 18:45 test_file.txt

### 4.2 디렉토리 권한 변경
* **대상**: test_folder (모든 사용자 모든 권한 허용)

# [변경 전]
$ ls -ld test_folder
drwxr-xr-x 2 developer developer 4096 Nov  7 18:44 test_folder

# [명령어 실행]
$ chmod 777 test_folder

# [변경 후]
$ ls -ld test_folder
drwxrwxrwx 2 developer developer 4096 Nov  7 18:44 test_folder

### 4.3 권한 변경 요약표

| 대상 | 변경 전 | 실행 명령어 | 변경 후 | 결과 요약 |
| :--- | :--- | :--- | :--- | :--- |
| 파일 (test_file.txt) | -rw-r--r-- | chmod 600 | -rw------- | 소유자 외 접근 차단 |
| 디렉토리 (test_folder) | drwxr-xr-x | chmod 777 | drwxrwxrwx | 모든 사용자 권한 허용 |
