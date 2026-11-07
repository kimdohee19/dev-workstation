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

### 3.1 현재 위치 확인
```bash
$ pwd
/mnt/c/Users/******/dev-workstation

3.2 목록 확인(숨김 파일 포함)
$ ls -al
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov 7 17:36 README.md
