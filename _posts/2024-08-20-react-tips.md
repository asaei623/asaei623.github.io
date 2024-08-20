---
title: "알아두면 유용한 '리액트' 개념과 성능 최적화 팁"
excerpt: "리액트 개념, 리액트 훅, 데이터 전달 방법"

categories:
    - 아티클 정리
tags: # 포스트 태그
    - [algorithm, python, BFS]

permalink: /categories/article/2024-08-20-react-tips/

toc: true
toc_sticky: true

date: 2024-08-20
last_modified_at: 2024-08-20
---

출처 : [알아두면 유용한 ‘리액트’ 개념과 성능 최적화 팁](https://yozm.wishket.com/magazine/detail/2688/)

<br/>

## 📄 서론

`리액트`는

-   컴포넌트 기반 아키텍처
-   가상 DOM

등의 개념을 도입한 **자바스크립트 라이브러리**이다.

리액트 활용을 위한 **리액트 컴포넌트, 훅, 개발자 도구 및 성능 최적화 팁**에 대해 살펴본다.

<br/>

## 📄 리액트 기본 개념

### 1) 컴포넌트 기반 아키텍처

웹 애플리케이션의 복잡한 UI를 **재사용 가능한 단위로 분할**하는 방식이다.

특정 기능이나 UI의 한 부분을 담당하는 `컴포넌트`는

-   상태
-   속성

을 가지며 각각 독립적으로 작동한다.

`컴포넌트`의 **장점**으로는

-   개발자가 관심사를 분리하여 개발에 집중할 수 있다.
-   UI를 계층적으로 구조화한다.
    -   → 코드 가독성이 높아진다.
    -   → 유지보수가 용이해진다.

가 있다.

컴포넌트 기반 아키텍처를 설계할 때는 `단일 책임 원칙` 을 지키는 것이 좋다.

`단일 책임 원칙` 은

-   구성 요소 간의 의존성을 최소화한다.
-   각 컴포넌트는 한 가지 책임만 진다.
-   즉 각 컴포넌트의 복잡도는 낮추고, 재사용성을 높여야 한다.

는 것을 의미한다.

또한, 다른 개발자가 `컴포넌트` 를 이해하기 쉽게, **속성**과 **반환값** 작성 방식을 일관되게 유지해야 한다.

<br/>

### 2) JSX 문법

`JSX(JavaScript XML)` 이란

-   자바스크립트를 확장한 문법
-   HTML과 유사한 형태
-   컴포넌트 렌더링 로직과 마크업을 _한 곳에서_ 관리할 수 있다.
    -   → 즉 컴포넌트의 동작과 구조를 한 번에 관리할 수 있다.

이며, 리액트에서 사용된다.

주요 규칙으로 다음의 것들이 있다.

1. 속성명은 카멜 케이스를 사용

    ```jsx
    <div className="signup" />
    ```

2. 자바스크립트 표현식은 중괄호 사용

    ```jsx
    {
        /* name 속성 값이 아래의 {name}에 매칭된다. */
    }
    <div>Welcome, {name};</div>;
    ```

3. 인라인 스타일은 `style={{}}` 사용

    ```jsx
    <div style={{ backgroundColor: "red" }} />
    ```

4. 주석은 `{/*  */}` 사용

<br/>

### 3) 가상 DOM(Virtual DOM)

`가상 DOM()` 이란 실제 DOM을 *추상화한 DOM*을 말한다.

리액트에서는

-   컴포넌트가 **처음 렌더** 될 때 **가상 DOM 트리를 생성**한다.
-   **상태, 속성**이 변경될 때 비교(Diffing)과 조정(Reconciliation)을 통해 ***변경된 부분*만 실제 DOM에 반영(Patch)**한다.
    -   → **불필요한** DOM 조작이 **최소화**된다.

<br/>

### 4) Props와 State

-   Props ⇒ 속성
-   State ⇒ 상태

Props는

-   부모 컴포넌트 → 자식 컴포넌트로 전달되는 데이터
-   읽기 전용(read-only)로 자식 컴포넌트에서 직접 수정할 수 없다.

State는

-   컴포넌트 내부에서 관리되는 상태 데이터
-   내부에서 직접 수정할 수 있다.
-   state 변경 시 자동으로 다시 렌더링(Re-rendering)된다.
-   다양한 방법으로 관리되며, `useState` 라는 **리액트 훅**을 사용하는 것이 가장 기본적이다.

<br/>

## 📄 리액트 훅(React Hooks)의 활용

### 1) 리액트 훅이란?

-   리액트 16.8 버전부터 도입됐다.
-   다양한 **리액트 기능**을 사용할 수 있게 해주는 **일종의 함수 API**이다.

장점

-   컴포넌트 로직을 **간결하게** 작성할 수 있다.
-   컴포넌트 간 상태를 공유, 불필요한 렌더링 방지 등 **성능 최적화**에 도움을 준다.

<br/>

### 2) 리액트 훅 사용 예시

1. **useState**

    - **상태를 관리**하기 위한 훅
    - `1) 상태 값` `2) 상태를 업테이트 하는 함수` 를 받는다.

    ```jsx
    const [count, setCount] = useState(0); //0은 초기 상태값
    ```

2. **useRef**

    - 컴포넌트 내에서 **특정 값을 저장**하고 **참조**할 수 있게 한다.
    - useRef는 **ref 객체**를 생성한다.
        - ref 객체는 컴포넌트 생명주기 동안 유지된다.
        - 값이 변경되도 리렌더링 되지 않는다.
        - DOM 엘리먼트에 직접 접근하거나, 이전 값을 저장해야 할 때 사용된다.
        - current 속성으로 접근할 수 있다.

    ```jsx
    import React, { useRef } from "react";

    const TextInputWithFocuseBottn = () => {
        const inputEl = useRef(null); //초기값이 null인 ref 객체 생성

        const onButtonClick = () => {
            inputEl.current.focus(); //current 속성으로 ref 객체에 접근
        };

        return (
            <>
                <input ref={inputEl} type="text" /> //ref객체를 inputEl에
                연결한다.
                <button onClick={onButtonClick}>Focus the input</button> //DOM 엘리먼트에
                직접 접근하기 위해 useRef를 사용했다.
            </>
        );
    };
    ```

3. **useEffect**

    - 컴포넌트의 **Side Effect를 처리**하기 위해 사용한다.
    - 컴포넌트 렌더링 이후 실행된다.
    - 인자로는 `1)Side Effect 함수` , `2)의존성 배열` 을 받는다.
        - `의존성 배열`에 넣은 특정 **값이 변경**될 때마다 `Side Effect 함수`를 실행한다.
        - `의존성 배열`이 **빈 배열**인 경우, 컴포넌트 **마운트 시**에만 `Side Effect 함수`를 실행한다.
        - `의존성 배열`이 **생략**된 경우, 컴포넌트 **업데이트 시**마다 실행된다.

    ```jsx
    useEffect(() => {
        console.log("You clicked Count one"); //count1 값 변경 시마다 이 부분이 실행된다.
    }, [count1]);
    ```

4. **useMemo**

    - **memoization**을 통해 **불필요한 중복 계산을 방지**한다.
    - 인자로 `1)메모제이션 할 함수` , `2)의존성 배열` 을 받는다.
        - `의존성 배열`의 값이 변경되지 않았으면, **이전에 계산된 값을 재사용**한다.
        - 계산량이 많은 함수의 반환 값을 기억하여 재사용하기 위해 사용된다.
        - `의존성 배열`이 **빈 배열**인 경우, 컴포넌트 **마운트 시에만** 함수가 실행된다.
        - `의존성 배열`이 **생략**된 경우, 컴포넌트 **업데이트 시마다** 함수가 실행된다.

    ```jsx
    const expensiveResult = useMemo(() => {
        //count 값이 변경됐을 경우만 아래 함수를 다시 실행한다.
        let result = 0;
        for (let i = 0; i < count; i++) {
            resut += i;
        }
        return resut;
    }, [count]);
    ```

5. **useReducer**

    - **상태 관리**를 위해 사용된다.
    - useState ⇒ 컴포넌트 **내**에 상태가 없데이트되는 로직이 위치한다.
    - useReducer ⇒ 컴포넌트 **밖**에 상태가 없데이트 되는 로직이 위치한다.
        - **중복**되는 상태 업데이트 로직을 컴포넌트 **외부의 한 곳에 모아 관리**할 수 있다.
        - 여러 개의 상태를 관리할 때 유용하다.
    - `reducer함수` 와 `dispatch함수` 가 필요하다.
        - `reducer함수` : state, action 객체 ⇒ 새로운 상태 반환
        - `dispatch함수` : action 객체 ⇒ reducer 함수 호출하여 인자로 넘김

    ```jsx
    import React, { useRecuder } from "react";

    const inialState = { count: 0 };

    const reducer = (state, action) => {
        switch (action.type) {
            case "increment":
                return { count: state.count + 1 };
            case "decrement":
                return { count: state.count - 1 };
            default:
                throw new Error("Unsupported action type");
        }
    };

    const Conter = () => {
        const [state, dispatch] = useRecuder(reducer, initialState); //reducer, initialState는 컴포넌트 외부에 선언되어있다.

        return (
            <div>
                <p>Count: {state.count}</p>
                {/* dispatch 함수가 액션 객체를 인자로 가져간다. 이는 reducer 함수로 넘어가서 state 상태값을 변경한다.*/}
                <button
                    onClick={() => dispatch({ type: "increment" })}
                ></button>
                <button
                    onClick={() => dispatch({ type: "decrement" })}
                ></button>
            </div>
        );
    };
    ```

<br/>

### 3) 커스텀 훅 만들기

-   개발자가 **직접 만들어 쓰는 훅**
-   **중복되는 로직**을 훅으로 처리할 수 있다.
-   **use로 시작하는 함수명**을 사용해야 한다.
-   커스텀 훅 **내부에 다른 리액트 훅**을 사용할 수 있다.

<br/>

### 4) 훅 사용 시 주의 사항

-   컴포넌트나 커스텀 훅의 **최상위 레벨에서만 호출**해야 한다.
    -   자바스크립트 함수, 반복문, 조건문 내에서 호출할 수 없다.
    -   그 이유는, 리액트가 컴포넌트를 렌더할 때 **훅이 동일한 순서로 호출될 것이라고 가정**하기 때문이다.
-   훅을 **과도하게 사용**하면 오히려 코드의 **복잡성이 증가**한다.
-   **의존성 배열**이 정확히 명시되지 않으면 **불필요한 렌더링**이 발생한다.

<br/>

## 📄 리액트 컴포넌트 종류와 데이터 전달 방법

<br/>

---

## ✏️ 더 공부하고 싶은 것

### useRef

-   useRef와 비슷한 document.getElementById의 차이점 명확하게 구분하기
-   타입스크립트에서 useRef를 사용하기 어려웠던 기억이 있다. 타입스크립트에서 useRef 사용법 알아보기
