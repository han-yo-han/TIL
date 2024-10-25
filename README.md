# TIL(Today I Learned)

## 2024-10

### 2024-10-25

- [REACT_NATIVE 기본개념 정리] (/REACT_NATIVE/basic-concepts.md)

- [MARKDOWN 기본개념 정리] (/MARKDOWN/basic-concepts.md)

- [LINUX commands 정리] (/LINUX/commands.md)

---

## 📝 TIL 작성 가이드

# [분야/대문자snakecase로/ex)REACT_NATIVE] [주제/소문자케밥케이스로/ex)basic-concepts]

## 📚 학습 목표 간략히

### 소주제1.

### 소주제2.

---

_작성일: 2024-xx-xx_

## 📝 Change Log

---

## 📝 Change Log 작성 가이드

### 기록 규칙

1. 중요 내용 변경

- 이전/이후 내용 명시
- 변경 이유 필수 작성

2. 단순 오타

- 간단히 수정 내용만 기록

3. 내용 추가/삭제

- 추가/삭제된 내용 명시

4. 구조 개선

- 개선 사항 요약
- 필요시 이전/이후 구조 비교

### 예시

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
