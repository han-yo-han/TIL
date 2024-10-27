# React & TypeScript 기초 개념 정리

## 1. Props 이해하기

### 1.1. Props란?
- 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하는 방법
- 컴포넌트의 매개변수라고 생각하면 됨

### 1.2. Props 사용 예시
```typescript
// 부모 컴포넌트에서 props 전달
<Card title="제목" color="blue">
  <Text>안녕하세요!</Text>
</Card>

// 자식 컴포넌트에서 props 받기
const Card = ({ title, color, children }) => {
  return (
    <View style={{ backgroundColor: color }}>
      <Text>{title}</Text>
      {children}
    </View>
  );
};
```

### 1.3. children props
- 컴포넌트 태그 사이에 들어가는 모든 요소
- React.ReactNode 타입으로 정의됨
```typescript
<Card>
  {/* 여기 들어가는 모든 것이 children */}
  <Text>제목</Text>
  <Button>클릭</Button>
</Card>
```

## 2. Interface 이해하기

### 2.1. Interface vs 일반 변수/객체
```typescript
// 방법 1: 일반 변수로 타입 정의 (비권장)
const cardProps = {
  title: String,
  color: String
}

// 방법 2: Interface로 타입 정의 (권장)
interface CardProps {
  title: string;
  color: string;
}
```

### 2.2. Interface를 사용하는 이유
1. **확장성 (extends)**
```typescript
interface BaseProps {
  title: string;
}

interface CardProps extends BaseProps {
  color: string;  // BaseProps의 속성 + 추가 속성
}
```

2. **재사용성**
```typescript
// 여러 컴포넌트에서 같은 인터페이스 사용 가능
const Card = ({ title, color }: CardProps) => {...}
const AnotherCard = ({ title, color }: CardProps) => {...}
```

3. **타입 안정성**
- 컴파일 시점에서 타입 체크
- IDE 자동완성 지원

## 3. TypeScript 타입 시스템

### 3.1. 기본 타입 설정
```typescript
// 변수의 타입 설정
const name: string = "John";
const age: number = 25;
const isActive: boolean = true;

// 배열 타입 설정
const names: string[] = ["John", "Jane"];
const numbers: Array<number> = [1, 2, 3];

// 함수 타입 설정
function add(x: number, y: number): number {
  return x + y;
}
```

### 3.2. 객체 타입
```typescript
// 객체 타입 정의 방법
type Person = {
  name: string;
  age: number;
}

interface Person {
  name: string;
  age: number;
}

// 선택적 속성 (Optional Properties)
interface CardProps {
  title?: string;  // ? 는 선택적이라는 의미
  color: string;   // 필수 속성
}
```

### 3.3. 타입 설정이 필요한 이유
1. **버그 예방**
   - 컴파일 시점에서 타입 관련 오류 발견
   - 런타임 에러 감소

2. **코드 품질 향상**
   - 명확한 타입 정의로 코드 이해도 증가
   - 리팩토링 시 안정성 확보

3. **개발 생산성**
   - IDE 자동완성 지원
   - 타입 관련 문서화 효과

## 4. 추가 개념

### 4.1. 객체 구조 분해 할당
```typescript
// 기본 형태
const { title, color } = props;

// 타입과 함께 사용
const Card = ({ title, color }: CardProps) => {...}
```

### 4.2. Style 처리
```typescript
// StyleSheet.create 사용 (권장)
const styles = StyleSheet.create({
  container: {
    padding: 16,
    backgroundColor: 'white'
  }
});

// 일반 객체로 스타일 정의 (비권장)
const styles = {
  container: {
    padding: 16,
    backgroundColor: 'white'
  }
};
```

### 4.3. 타입 표기법 이해
- `:` 콜론의 두 가지 용도:
  1. 객체의 키-값 쌍 구분
  ```typescript
  const person = {
    name: "John",    // 키-값 구분
    age: 25
  }
  ```
  
  2. 타입 지정
  ```typescript
  const name: string = "John"    // 타입 지정
  const Card = (props: CardProps) => {...}  // 타입 지정
  ```
