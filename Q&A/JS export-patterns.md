# JavaScript/TypeScript Export Patterns Guide

## Default Export

Default export는 파일당 **하나의** 기본 내보내기를 허용합니다.

### 기본 문법

```javascript
// 1. 선언 후 export
const Card = () => {
  return <div>Card Component</div>;
}
export default Card;

// 2. 인라인 export
export default function Card() {
  return <div>Card Component</div>;
}

// 3. 익명 함수로 export
export default () => {
  return <div>Card Component</div>;
}
```

### Import 방법

```javascript
// 어떤 이름으로든 import 가능
import Card from './Card';
import MyCard from './Card';
import Whatever from './Card';     // 작동하지만 권장하지 않음
```

### 주의사항
- 파일당 하나만 가능
- 이름을 자유롭게 바꿀 수 있어서 일관성이 깨질 수 있음
- Tree-shaking이 덜 효율적일 수 있음

## Named Export

Named export는 파일에서 **여러 개**의 값을 내보낼 수 있습니다.

### 기본 문법

```javascript
// 1. 선언과 동시에 export
export const Button = () => {
  return <button>Click Me</button>;
}

// 2. 선언 후 export
const Input = () => {
  return <input type="text" />;
}
const Label = () => {
  return <label>Label</label>;
}

export { Input, Label };

// 3. 상수나 유틸리티 함수도 export 가능
export const Colors = {
  primary: '#007AFF',
  secondary: '#5856D6'
};
```

### Import 방법

```javascript
// 1. 개별 import
import { Button } from './Components';

// 2. 여러 개 동시 import
import { Button, Input, Label } from './Components';

// 3. 이름 바꾸기 (as 사용)
import { Button as CustomButton } from './Components';

// 4. 전체 import
import * as Components from './Components';
// 사용: Components.Button, Components.Input
```

## 혼합 사용

한 파일에서 default export와 named export를 함께 사용할 수 있습니다.

```javascript
// Card.js
export default function Card() {
  return <div>Card</div>;
}

export const SmallCard = () => {
  return <div>Small Card</div>;
}

export const CardTypes = {
  BASIC: 'basic',
  PREMIUM: 'premium'
};
```

```javascript
// 혼합 import
import Card, { SmallCard, CardTypes } from './Card';
```

## 권장 사례

### Default Export 사용하기 좋은 경우
- 파일당 하나의 주요 컴포넌트만 있을 때
- React 컴포넌트 파일 하나가 하나의 주요 컴포넌트만 담당할 때
- 클래스 기반 컴포넌트

### Named Export 사용하기 좋은 경우
- 유틸리티 함수들
- 상수나 타입 정의
- 관련된 여러 컴포넌트들
- Hook들
- 설정 객체들

## 모듈 인덱스 패턴

여러 컴포넌트를 한 번에 export/import 하기 위한 패턴입니다.

```javascript
// /components/index.js
export { default as Card } from './Card';
export { default as Button } from './Button';
export { default as Input } from './Input';
export { Colors } from './constants';

// 사용할 때
import { Card, Button, Input, Colors } from '@components';
```

## 현대적인 추세

최근의 React 개발에서는 다음과 같은 이유로 Named Export를 선호하는 경향이 있습니다:

1. 더 나은 IDE 지원
   - 자동 완성이 더 정확함
   - 리팩토링 도구가 더 잘 작동

2. 더 명확한 의도 전달
   - 컴포넌트 이름이 고정되어 일관성 유지
   - 코드 리뷰가 더 쉬워짐

3. 더 좋은 트리 쉐이킹
   - 번들러가 사용하지 않는 코드를 더 잘 제거할 수 있음

4. 모듈 묶음 관리가 쉬움
   - 관련된 컴포넌트들을 하나의 파일에서 관리 가능
