# 🔁 Functional Component Lifecycle

## #️⃣Functional Component Lifecycle

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p><a href="https://wavez.github.io/react-hooks-lifecycle/">react-hook-lifecycle</a></p></figcaption></figure>



💡 이전 클래스 컴포넌트와 비교하여 함수형 컴포넌트에서는 클래스형 컴포넌트의 라이프 사이클 메서드로 사용되었던 constructor(), render(), ComponenDidMount(), componentDidUpdate(), componentWillUnmount()는 아래와 같이 사용한다.

> [\[참고\] 클래스형 컴포넌트와 함수형 컴포넌트의 비교](https://adjh54.tistory.com/43)

<table><thead><tr><th width="174" align="center">분류</th><th align="center">클래스형 컴포넌트</th><th align="center">함수형 컴포넌트</th></tr></thead><tbody><tr><td align="center">Mounting</td><td align="center">constructor()</td><td align="center">함수형 컴포넌트 내부</td></tr><tr><td align="center">Mounting</td><td align="center">render()</td><td align="center">return()</td></tr><tr><td align="center">Mounting</td><td align="center">ComponenDidMount()</td><td align="center">useEffect()</td></tr><tr><td align="center">Updating</td><td align="center">componentDidUpdate()</td><td align="center">useEffect()</td></tr><tr><td align="center">UnMounting</td><td align="center">componentWillUnmount()</td><td align="center">useEffect()</td></tr></tbody></table>

***

### useEffect() 를 사용하여 클래스 컴포넌트 라이프 사이클처럼 구현하기

#### useEffect()

리액트 컴포넌트가 렌더링 될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook

```javascript
useEffect(() => { },[]);

useEffect(() => { 
  // first: useEffect가 실행될 때 수행할 작업
  // (데이터 가져오기, 구독 설정 등)
  // componentDidMount :첫 렌더링 후 실행
  // componentDidUpdate :리렌더링을 완료한 후 실행

  return () => {
    // second: 컴포넌트가 unmount될 때 실행할 작업
    // (구독 해제, 정리 작업 등)
    // componentWillUnmount
  }
}, [third])
```

* `first` : 첫 번째 매개변수로 전달된 함수\
  컴포넌트가 렌더링될 때마다 실행된다. \
  이 함수는 부수 효과를 처리하고, 렌더링 결과에 영향을 주지 않아야 한다.
* `return`문 안에 있는 함수\
  컴포넌트가 unmount될 때 실행된다. \
  이것은 주로 useEffect에서 수행한 작업들을 정리하고, 메모리 누수를 방지하기 위해 사용된다.
* `[third]`: 의존성 배열\
  useEffect가 의존하는 값들을 배열로 받는다. 이 배열 안의 값이 변경될 때마다 다시 실행된다. \
  만약 `[third]` 대신 `[]`를 전달하면, useEffect는 컴포넌트가 처음 렌더링될 때만 실행된다.

***

### 함수형 컴포넌트를 선호하는 이유

이전에는 클래스형 컴포넌트에서만 상태와 라이프사이클을 다룰 수 있었으며 함수형 컴포넌트는 단순히 함수로 정의되어 있어 제한적이었다. **React Hooks의 등장**으로 함수형 컴포넌트가 상태와 라이프사이클을 효과적으로 다룰 수 있게 되었다. 이로써 함수형 컴포넌트는 **코드**가 더 **간결**하고 **명확**해졌다.&#x20;

React Hooks를 사용하면 \*상태 관리와 라이프사이클 처리에 대한 접근 방식이 클래스형 컴포넌트와는 달라진다. 이는 코드의 **일관성**과 **유연성**을 높인다.&#x20;

함수형 컴포넌트와 React Hooks를 함께 사용하면서 개발자는 더 직관적이고 간단한 코드를 작성할 수 있게 되었고, 이러한 이점으로 인해 함수형 컴포넌트가 현재 React 애플리케이션 개발에서 **더 많이 선호**되는 경향이 있다.

> _\*상태 관리와 라이프사이클 처리에 대한 접근 방식_
>
> \- 클래스형 컴포넌트 \
> &#x20;  `setState`를 사용하여 상태를 변경하고 라이프 사이클 메서드를 사용하여 비동기 작업 처리
>
> \- 함수형 컴포넌트\
> &#x20; `useState`, `useEffect` 등의 Hook 함수를 사용하여 코드가 간결하고 더 많은 유연성을 제공

1. **간결성과 가독성**\
   함수형 컴포넌트는 일반적으로 훨씬 더 간결하고 가독성이 높다. 클래스형 컴포넌트에서는 생성자, 라이프사이클 메서드, `this` 키워드 등을 사용해야 하지만, 함수형 컴포넌트에서는 이러한 것들이 필요하지 않다.
2. **라이프사이클 관리의 단순화**\
   함수형 컴포넌트에서는 React Hooks를 사용하여 상태와 라이프사이클 이벤트를 관리할 수 있다. \
   이는 클래스형 컴포넌트의 복잡한 라이프사이클 메서드보다 훨씬 직관적이고 간단하다.
3. **재사용성과 테스트 용이성**\
   함수형 컴포넌트는 순수 함수의 특성을 가지고 있어서 테스트하기가 더 쉽다. \
   또한, 함수형 컴포넌트는 더 작고 단순한 단위로 나누기가 더 쉬워서, 재사용성이 높아진다.

{% hint style="info" %}
#### 요약

함수형 컴포넌트는 React Hooks를 활용하여 상태 관리와 라이프사이클을 다루면서 코드의 간결성과 유연성이 향상되었다. 이러한 이점으로 인해 함수형 컴포넌트가 더 많은 선호를 받고 있다.
{% endhint %}

***

참고 사이트

[\[React\] 함수형 컴포넌트 생명주기(lifecycle) 이해하기](https://adjh54.tistory.com/43)

[\[React\] 컴포넌트 생명주기 / 클래스형 , 함수형LifeCycle](https://suinchoi.tistory.com/40)
