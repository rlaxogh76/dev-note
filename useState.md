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

## 주의점

앞으로 많이 만나게 될 useState는 만나는 만큼 사용 빈도도 높아져 한 코드에 다양한 종류의 useState가 들어가게 될 수 밖에 없다.

```jsx
function UserCard() {
  const [name, setName] = useState("");
  const [age, setAge] = useState(20);
  const [school, setSchool] = useState("");

  return (
    <div>
      <h1>이름: {name}</h1>
      <h2>나이: {age}</h2>
      <h3>학교: {school}</h3>
      <button
        onClick={() => {
          setName("rlaxogh76");
          setAge("20");
          setSchool("GBSW");
        }}
      >
        정보 변경
      </button>
    </div>
  );
}
```

위 코드처럼 유저에 대한 정보를 다루는 useState 같은 경우 setName 등을 통해 계속 바꿔줘야 한다. 나쁜 방식은 아니지만 그렇다고 추천하는 방식도 아니다. <br>
이 코드를 아래와 같이 좀 더 깔끔하게 수정할 수 있다.

```jsx
function UserCardSquashed() {
  const [user, setUser] = useState({
    name: "",
    age: 20,
    school: "",
  });

  return (
    <div>
      <h1>이름: {user.name}</h1>
      <h2>나이: {user.age}</h2>
      <h3>학교: {user.school}</h3>
      <button
        onClick={() => {
          setUser({
            name: "rlaxogh76",
            age: 20,
            school: "GBSW",
          });
        }}
      >
        정보 변경
      </button>
    </div>
  );
}
```

useState 내에서 name, age, school를 다루면 한 번만 상태를 변경할 수 있다는 장점이 있다.
