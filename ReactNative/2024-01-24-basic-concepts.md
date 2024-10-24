# 2024-10-24 학습내용

## 📚 학습 주제

React Native 기초

### 🔥 주요 내용

1. **리액트 네이티브 작동 원리**

- JavaScript 코드가 별도의 JS 스레드에서 실행됨
- Native Bridge를 통해 네이티브 플랫폼과 통신
- Virtual Dom을 네이티브 뷰로 변환 //virtual dom의 개념적 의미 부족, 네이티브 뷰라는것의 의미 부족.
  [JavaScript 코드] <-> [Bridge] <-> [Native Components] ?? 브릿지가 뭐지? 중간다리역할한다는건알겠어 Native Components라는게 뭐지? 안드로이드의 경우 java, ios의 경우 swift로 만들어진 요소들을 말하는건가?

2. **기본 컴포넌트**

- View: div와 유사, 기본 컨테이너
- Text: 텍스트로 표시
- Image: 이미지 표시
- ScrollView: 스크롤 가능한 컨테이너
- FlatList: 최적화된 리스트뷰
- TextInput: 텍스트 입력

3. **주요 API**

- platform: OS구분
- Dimensions: 화면 크기
- AsyncStorage: 로컬 저장소
- Animated: 애니메이션

4. **스타일링 특징**

- flexbox 기반 레이아웃

5. **최적화 고려사항**

   - **JS 스레드와 메인 스레드 분리**

     - Js스레드: JS 코드 실행 담당, 데이터 처리, 계산, API 호출 등의 로직 담당
       - 일반 함수 및 로직 실행 담당
     - 메인스레드: 실제로 화면에 그림 그리는 담당, 버튼 텍스트, 이미지 등을 보여줌
       - UI 관련 코드, return 이후 jsx 실행 담당
     - _requestAnimationFrame_ : js스레드와 메인 스레드 간의 동기화 도구, js 로직이 무거울 경우 적절히 쪼개서 UI작업으로 이어질 수 있도록 도와줌.

   - **불필요한 리렌더링 방지**

     - 리렌더링이 발생하는 경우
       - props 변경
       - state 변경 :
       - 부모 컴포넌트 리렌더링링
     - 최적화방법: _메모이제이션_ : 이전에 계산한 값을 저장해두고, 동일한 입력이 들어오면 다시 계산하지 않고 재사용함. 김대원의 reuse, computation
       - *React.memo*를 사용한 컴포넌트 메모이제이션: props 같은 자식 컴포넌트는 리렌더링하지 x
       - *useMemo*를 사용한 계산값 메모이제이션: 리렌더링시 계산할지안할지를 _의존성 배열_ 보고 결정 -_의존성배열_: []:컴포넌트 마운트시 1번 계산, [data]:data가 변경될때만 재계산, 배열없음:매렌더링마다 재계산
       - *useCallback*을 사용한 함수 메모이제이션

   - **이미지 최적화**
     - 크기 지정
     - _resizeMode_ 사용하기: 지정된 크기 안에서 어떻게 배치할 지 결정
       - cover: 영역 맞게 조정
       - contain: 이미지 전체 보이게
       - stretch: 늘려서 채움
       - center: 중앙정렬
     - 네트워크 이미지 사용하기: url로 불러오기
     - 로딩 상태 처리하기: alt 대신 로딩 인디케이터 사용
     - 여러 이미지를 목록으로 표시할 때: FlatList 사용 권장.

6. **Hooks**
   - useState: 상태관리
   - useEffect: 생명주기관리 //컴포넌트 마운트시에만 실행(mount) //특정 값이 변경될 때마다 실행(update) 데이터 페칭: 서버에서 데이터를 가져오는 작업. 이런 작업은 처음 마운트될 때만 실행.
   - useRef: 값 참조
   - useMemo, useCallback: 성능 최적화
     - useMemo: 복잡한 계산 값 메모이제이션
     - useCallback: 함수 메모이제이션
   - useContext: 컨텍스트 사용 ContextAPI: React의 전역 상태 관리 시스템
     - props drilling: props가 여러 층의 컴포넌트를 거쳐 전달하는 현상.
   - useReducer: 복잡한 상태 로직 관리
   - 커스텀 훅: 폼 입력 관리를 위해 필요
   - _주의사항_
     - 반드시 컴포넌트 최상위에서만 호출
     - 조건문이나 반복문 안에서 사용 금지
     - 일반 함수가 아닌 리액트 함수 컴포넌트 안에서만 사용

### 📝 메모

- 키워드1
- 키워드2

### 📌 참고자료

```

```
