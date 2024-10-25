# Linux Commands

## 📚 기본 명령어 정리

### 파일 시스템 탐색

```bash
pwd           # 현재 작업 디렉토리 출력
ls            # 디렉토리 내용 출력
  ls -l       # 자세한 내용 출력
  ls -a       # 숨김 파일 포함 출력
  ls -la      # 숨김 파일 포함 자세히 출력
cd            # 디렉토리 이동
  cd ..       # 상위 디렉토리로 이동
  cd ~        # 홈 디렉토리로 이동
  cd -        # 이전 디렉토리로 이동
```

### 파일 및 디렉토리 조작

```bash
mkdir dir1          # 디렉토리 생성
rm file1           # 파일 삭제
  rm -r dir1       # 디렉토리 삭제
  rm -rf dir1      # 강제 삭제 (주의!)
cp file1 file2     # 파일 복사
mv file1 file2     # 파일 이동/이름변경
touch file1        # 빈 파일 생성
```

### 파일 내용 확인

```bash
cat file           # 파일 내용 출력
less file          # 파일 내용 페이지별 확인
head file          # 파일 앞부분 출력
tail file          # 파일 뒷부분 출력
  tail -f file     # 실시간 파일 변경 확인
grep pattern file  # 파일에서 패턴 검색
```

### 시스템 정보

```bash
uname -a           # 시스템 정보 출력
df -h              # 디스크 사용량 확인
free -h            # 메모리 사용량 확인
top                # 프로세스 실시간 모니터링
ps aux             # 실행 중인 프로세스 확인
```

### 권한 관리

```bash
chmod 755 file     # 파일 권한 변경
chown user file    # 파일 소유자 변경
sudo command       # 관리자 권한으로 실행
```

### 네트워크

```bash
ping host          # 호스트 연결 테스트
wget url           # 파일 다운로드
curl url           # HTTP 요청
ssh user@host      # 원격 서버 접속
```

### 압축

```bash
tar -czf file.tar.gz dir/    # 디렉토리 압축
tar -xzf file.tar.gz         # 압축 해제
zip -r file.zip dir/         # ZIP 압축
unzip file.zip               # ZIP 압축 해제
```

### 프로세스 관리

```bash
kill pid           # 프로세스 종료
killall name       # 이름으로 프로세스 종료
jobs              # 백그라운드 작업 목록
bg                # 작업 백그라운드로 보내기
fg                # 작업 포그라운드로 가져오기
```

## 🔍 자주 사용하는 옵션

- `-r`: 재귀적 (디렉토리 포함)
- `-f`: 강제 실행
- `-h`: 사람이 읽기 쉬운 형태로 출력
- `-a`: 모든 파일 (숨김 파일 포함)
- `-l`: 자세한 정보 출력

## ⚡ 유용한 단축키

- `Ctrl + C`: 현재 실행 중인 프로세스 중단
- `Ctrl + Z`: 현재 프로세스 일시 중지
- `Ctrl + D`: EOF (End of File) 전송
- `Ctrl + L`: 화면 지우기 (clear)
- `Ctrl + R`: 명령어 히스토리 검색
- `Ctrl + A`: 줄의 맨 앞으로 이동
- `Ctrl + E`: 줄의 맨 뒤로 이동

## 📚 파일 권한 이해하기

```bash
권한 표기: rwxrwxrwx
- r: 읽기 (4)
- w: 쓰기 (2)
- x: 실행 (1)

예시:
- 755: rwxr-xr-x (소유자:rwx, 그룹:r-x, 기타:r-x)
- 644: rw-r--r-- (소유자:rw-, 그룹:r--, 기타:r--)
```

## 🌟 추가 학습 필요

- [ ] 파이프와 리다이렉션
- [ ] 셸 스크립팅 기초
- [ ] 환경변수 설정
- [ ] cron 작업 스케줄링

---

_작성일: 2024-10-25_---

## 📝 Change Log

### 2024-10-25

- ✨ 최초 작성
- 📝 기본 리눅스 명령어 정리
- 📚 파일 시스템 탐색 명령어 추가

### 2024-10-26

- 🔍 단순 오타 수정
- remov → remove
- usr → user

- 🔄 rm 명령어 설명 개선 [중요 변경]
- Before: rm -rf dir/ # 디렉토리 강제 삭제
- After: rm -rf dir/ # 강제 삭제 (주의! 복구 불가능)
- Reason: 명령어의 위험성을 명확히 전달하기 위해 설명 보완

- ➕ 새로운 내용 추가

* 명령어 옵션 순서 섹션 추가
* 옵션 결합 규칙 설명 추가

### 2024-10-27

- ♻️ 파일 시스템 탐색 섹션 구조 개선 [구조 변경]
- Before: 모든 명령어가 한 섹션에 나열
- After: 하위 섹션으로 구분 (디렉토리 이동, 경로 이동 방식)
- Reason: 내용을 주제별로 구분하여 가독성 향상

- 🗑️ 불필요한 내용 삭제
- DOS 명령어 비교 섹션 삭제 (리눅스 중심으로 문서 개선)

- 🔄 cd 명령어 설명 개선 [중요 변경]
- Before: cd /home/user # 홈 디렉토리로 이동
- After: cd ~ # 홈 디렉토리로 이동 (단축키)
- Reason: 더 효율적인 단축키 사용법 안내

### 2024-10-28

- 📚 권한 설명 보완 [중요 변경]
- Before: chmod 755 file # 권한 변경
- After: chmod 755 file # 읽기(r), 쓰기(w), 실행(x) 권한 변경
- Reason: 권한 구성 요소를 구체적으로 설명하여 이해도 향상
