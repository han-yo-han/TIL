src/
├── assets/ # 정적 리소스
│ ├── images/ # 이미지 파일들
│ ├── fonts/ # 폰트 파일들
│ └── icons/ # 아이콘 파일들
│
├── components/ # 재사용 가능한 컴포넌트
│ ├── common/ # 공통 컴포넌트
│ │ ├── Button.tsx
│ │ ├── Input.tsx
│ │ └── Header.tsx
│ └── auth/ # 인증 관련 컴포넌트
│ ├── LoginForm.tsx
│ └── SocialLogin.tsx
│
├── screens/ # 화면 컴포넌트
│ ├── auth/ # 인증 관련 화면
│ │ ├── LoginScreen.tsx
│ │ └── SignupScreen.tsx
│ └── main/ # 메인 화면들
│ ├── HomeScreen.tsx
│ └── ProfileScreen.tsx
│
├── navigation/ # 네비게이션 설정
│ ├── AppNavigator.tsx
│ └── AuthNavigator.tsx
│
├── services/ # API 호출, 외부 서비스
│ ├── api.ts # API 클라이언트
│ └── auth.ts # 인증 관련 API
│
├── store/ # 상태 관리 (Redux/Context)
│ ├── auth/
│ │ ├── actions.ts
│ │ └── reducer.ts
│ └── index.ts
│
├── utils/ # 유틸리티 함수들
│ ├── constants.ts
│ ├── helpers.ts
│ └── validation.ts
│
├── hooks/ # 커스텀 훅
│ ├── useAuth.ts
│ └── useForm.ts
│
└── App.tsx # 앱의 진입점
