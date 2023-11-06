# Basic Syntax - 02

---

# INDEX

### 1. Computed Property

### 2. Conditional Rendering

### 3. List Rendering

### 4. Watchers

### 5. Lifecycle Hooks

### 6. Vue Style Guide

---

# 1. Computed Properties

---

## Computed

### 1. `computed()`

- 계산된 속성을 정의하는 함수
- 미리 계산된 속성을 사용하여 템플릿에서 표현식을 단순하게 하고 불필요한 반복 연산을 줄임

### 2. `computed` 기본 예시

1. 할 일이 남았는지 여부에 따라 다른 메시지를 출력하기

   ```html
   <h2>남은 할일</h2>
   <p>{{todos.length > 0 ? '아직 남았다' : '퇴근!'}}</p>
   ```

   ```javascript
   const todos = ref([
     { text: "Vue 실습" },
     { text: "자격증 공부" },
     { text: "TIL 작성" },
   ]);
   ```

   - 템플릿이 복잡해지며 todos에 따라 계산을 수행하게 됨
   - 만약 이 계산을 템플릿에 여러 번 사용하는 경우에는 반복이 발생

2. `computed` 적용

   - 반응성 데이터를 포함하는 복잡한 로직의 경우 `computed`를 활용하여 미리 값을 계산

   ```html
   <h2>남은 할일</h2>
   <p>{{restOfTodos}}</p>
   ```

   ```javascript
   const { createApp, ref, computed } = Vue;

   const restOfTodos = computed(() => {
     return todos.value.length > 0 ? "아직 남았다" : "퇴근!";
   });
   ```

### 3. `computed` 특징

1. 반환되는 값을 `computed ref`이며 일반 `refs`와 유사하게 계산된 결과를 `.value`로 참조할 수 있음 (템플릿에서는 `.value` 생략가능)
2. `computed` 속성은 의존된 반응형 데이터를 자동으로 추적
3. 의존하는 데이터가 변경될 때만 재평가
   - restOfTodos의 계산은 todos에 의존하고 있음
   - 따라서 todos가 변경될 때만 restOfTodos가 업데이트 됨
   ```javascript
   const restOfTodos = computed(() => {
     return todos.value.length > 0 ? "아직 남았다" : "퇴근!";
   });
   ```

---

## `computed` vs `Methods`

### 1. `computed`와 동일한 로직을 처리할 수 있는 `method`

- `computed` 속성 대신 `method`로도 동일한 기능을 정의할 수 있음
- 두 가지 접근 방식은 실제로 완전히 동일
  ```html
  <p>{{getRestOfTodos}}</p>
  ```
  ```javascript
  const getRestOfTodos = function () {
    return todos.value.length > 0 ? "아직 남았다" : "퇴근!";
  };
  ```

### 2. `computed`와 `Methods` 차이

1. `computed` 속성은 의존된 반응형 데이터를 기반으로 캐시(cached)된다.
2. 의존하는 데이터가 변경된 경우에만 재평가됨
3. 즉, 의존된 반응형 데이터가 변경되지 않는 한 이미 계산된 결과에 대한 여러 참조는 다시 평가할 필요 없이 이전에 계산된 결과를 즉시 반환

- 반면, `Methods` 호출은 다시 렌더링이 발생할 때마다 함수를 실행

### 3. Cache(캐시)

- 데이터나 결과를 일시적으로 저장해두는 임시 저장소
- 이후에 같은 데이터나 결과를 다시 계산하지 않고 빠르게 접근할 수 있도록 함

### 4. Cache 예시

- "웹 페이지의 캐시 데이터"
  - 페이지 일부 데이터를 브라우저 캐시에 저장 후 같은 페이지에 다시 요청 시 모든 데이터를 다시 응답 받는 것이 아닌 캐시 된 데이터를 사용하여 더 빠르게 웹 페이지를 렌더링

### 5. `computed`와 `Methods`의 적절한 사용처

1. `computed`
   - 의존하는 데이터에 따라 결과가 바뀌는 계산된 속성을 만들 때 유용
   - 동일한 의존성을 가진 여러 곳에서 사용할 때 계산 결과를 캐싱하여 중복 계산 방지
2. `Methods`
   - 단순히 특정 동작을 수행하는 함수를 정의할 때 사용
   - 데이터에 의존하는지 여부와 관계없이 항상 동일한 결과를 반환하는 함수

### 6. `computed`와 `Methods`

1. `computed`
   - 의존된 데이터가 변경되면 자동으로 업데이트
2. `Methods`
   - 호출해야만 실행됨

- 무조건 `computed`만 사용하는 것이 아니라 사용 목적과 상황에 맞게 `computed`와 `Methods`를 적절히 조합하여 사용

---

# 2. Conditional Rendering

---

## `v-if`

### 1. `v-if`

- 표현식 값이 T/F를 기반으로 요소를 조건부로 렌더링

### 2. `v-if`예시

1. `v-else` directive를 사용하여 `v-if`에 대한 else 블록을 나타낼 수 있음

   ```html
   <p v-if="isSeen">true일때 보여요</p>
   <p v-else>false일때 보여요</p>
   <button @click="isSeen = !isSeen">토글</button>
   ```

   ```javascript
   const isSeen = ref(true);
   ```

2. `v-else-if` directive를 사용하여 `v-if`에 대한 else if 블록을 나타낼 수 있음

   ```html
   <div v-if="name==='Alice'">Alice입니다.</div>
   <div v-else-if="name==='Bella'">Bella입니다.</div>
   <div v-else-if="name==='Cathy'">Cathy입니다.</div>
   <div v-else>아무도 아닙니다.</div>
   ```

   ```javascript
   const name = ref("Cathy");
   ```

### 3. 여러 요소에 대한 `v-if`적용

- `v-if`는 directive이기 때문에 단일 요소에만 연결 가능
- 이 경우 template 요소에 `v-if`를 사용하여 하나 이상의 요소에 대해 적용 할 수 있음 (`v-else`, `v-else-if` 모두 적용 가능)
  ```html
  <template v-if="name==='Cathy'">
    <div>Cathy입니다</div>
    <div>나이는 30살입니다</div>
  </template>
  ```

### 4. HTML `<template>` element

- 페이지가 로드 될 때 렌더링 되지 않지만 JavaScript를 사용하여 나중에 문서에서 사용할 수 있도록 하는 HTML을 보유하기 위한 메커니즘
- "보이지 않는 wrapper 역할"

---

## `v-if` vs `v-show`

### 1. `v-show`

- 표현식 값이 T/F를 기반으로 요소의 가시성을 전환

### 2. `v-show` 예시

1. `v-show` 요소는 항상 렌더링 되어 DOM에 남아있음
2. CSS display 속성만 전환하기 때문
   ```html
   <div v-show="isShow">v-show</div>
   ```
   ```javascript
   const isShow = ref(false);
   ```

### 3. `v-if` vs `v-show`

1. `v-if`(Cheap initial load, expensive toggle)
   - 초기 조건이 false인 경우 아무 작업도 수행하지 않음
   - 토글 비용이 높음
2. `v-show`(Expensive initial load, cheep toggle)
   - 초기 조건에 관계 없이 항상 렌더링
   - 초기 렌더링 비용이 더 높음

- 우언가를 매우 자주 전환해야 하는 경우에는 `v-show`를, 실행 중에 조건이 변경되지 않는 경우에는 `v-if`를 권장

---

# 3. List Rendering

---

## `v-for`

### 1. `v-for`

- 소스 데이터를 기반으로 요소 또는 템블릿 블록을 여러 번 렌더링
  (Array, Object, number, string, iterable)

### 2. `v-for` 구조

1. `v-for`는 alias in experssion 형식의 특수 구문을 사용하여 반복되는 현재 요소에 대한 별칭(alias)을 제공

   ```html
   <div v-for="item in items">{{ item.text }}</div>
   ```

2. 인덱스(객체에서는 키)에 대한 별칭을 지정할 수 있음

   ```html
   <div v-for="(item, index) in items"></div>

   <div v-for="value in object"></div>
   <div v-for="(value, key) in object"></div>
   <div v-for="(value, key, index) in object"></div>
   ```

### 3. `v-for` 예시

1. 배열 반복
   ```html
   <div v-for="(item, index) in myArr">{{index}} / {{item}}</div>
   ```
   ```javascript
   const myArr = ref([
     { name: "Alice", age: 20 },
     { name: "Bella", age: 21 },
   ]);
   ```
2. 객체 반복
   ```html
   <div v-for="(value, key, index) in myObj">
     {{index}} / {{key}} / {{value}}
   </div>
   ```
   ```javascript
   const myObj = ref({
     name: "Cathy",
     age: 30,
   });
   ```

### 4. 여러 요소에 대한 `v-for` 적용

- template 요소에 `v-for`를 사용하여 하나 이상의 요소에 대해 반복 렌더링 할 수 있음
  ```html
  <ul>
    <template v-for="item in myArr">
      <li>{{item.name}}</li>
      <li>{{item.age}}</li>
      <hr />
    </template>
  </ul>
  ```

### 5. 중첩된 `v-for`

- 각 `v-for` 범위는 상위 범위에 접근 할 수 있음

  ```html
  <ul v-for="item in myInfo">
    <li v-for="friend in item.friends">{{item.name}} - {{friend}}</li>
  </ul>
  ```

  ```javascript
  const myInfo = ref([
    { name: "Alice", age: 20, friends: ["Bella", "Cathy", "Dan"] },
    { name: "Bella", age: 21, friends: ["Alice", "Cathy"] },
  ]);
  ```

---

## `v-for` with key

### 1. 반드시 `v-for`와 key를 함께 사용한다

- 내부 컴포넌트의 상태를 일괄되게 유지
- 데이터의 예측 가능한 행동을 유지 (Vue 내부 동작 관련)

### 2. `v-for` 와 key

- key는 반드시 각 요소에 대한 고유한 값을 나타낼 수 있는 식별자여야 함
  ```html
  <div v-for="item in items" :key="item.id">
    <!-- content -->
  </div>
  ```
  ```javascript
  let id = 0;
  const items = ref([
    { id: id++, name: "Alice" },
    { id: id++, name: "Bella" },
  ]);
  ```

---

## `v-for` with `v-if`

### 1. 동일 요소에 `v-for`와 `v-if`를 함께 사용하지 않는다

- 동일한 요소에서 `v-if`가 `v-for`보다 우선순위가 더 높기 때문
- `v-if`조건은 `v-for` 범위의 변수에 접근할 수 없음

### 2. `v-for`와 `v-if` 문제 상황 - 1

- todo 데이터 중 이미 처리한 (`isComplete === true`) todo 만 출력하기

  ```html
  <ul>
    <li v-for="todo in todos" v-if="!todo.isComplete" :key="todo.id">
      {{ todo.name }}
    </li>
  </ul>
  ```

  ```javascript
  let id = 0;

  const todos = ref([
    { id: id++, name: "복습", isComplete: true },
    { id: id++, name: "예습", isComplete: false },
    { id: id++, name: "저녁식사", isComplete: true },
    { id: id++, name: "노래방", isComplete: false },
  ]);
  ```

### 3. `v-for`와 `v-if` 해결법 - 1

- `computed`를 활용해 필터링 된 목록을 반환하여 반복하도록 설정

  ```html
  <ul>
    <li v-for="todo in completeTodos" :key="todo.id">{{todo.name}}</li>
  </ul>
  ```

  ```javascript
  const completeTodos = computed(() => {
    return todos.value.filter((todo) => !todo.isComplete);
  });
  ```

### 4. `v-for`와 `v-if` 문제 상황 - 2

- `v-if`가 더 높은 우선순위를 가지므로 `v-for`의 todo 요소를 `v-if`에서 사용할 수 없음
  ```html
  <ul>
    <li v-for="todo in todos" v-if="!todo.isComplete" :key="todo.id">
      {{ todo.name }}
    </li>
  </ul>
  <!--
    Uncaught TypeError: Cannot read properties of undefined (reading 'isComplete')
  -->
  ```

### 5. `v-for`와 `v-if` 해결법 - 2

- `v-for`와 template 요소를 사용하여 `v-if`를 이동
  ```html
  <ul>
    <template v-for="todo in todos" :key="todo.id">
      <li v-if="!todo.isComplete">{{ todo.name }}</li>
    </template>
  </ul>
  ```

---

# 4. Watchers

---

### 1. `watch()`

- 반응형 데이터를 감시하고, 감시하는 데이터가 변경되면 콜백 함수를 호출

### 2. `watch` 구조

```javascript
watch(variable, (newValue, oldValue) => {
  // do something
});
```

1. variable
   - 감시하는 변수
2. newValue
   - 감시하는 변수가 변화된 값
   - 콜백 함수의 첫 번째 인자
3. oldValue
   - 콜백 함수의 두 번째 인자

### 3. `watch` 예시

1. 감시하는 변수에 변화가 생겼을 때 기본 동작 확인하기

   ```html
   <button @click="count++">Add1</button>
   <p>Count: {{count}}</p>
   ```

   ```javascript
   const count = ref(0);

   const countWatch = watch(count, (newValue, oldValue) => {
     console.log(`newValue: ${newValue}, oldValue: ${oldValue}`);
   });
   ```

   ```
   newValue: 1, oldValue: 0
   newValue: 2, oldValue: 1
   newValue: 3, oldValue: 2
   ```

2. 감시하는 변수에 변화가 생겼을 때 연관 데이터 업데이트하기

   ```html
   <input v-model="message" />
   <p>Message length: {{messageLength}}</p>
   ```

   ```javascript
   const message = ref("");
   const messageLength = ref(0);

   const messageWatch = watch(message, (newValue, oldValue) => {
     messageLength.value = newValue.length;
   });
   ```

### 4. Computed와 Watchers

1. 공통점
   - 데이터의 변화를 감지하고 처리
2. 동작
   - Computed : 의존하는 데이터 속성의 계산된 값을 반환
   - Watchers : 특정 데이터 속성의 변화를 감시하고 작업을 수행
3. 사용목적
   - Computed : 템플릿 내에서 사용되는 데이터 연산용
   - Watchers : 데이터 변경에 따른 특정 작업 처리용
4. 사용 예시
   - Computed : 연산 된 길이, 필터링 된 목록 계산 등
   - Watchers : 비동기 API 요청, 연관 데이터 업데이트

- computed와 watch 모두 의존(감시)하는 원본 데이터를 직접 변경하지 않음

---

# 5. Lifecycle Hooks

---

### 1. Lifecycle Hooks

- Vue 인스턴스의 생애주기 동안 특정 시점에 실행되는 함수
- 개발자가 특정 단계에서 의도하는 로직이 실행될 수 있도록 함

### 2. Lifecycle Hooks 예시

1. Vue 컴포넌트 인스턴스가 초기 렌더링 및 DOM 요소 생성이 완료된 후 특정 로직을 수행하기

   ```javascript
   const { createApp, ref, onMounted } = Vue;
   ```

   ```javascript
   setup(){
       onMounted(()=>{
           console.log('mounted')
       })
   }
   ```

   ```
   mounted
   ```

2. 반응형 데이터의 변경으로 인해 컴포넌트의 DOM이 업데이트 된 후 특정 로직을 수행하기

   ```html
   <button @click="count++">Add 1</button>
   <p>Count: {{count}}</p>
   <p>{{message}}</p>
   ```

   ```javascript
   const { createApp, ref, onMounted, onUpdated } = Vue;
   ```

   ```javascript
   const count = ref(0);
   const message = ref(null);
   onUpdated(() => {
     message.value = "updated!";
   });
   ```

### 3. Lifecycle Hooks 특징

1. Vue는 Lifecycle Hooks에 등록된 콜백 함수들을 인스턴스와 자동으로 연결함
2. 이렇게 동작하려면 hooks 함수들은 반드시 동기적으로 작성되어야 함
3. 인스턴스 생애 주기의 여러 단계에서 호출되는 다른 hooksLifecycle Hook도 있으며, 가장 일반적으로 사용되는 것은 `onMounted`, `onUpdated`, `onUnmounted`

- https://vuejs.org/api/composition-api-lifecycle.html

---

# 6. Vue Style Guide

---

### 1. Vue Style Guide

- Vue의 스타일 가이드 규칙은 우선순위에 따라 4가지 범주로 나눔
- 규칙 범주
  1. 우선순위 A : 필수 (Essential)
  2. 우선순위 B : 적극 권장 (Strongly Recommended)
  3. 우선순위 C : 권장 (Recommended)
  4. 우선순위 D : 주의 필요 (Use with Caution)
- https://vuejs.org/style-guide/

### 2. 우선순위 별 특징

1. A : 필수 (Essential)
   - 오류를 방지하는 데 도움이 되브로 어떤 경우에도 규칙을 학습하고 준수
2. B : 적극 권장 (Strongly Recommended)
   - 가독성 및/또는 개발자 경험을 향상시킴
   - 규칙을 어겨도 코드는 여전히 실행되겠지만, 정당한 사유가 있어야 규칙을 위반할 수 있음
3. C : 권장 (Recommended)
   - 일관성을 보장하도록 임의의 선택을 할 수 있음
4. D : 주의 필요 (Use with Caution)
   - 잠재적 위험 특성을 고려함

### 3 우선순위 A였던 금일 학습 내용

1. `v-for`에 `key` 작성하기
2. 동일 요소에 `v-if`와 `v-for` 함께 사용하지 않기

---

# 참고

---

### 1. [주의] `computed`의 반환 값을 변경하지 말 것

- `computed`의 반환 값을 의존하는 데이터의 파생된 값
- 일종의 snapshot 이며 의존하는 데이터가 변경될 때 마다 새 snapshot이 생성됨
- snapshot을 변경하는 것은 의미가 없으므로 계산된 반환 값은 읽기 전용으로 취급되어야 하며 변경되어서는 안됨
- 대신 새 값을 얻기 위해서는 의존하는 데이터를 업데이트 해야 함

### 2. [주의] `computed` 사용 시 원본 배열 변경하지 말 것

- `computed`에서 `reverse()` 및 `sort()` 사용시 원본 배열을 변경하기 때문에 복사본을 만들어서 진행 해야 함
- 틀린 예시
  ```javascript
  return numbers.reverse();
  ```
- 올바른 예시
  ```javascript
  return [...numbers].reverse();
  ```

### 3. [주의] 배열의 인덱스를 `v-for`의 key로 사용하지 말 것

- 틀린 예시
  ```html
  <div v-for="(item, index) in items" :key="index">
    <!-- content -->
  </div>
  ```
- 인덱스는 식별자가 아닌 배열의 항목 위치만 나타내기 때문에 Vue가 DOM을 변경 할 때 (끝이 아닌 위치에 새 항목이 배열에 삽입되면) 여러 컴포넌트간 데이터 공유 시 문제가 발생
- 직접 고유한 값을 만들어내는 메서드를 만들거나 외부 라이브러리 등을 활용하는 등 식별자 역할을 할 수 있는 값을 만들어 사용

### 4. `v-for`와 배열 - "배열 변경 감지"

- 수정 메서드 (원본 배열 수정)
  - Vue는 반응형 배열의 변경 메소드가 호출 되는 것을 감지하여, 필요한 업데이트를 발생시킴
  - `push`, `pop()`, `shift()`, `unshift()`, `splice()`, `sort()`, `reverse()`
- 배열 교체
  - 원본 배열을 수정하지 않고 항상 새 배열을 반환
  - `filter`, `concat()`, `slice()`

### 5. `v-for`와 배열 - "필터링/정렬 결과 표시"

- 원본 데이터를 수정하거나 교체하지 않고 필터링 되거나 정렬된 결과를 표시
  1. `computed` 활용
  2. `method` 활용 (`computed` 가 불가능한 중첩된 `v-for`에 경우)

1. `computed` 활용

   ```html
   <li v-for="num in evenNumbers">{{num}}</li>
   ```

   ```javascript
   const numbers = ref([1, 2, 3, 4, 5]);
   const evenNumbers = computed(() => {
     return numbers.value.filter((number) => number % 2 === 0);
   });
   ```

2. `method` 활용

   ```html
   <ul v-for="numbers in numberSets">
     <li v-for="num in evenNumbers(numbers)">{{num}}</li>
   </ul>
   ```

   ```javascript
   const numberSets = ref([
     [1, 2, 3, 4, 5],
     [6, 7, 8, 9, 10],
   ]);

   const evenNumbers = function (numbers) {
     return numbers.filter((number) => number % 2 === 0);
   };
   ```

---
