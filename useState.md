# useState

React 내에서 가장 많이 사용되는 Hook 중 하나로, 함수형 컴포넌트에서 상태(State)를 관리할 때 쓰인다.

## 특징

- **함수 컴포넌트에서 상태 관리**  
  클래스 컴포넌트에서만 가능했던 상태 관리를 함수 컴포넌트에서도 가능하게 해준다.

- **자동 UI 업데이트**  
  상태가 변경되면 React가 자동으로 해당 컴포넌트를 다시 렌더링하여 UI를 최신 상태로 유지해준다.

- **초기값 설정**  
  useState를 호출할 때 초기 상태 값을 설정해줘야 한다.

## 예시

버튼 클릭 시 숫자가 변경되는 간단한 코드

```jsx
import { useState } from "react";
export default function Count() {
  const [count, setCount] = useState(0);
  return (
    <>
      <div>숫자 : {count}</div>
      <div>
        <button
          onClick={() => {
            setCount(count + 1);
          }}
        >
          증가
        </button>
        <button
          onClick={() => {
            setCount(count - 1);
          }}
        >
          감소
        </button>
        <button
          onClick={() => {
            setCount(0);
          }}
        >
          리셋
        </button>
      </div>
    </>
  );
}
```
