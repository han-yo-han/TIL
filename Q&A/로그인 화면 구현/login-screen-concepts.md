# 로그인 화면 UI 구성요소 개념 정리

## 1. 기본 레이아웃 요소
- **View**: 레이아웃의 기본 컨테이너 (div와 유사)
- **SafeAreaView**: iOS의 노치나 상태바를 고려한 안전영역 설정
- **KeyboardAvoidingView**: 키보드가 UI를 가리지 않도록 조정

## 2. 입력 폼 요소
- **TextInput**: 텍스트 입력 필드 (아이디, 비밀번호 입력용)
  - secureTextEntry: 비밀번호 입력시 문자 숨김 처리
  - placeholder: 입력 전 안내 텍스트
  - autoCapitalize: 자동 대문자 설정
  - autoCorrect: 자동 수정 기능

## 3. 상호작용 요소
- **TouchableOpacity**: 터치 피드백이 있는 버튼 (로그인 버튼)
- **Pressable**: 더 세밀한 터치 상태 제어가 가능한 버튼 (신형)
- **Button**: 기본 버튼 컴포넌트 (플랫폼별 기본 스타일)
- **Text**: 텍스트 표시 (링크, 라벨 등)

## 4. 체크박스 구현 방법
- **Checkbox 컴포넌트** (서드파티 라이브러리 필요)
  - @react-native-community/checkbox
  - expo-checkbox
- **커스텀 체크박스**: TouchableOpacity + 이미지/아이콘

## 5. 이미지 요소
- **Image**: 로고, 아이콘 표시
  - source: 이미지 소스 지정
  - resizeMode: 이미지 맞춤 방식
    - contain: 비율 유지, 컨테이너 내 전체 표시
    - cover: 비율 유지, 컨테이너 가득 채움
    - center: 중앙 정렬

## 6. 스타일링 주요 개념
- **StyleSheet.create()**: 스타일 객체 생성
- **Flexbox**: 레이아웃 배치
  - flexDirection: 요소 배치 방향
  - justifyContent: 주축 정렬
  - alignItems: 교차축 정렬
- **Shadow Properties**: 그림자 효과
  - iOS: shadowColor, shadowOffset, shadowOpacity, shadowRadius
  - Android: elevation

## 7. 폼 상태 관리
- **useState**: 입력값, 체크박스 상태 관리
- **useForm**: 폼 데이터 통합 관리 (선택적)
- **Validation**: 입력값 검증
  - 이메일 형식
  - 비밀번호 규칙
  - 빈 값 체크

## 8. 네비게이션 관련
- **Stack Navigation**: 화면 전환
  - navigate(): 다른 화면으로 이동
  - goBack(): 이전 화면으로 돌아가기
- **Linking**: 외부 앱 연동 (SNS 로그인)

## 주요 구현 포인트
1. 키보드 처리
2. 에러 메시지 표시
3. 로딩 상태 표시
4. 자동 로그인 처리
5. SNS 로그인 연동
