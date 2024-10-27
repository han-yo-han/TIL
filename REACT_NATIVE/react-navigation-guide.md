# React Navigation 완벽 가이드

## 목차
1. [기본 개념](#기본-개념)
2. [네비게이터 종류](#네비게이터-종류)
3. [주요 기능](#주요-기능)
4. [자주 묻는 질문 (FAQ)](#자주-묻는-질문)
5. [실전 팁](#실전-팁)

## 기본 개념

### React Navigation이란?
React Native 애플리케이션에서 화면 전환과 네비게이션을 관리하는 라이브러리입니다. 네이티브 플랫폼의 네비게이션 패턴을 따르면서도 JavaScript로 구현되어 있어 유연하게 사용할 수 있습니다.

### 핵심 컴포넌트
- `NavigationContainer`: 네비게이션 상태를 관리하는 최상위 컴포넌트
- `Navigator`: 화면 전환 방식을 정의하는 컴포넌트
- `Screen`: 실제 화면을 정의하는 컴포넌트

### 기본 설정
```typescript
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';

const Stack = createStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

## 네비게이터 종류

### 1. Stack Navigator
- 화면을 카드처럼 쌓아가는 방식
- 일반적인 계층적 네비게이션에 사용
- iOS의 NavigationController와 유사

### 2. Tab Navigator
- 하단이나 상단에 탭을 표시
- 주요 섹션 간 전환에 사용
- 보통 앱의 메인 화면에서 사용

### 3. Drawer Navigator
- 측면에서 슬라이드되는 메뉴
- 추가 네비게이션 옵션을 제공할 때 사용
- 햄버거 메뉴 구현에 적합

## 주요 기능

### 1. 네비게이션 메서드
```typescript
// 기본 네비게이션
navigation.navigate('Screen');     // 화면 이동
navigation.goBack();              // 뒤로 가기

// 스택 조작
navigation.push('Screen');        // 스택에 추가
navigation.pop();                 // 스택에서 제거
navigation.popToTop();           // 처음으로 이동

// 화면 교체
navigation.replace('Screen');     // 현재 화면 교체
```

### 2. 파라미터 전달
```typescript
// 파라미터 전달
navigation.navigate('Screen', { id: 123 });

// 파라미터 받기
const { id } = route.params;
```

### 3. 생명주기 이벤트
```typescript
useEffect(() => {
  const unsubscribe = navigation.addListener('focus', () => {
    // 화면이 포커스를 받았을 때
  });
  return unsubscribe;
}, [navigation]);
```

## 자주 묻는 질문

### Q1: 스택은 누가 관리하나요?
A: React Navigation이 내부적으로 관리합니다. 개발자는 `navigation` 객체를 통해 간접적으로 스택을 조작합니다. 실제 스택의 상태를 직접 수정할 필요는 없습니다.

### Q2: 네비게이션 생명주기가 왜 필요한가요?
A: 다음과 같은 상황에서 필요합니다:
- 화면 진입 시 데이터 새로고침
- 화면 이탈 시 리소스 정리
- 저장되지 않은 변경사항 처리
- 실시간 연결 관리
- 분석 데이터 수집

### Q3: 헤더/네비게이션 바/탭바의 차이점은 무엇인가요?
A: 
- 헤더(네비게이션 바): 화면 상단의 타이틀과 버튼을 포함하는 영역
- 탭바: 화면 하단의 주요 섹션 전환을 위한 탭들
- 둘 다 `options` prop을 통해 커스터마이징 가능

### Q4: 뒤로가기 동작을 어떻게 제어하나요?
```typescript
// 헤더의 뒤로가기 버튼 제거
options={{ headerLeft: () => null }}

// 안드로이드 하드웨어 뒤로가기 제어
useEffect(() => {
  const backHandler = BackHandler.addEventListener(
    'hardwareBackPress',
    () => {
      // 처리 로직
      return true; // 기본 동작 방지
    }
  );
  return () => backHandler.remove();
}, []);
```

### Q5: 네비게이션 상태를 전역 상태와 어떻게 연동하나요?
A: Redux나 Context API와 함께 사용할 수 있습니다:
```typescript
function App() {
  return (
    <Provider store={store}>
      <NavigationContainer>
        <Stack.Navigator>
          {/* 로그인 상태에 따라 다른 화면 표시 */}
          {isLoggedIn ? (
            <Stack.Screen name="Home" component={HomeScreen} />
          ) : (
            <Stack.Screen name="Login" component={LoginScreen} />
          )}
        </Stack.Navigator>
      </NavigationContainer>
    </Provider>
  );
}
```

## 실전 팁

### 1. 타입 안전성 확보
```typescript
type RootStackParamList = {
  Home: undefined;
  Profile: { userId: string };
};

type Props = NativeStackScreenProps<RootStackParamList, 'Profile'>;
```

### 2. 중첩 네비게이션
```typescript
function HomeStack() {
  return (
    <Stack.Navigator>
      <Stack.Screen name="Feed" component={Feed} />
      <Stack.Screen name="Profile" component={Profile} />
    </Stack.Navigator>
  );
}

function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator>
        <Tab.Screen name="Home" component={HomeStack} />
        <Tab.Screen name="Settings" component={Settings} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}
```

### 3. 성능 최적화
- 화면 컴포넌트를 메모이제이션
- 불필요한 리렌더링 방지
- 네비게이션 이벤트 구독 해제 관리

### 4. 디버깅 팁
```typescript
<NavigationContainer
  onStateChange={(state) => {
    console.log('New state:', state);
  }}
>
  {/* ... */}
</NavigationContainer>
```

---

이 가이드는 React Navigation의 기본부터 고급 사용법까지 다루고 있습니다. 추가 정보나 최신 업데이트는 [공식 문서](https://reactnavigation.org/)를 참고하세요.
