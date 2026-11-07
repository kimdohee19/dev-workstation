## 프로젝트 개요
터미널, Docker, Git, GitHub를 직접 활용해 개발 워크스테이션을 구성하고, 누구나 비슷한 환경을 다시 만들 수 있도록 재현 가능한 개발 환경을 익히는 것이 목적입니다.

## 실행 환경
- OS: Windows 11
- Shell: bash
- Terminal: WSL Ubuntu, VS Code 통합 터미널
- Docker: 29.9.2
- Git: 2.53.0

## 🖥️ 터미널 조작 로그

> 📌 각 항목은 명령어 입력과 출력 결과를 함께 포함합니다.

---

### 1. pwd
```bash
$ pwd
/mnt/c/Users/******/dev-workstation
```

---

### 2. ls -al
```bash
$ ls -al
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov 7 17:36 README.md
```

---

### 3. mkdir / cd / touch / cat / cp / mv
```bash
$ mkdir practice
$ cd practice
$ touch test.txt
$ cat test.txt
$ cp test.txt test_copy.txt
$ mv test_copy.txt test_rename.txt
$ cd ..
```

---

### 4. cp -r (폴더 복사) / mv (이름 변경)
```bash
$ cp -r practice pratice_copy
$ mv pratice_copy practice_rename
mv: cannot stat 'practice_copy': No such file or directory
$ mv pratice_copy practice_rename
```

---

### 5. ls -la (폴더 복사/이름 변경 후 확인)
```bash
$ ls -la
drwxrwxrwx 1 developer developer 4096 Nov 7 17:55 .
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov 7 17:36 README.md
drwxrwxrwx 1 developer developer 4096 Nov 7 17:47 practice
drwxrwxrwx 1 developer developer 4096 Nov 7 17:52 practice_rename

$ ls practice_rename
test.txt  test_rename.txt
```

---

### 6. rm (파일/폴더 삭제)
```bash
$ rm practice/test_rename.txt
$ rm -r practice_rename
$ ls -la
drwxrwxrwx 1 developer developer 4096 Nov 7 18:11 .
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 ..
drwxrwxrwx 1 developer developer 4096 Nov 7 17:36 .git
-rwxrwxrwx 1 developer developer  372 Nov 7 17:36 README.md
drwxrwxrwx 1 developer developer 4096 Nov 7 18:11 practice
```
