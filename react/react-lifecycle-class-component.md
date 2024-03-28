# 🔃 React Lifecycle (class component)

## #️⃣React Lifecycle&#x20;

React 컴포넌트가 생성될 때, 업데이트될 때, 그리고 제거될 때 일어나는 일련의 단계를 설명하는 개념으로 모든 React 컴포넌트는 동일한 생명주기를 거친다.

**생성(mounting) → 업데이트(updating) → 제거(unmounting)**

* 컴포넌트는 화면에 추가될 때 마운트된다.
* 컴포넌트는 새로운 props나 state를 받으면 업데이트된다. 이는 보통 상호작용에 대한 응답으로 발생한다.
* 화면에서 제거되면 컴포넌트가 마운트 해제된다.

<mark style="background-color:purple;">클래스형 컴포넌트</mark>의 경우 특정 <mark style="background-color:purple;">라이프 사이클 메소드</mark>를 사용하며\
<mark style="background-color:red;">함수형 컴포넌트</mark>에서는 <mark style="background-color:red;">Hook</mark>을 사용하여 클래스형 component 의 lifeCycle처럼 관리가 가능하다.



### [React의 생명주기 용어](https://adjh54.tistory.com/42#1\)%20React%EC%9D%98%20%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0%20%EC%9A%A9%EC%96%B4-1) <a href="#id-1-20react-ec-9d-98-20-ec-83-9d-eb-aa-85-ec-a3-bc-ea-b8-b0-20-ec-9a-a9-ec-96-b4-1" id="id-1-20react-ec-9d-98-20-ec-83-9d-eb-aa-85-ec-a3-bc-ea-b8-b0-20-ec-9a-a9-ec-96-b4-1"></a>

<table><thead><tr><th width="147">용어</th><th>설명</th></tr></thead><tbody><tr><td>~ will</td><td>어떤 '작업을 <strong>수행</strong>하기 <strong>전</strong>에 실행되는 메서드와 관련된 용어</td></tr><tr><td>~ did</td><td>어떤' 작업을 <strong>수행</strong>한 <strong>이후</strong>'에 실행되는 메서드와 관련된 용어</td></tr><tr><td>mount</td><td>컴포넌트 내에서 <strong>'DOM이 생성'</strong>되고 웹 브라우저 상에 <strong>나타나는</strong> 메서드와 관련된 용어</td></tr><tr><td>update</td><td>컴포넌트 내에서 <strong>'변화'</strong>가 발생했을 때 수행하는 것<br>ex) props, state, 부모 컴포넌트의 리 렌더링, forceUpdate를 통해 강제로 변경하는 경우</td></tr><tr><td>unmount</td><td>컴포넌트 내에서 <strong>'DOM이 제거'</strong>되고 웹 브라우저 상에 <strong>사라지는</strong> 메서드와 관련된 용어</td></tr></tbody></table>



***

## #️⃣Class Component Lifecycle&#x20;

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p><a href="https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/">react-lifecycle-methods-diagram</a></p></figcaption></figure>

### 1. Mounting&#x20;

#### ▸constructor() &#x20;

컴포넌트가 호출되어 로드가 된 이후 렌더링되기 이전에 '데이터 \*바인딩', '초기화'를 수행하기 위해 호출되는 함수.\
메서드를 바인딩하거나 state를 초기화하는 작업이 없다면, 해당 React 컴포넌트에는 생성자를 구현하지 않아도 된다.

_\*바인딩 : 두 개의 데이터 소스(또는 동일한 데이터에 대한 두 개의 개별 표현)를 함께 연결하고 동기화 상태를 유지하는 일반적인 기술. react에서는 부모 → 자식 단방향 바인딩이 이루어진다._

#### ▸render()

미리 구현된 HTML을 화면상에 그려지는 과정(렌더링)을 수행하는 함수\
클래스 컴포넌트에서 반드시 구현되야 하는 유일한 메서드이며 React.Component의 하위 class에서 반드시 정의해야 하는 메서드이다.

* 해당 메서드 안에서는 부모 컴포넌트로 전달받은 'props 값의 접근'이 가능하다.
* constructor()에서 정의한 'state 값의 접근이 가능하다.
* 해당 공간에서는 setState()를 사용할 수 없다.

#### ▸componentDidMount()&#x20;

화면이 렌더링 된 이후에 해당 '컴포넌트를 DOM 트리에 삽입'(마운트)이 되면 발생하는 메서드

* 자바스크립트 라이브러리 또는 프레임워크의 함수를 호출하거나 이벤트 등록에 사용
* setTimeout, setInterval, 네트워크 요청 같은 비동기 작업을 처리할 때 사용

### 2. Updating

#### ▸componentDidUpdate(prevProps, prevState, snapshot)

컴포넌트 내에서 '변화'가 발생된 이후 호출되는 메서드

DidMount()가 첫 렌더링 후에 호출 되는 함수라면, DidUpdate()는 리렌더링을 완료한 후 실행되는 함수이다.

1. props의 변경 : 부모 컴포넌트로부터 전달 받은 props 값의 변화가 발생하는 경우&#x20;
2. state의 변경 : 해당 컴포넌트 내에서 state의 값을 변경하는 경우&#x20;
3. forceUpdate() 수행: 메서드를 통해 강제로 변경하는 경우

### 3. Unmounting&#x20;

#### ▸componentWillUnmount()

컴포넌트가 DOM에서 제거되기 직전에 호출되는 메서드 (더는 컴포넌트를 사용하지 않을 때)\
\
1\. 컴포넌트에서 사용 중인 리소스를 해제하거나 구독을 취소하는 경우\
2\. 타이머를 해제하는 경우\
3\. 네트워크 요청을 취소하는 등의 클린업 작업을 하는 경우\


{% code fullWidth="false" %}
````javascript
import React from "react";

// 클래스형 컴포넌트
class LifecycleClassComponent extends React.Component {
  // constructor: 생성자 함수 - 초기값의 설정
  constructor(props) {
    super(props);
    this.state = {my_name: "Wynter24",};
    console.log("in constructor!");
  }

  changeMyName = () => {
    //state값 변경 
    this.setState({ cat_name: "Amanda" });
    console.log("이름을 변경합니다!");
  };

  //componentDidMount() 
  componentDidMount() {
    console.log("화면이 렌더링 된 이후에 바로 수행이 됨: componentDidMount()");
  }

  //componentDidUpdate
  // 컴포넌트 내에서 변화가 발생하였을 경우에 실행되는 메서드이다.
  // prevProps : 이전 Props의 값
  //  prevState : 이전 State의 값
  componentDidUpdate(prevProps, prevState) {
    console.log(prevProps, prevState);
    console.log("in componentDidUpdate!");
  }

  // componentWillUnmount
  componentWillUnmount() {
    console.log("해당 컴포넌트가 삭제 되었습니다.");
  }

  //render
  render() {
    console.log("in render!");
    return (
      <div>
        <h1>제 이름은 {this.state.my_name}입니다.</h1>
        <button onClick={this.changeMyName}>내 이름 바꾸기</button>
      </div>
    );
  }
}

export default LifecycleClassComponent;
```
````
{% endcode %}

***

### 👍🏻Class Component Lifecycle 장점

#### **불필요한 업데이트(리 렌더링) 방지**&#x20;

* 클래스형 컴포넌트에서는 `shouldComponentUpdate` 메서드를 사용하여 컴포넌트가 리 렌더링 되는 것을 방지한다.
* 이 메서드를 사용하면 컴포넌트의 상태나 속성이 변경되었을 때 리 렌더링을 수행할지 여부를 결정하여 불필요한 리렌더링을 방지할 수 있다.

#### **단순화된 상태 관리** &#x20;

* `setState`및 라이프사이클 메서드를 사용하여 상태 관리를 단순화할 수 있다.
* 이를 통해 상태의 변경을 효과적으로 관리, 코드의 가독성 향상, 상태 관련 버그를 줄일 수 있다.

#### **비동기 작업 처리 용이성**&#x20;

* `componentDidMount`, `componentDidUpdate` 등의 라이프사이클 메서드를 활용하여 비동기 작업을 처리할 수 있다.
* 이를 통해 초기 렌더링이 완료된 후에 비동기 작업을 수행하거나, 상태 또는 속성이 변경된 후에 비동기 작업을 다룰 수 있다.

### 👎🏻Class Component Lifecycle 단점

#### **상태 및 속성 관리의 복잡성**&#x20;

* 라이프사이클 메서드를 과도하게 사용하면 복잡성이 증가하고 코드의 유지보수 및 이해가 어려워질 수 있다.&#x20;
* 상태 관리를 위해 React Hooks나 Redux와 같은 라이브러리를 함께 사용하는 것이 중요하다.

#### **비동기 코드 관리의 어려움**&#x20;

* 복잡한 비동기 작업을 처리할 때 발생하는 코드의 복잡성과 오류 가능성이 있다.
* 이러한 어려움은 코드를 유지하고 이해하기 어렵게 만들 수 있다.
* ex. 여러 동시 네트워크 요청을 관리하거나 비동기 상태 업데이트를 처리하는 것은 코드를 복잡하게 만들고 오류 발생 가능성을 높일 수 있다.

비동기 상태 관리는 비동기 작업을 관리하는 것보다 명확하고 체계적인 방법을 제공하는 React Hooks 또는 외부 상태 관리 라이브러리를 통해 더 잘 처리된다.&#x20;

***

참고 사이트

[\[React\] 클래스 컴포넌트 생명주기(lifecycle) 이해하기](https://adjh54.tistory.com/42)

[The lifecycle of an Effect | Effect의 생명주기](https://react-ko.dev/learn/lifecycle-of-reactive-effects)&#x20;

[\[React\] 컴포넌트 생명주기 / 클래스형 , 함수형LifeCycle](https://suinchoi.tistory.com/40)

[What is React Lifecycle - Explain in Detail](https://www.theknowledgeacademy.com/blog/react-lifecycle/)
