# Functional Component Lifecycle

### #️⃣Functional Component Lifecycle

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p><a href="https://wavez.github.io/react-hooks-lifecycle/">react-hook-lifecycle</a></p></figcaption></figure>

### React Hooks의 등장 계기 및 함수형 컴포넌트를 선호하는 이유

이전에는 클래스형 컴포넌트에서만 상태와 라이프사이클을 다룰 수 있었는데, 함수형 컴포넌트는 단순히 함수로 정의되어 있어서 상태와 라이프사이클 관리가 제한적이었다. 이러한 한계를 극복하기 위해 **React Hooks**가 등장했고, 함수형 컴포넌트에서도 상태와 라이프사이클을 다룰 수 있게 되었다.

React Hooks는 상태 관리 및 라이프사이클 사용의 제약을 극복하기 위해 등장했지만, 현재는 함수형 컴포넌트와 함께 사용되면서 함수형 컴포넌트가 더 많이 선호돼는 추세이다.

함수형 컴포넌트는 단순히 함수로 정의되어 있어서 코드가 더 간결하고 명확하며, React Hooks를 통해 상태와 라이프사이클을 다룰 수 있기 때문에 클래스형 컴포넌트보다 코드의 일관성이 더 높다.&#x20;

또한, React Hooks를 활용하여 상태 관리와 라이프사이클을 다룰 때, 클래스형 컴포넌트와는 다른 접근 방식을 사용할 수 있다. 예를 들어, 클래스형 컴포넌트에서는 `setState`를 사용하여 상태를 변경하고 라이프사이클 메서드를 사용하여 비동기 작업을 처리할 수 있지만, React Hooks에서는 `useState`, `useEffect` 등의 Hook 함수를 사용하여 상태와 라이프사이클을 다룬다. 이로 인해 코드가 간결하고 더 많은 유연성을 제공할 수 있다.

{% hint style="info" %}
#### 요약

함수형 컴포넌트는 React Hooks를 활용하여 상태 관리와 라이프사이클을 다루면서코드의 간결성과 유연성이 향상되었다. 이러한 이점으로 인해 함수형 컴포넌트가 더 많은 선호를 받고 있다.
{% endhint %}

***

### #️⃣React Hooks&#x20;

함수형은 클래스형에 비해 기능은 작지만 간결하고 빠르다.&#x20;

react 18.6이 출시되며 hooks가 기능이 작다는 단점을 보완해주었다.&#x20;

\*Hook: 함수형 컴포넌트에서 React state와 생명주기 기능을 연동 할 수 있게 해주는 함수

사용 규칙

1. 최상위에서만 Hook을 호출 반복문, 조건문, 중첩된 함수 내에서 Hook을 실행하면 안된다. \
   → 렌더링될 때마다 항상 동일한 순서로 Hook이 호출되는 것이 보장
2. 리액트 함수 컴포넌트에서만 호출



***

참고 사이트

