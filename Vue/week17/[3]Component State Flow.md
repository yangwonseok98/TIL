# Component State Flow

---

# INDEX

### 1. Passing Props

### 2. Component Events

---

# 1. Passing Props

---

## 개요

### 1. 같은 데이터 하지만 다른 컴포넌트

- 동일한 사진 데이터가 한 화면에 다양한 위치에서 여러 번 출력되고 있음
- 하지만 해당 페이지를 구성하는 컴포넌트가 여러 개라면 각 컴포넌트가 개별적으로 동일한 데이터를 관리해야 할까?
- 그렇다면 사진을 변경 해야 할 때 모든 컴포넌트에 대해 변경 요청을 해야 함
- "공통된 부모 컴포넌트에서 관리하자"
  ### 부모는 자식에게 데이터를 전달(Pass Props)하며, 자식은 자신에게 일어난 일을 부모에게 알림(Emit event)

### 2. Props

- 부모 컴포넌트로부터 자식 컴포넌트로 데이터를 전달하는데 사용되는 속성

### 3. One-Way Data Flow

- 모든 props는 자식 속성과 부모 속성 사이에 하향식 단방향 바인디을 형성 (one-way-down binding)

### 4. Props 특징

1. 부모 속성이 업데이트되면 자식으로 흐르지만 그 반대는 안됨
2. 즉, 자식 컴포넌트 내부에서 props를 변경하려고 시도해서는 안되며 불가능
3. 또한 부모 컴포넌트가 업데이트될 때마다 자식 컴포넌트의 모든 props가 최신 값으로 업데이트 됨

   ### 부모 컴포넌트에서만 변경하고 이를 내려 받는 자식 컴포넌트는 자연스럽게 갱신

### 5. 단방향인 이유

- 하위 컴포넌트가 실수로 상위 컴포넌트의 상태를 변경하여 앱에서의 데이터 흐름을 이해하기 어렵게 만드는 것을 방지하기 위함

---

## 사전 준비

### 1. 사전 준비

1. Vue 프로젝트 생성
2. 초기 생성된 컴포넌트 모두 삭제(App.vue 제외)
3. src/assets 내부 파일 모두 삭제
4. main.js 해당 코드 삭제

   ```javascript
   //main.js

   import "./assets/main.css"; // 삭제
   ```

### 2. App > Parent > ParentChild 컴포넌트 관계 작성

1. App 컴포넌트 작성

```html
<!--App.vue-->
<template>
  <div>
    <Parent />
  </div>
</template>

<script setup>
  import Parent from "@/components/Parent.vue";
</script>

<style scoped></style>
```

2. Parent 컴포넌트 작성

```html
<!--Parent.vue-->
<template>
  <div>
    <ParentChild />
  </div>
</template>

<script setup>
  import ParentChild from "@/components/ParentChild.vue";
</script>

<style scoped></style>
```

3. ParentChild 컴포넌트 작성

```html
<!--ParentChild.vue-->
<template>
  <div></div>
</template>

<script setup></script>

<style scoped></style>
```

---

## Props 선언

### 1. Props 선언

- 부모 컴포넌트에서 보낸 props를 사용하기 위해서는 자식 컴포넌트에서 명시적인 props 선언이 필요

### 2. Props 작성

- 부모 컴포넌트 Parent에서 자식 컴포넌트 ParentChild에 보낼 props 작성

  ```html
  <!--Parent.vue-->
  <template>
    <div>
      <ParentChild my-msg="message" />
    </div>
  </template>

  <script setup>
    import ParentChild from "@/components/ParentChild.vue";
  </script>

  <style scoped></style>
  ```

- `my-msg="message"`
  - my-msg : prop 이름
  - "message" : prop 값

### 3. Props 선언 2가지 방식

1. 문자열 배열을 사용한 선언
2. 객체를 사용한 선언

### 4. 문자열 배열을 사용한 선언

- `defineProps()`를 사용하여 props를 선언

  ```html
  <!--ParentChild.vue-->
  <template>
    <div>{{ myMsg }}</div>
  </template>

  <script setup>
    defineProps(["myMsg"]);
  </script>

  <style scoped></style>
  ```

### 5. 객체를 사용한 선언

- 객체 선언 문법의 각 객체 속성의 키는 props의 이름이 되며, 객체 속성의 값은 값이 될 데이터의 타입에 해당하는 생성자 함수(`Number`,`String`...) 여야 함
- 객체 선언 문법 사용 권장

```html
<!--ParentChild.vue-->
<template>
  <div>{{ myMsg }}</div>
</template>

<script setup>
  defineProps({
    myMsg: String,
  });
</script>

<style scoped></style>
```

### 6. prop 데이터 사용

1. 템플릿에서 반응형 변수와 같은 방식으로 활용
   ```html
   <!--ParentChild.vue-->
   <template>
     <div>{{ myMsg }}</div>
   </template>
   ```
2. props를 객체로 반환하므로 필요한 경우 JavaScript에서 접근 가능

   ```html
   <!--ParentChild.vue-->
   <script setup>
     const props = defineProps({
       myMsg: String,
     });
     console.log(props);
     console.log(props.myMsg);
   </script>
   ```

3. prop 출력 결과 확인

### 7. 한 단계 더 prop 내려 보내기

1. ParentChild 컴포넌트를 부모로 갖는 ParentGrandChild 컴포넌트 생성 및 등록

   ```html
   <!--ParentGrandChild.vue-->
   <template>
     <div></div>
   </template>

   <script setup></script>

   <style scoped></style>
   ```

   ```html
   <!--ParentChild.vue-->
   <template>
     <div>
       {{ myMsg }}
       <ParentGrandChild />
     </div>
   </template>

   <script setup>
     import ParentGrandChild from "@/components/ParentGrandChild.vue";

     defineProps({
       myMsg: String,
     });
   </script>

   <style scoped></style>
   ```

2. ParentChild 컴포넌트에서 Parent로 부터 받은 prop인 myMsg를 ParentGrandChild에게 전달

   ```html
   <!--ParentGrandChild.vue-->
   <template>
     <div>
       {{ myMsg }}
       <ParentGrandChild :my-msg="myMsg" />
     </div>
   </template>
   ```

   ```html
   <!--ParentChild.vue-->
   <template>
     <div>
       <p>{{ myMsg }}</p>
     </div>
   </template>

   <script setup>
     defineProps({
       myMsg: String,
     });
   </script>
   ```

3. 출력 결과 확인
   - ParentGrandChild가 받아서 출력하는 prop은 Parent에 정의 되어있는 prop이며 Parent가 prop을 변경할 경우 이를 전달받고 있는 ParentChild, ParentGrandChild에서도 모두 업데이트 됨

---

## Props 세부사항

### 1. Props 세부사항

1. Props Name Casing (Props 이름 컨벤션)
2. Static Props & Dynamic Props

### 2. Props Name Casing

1. 선언 및 템플릿 참조 시 (-> `camelCase`)

   ```html
   <p>{{ myMsg }}</p>
   ```

   ```javascript
   defineProps({
     myMsg: String,
   });
   ```

2. 자식 컴포넌트로 전달 시 (-> `kebab-case`)

   ```html
   <ParentChild my-msg="message" />
   ```

   ### 기술적으로 camelCase도 가능하나 HTML 속성 표기법과 동일하게 kebab-case로 표기할 것을 권장

### 3. Static Props & Dynamic Props

- 지금까지 작성한 것은 Static(정적) props
  - v-bind를 사용하여 동적으로 할당된 props를 사용할 수 있음

1. Dynamic props 정의

   ```javaScript
   // Parent.vue
   import { ref } from "vue";

   const name = ref("Alice");
   ```

   ```html
   <!--Parent.vue-->
   <ParentChild my-msg="message" :dynamic-props="name" />
   ```

2. Dynamic props 선언 및 출력
   ```javascript
   // ParentChild.vue-->
   defineProps({
     myMsg: String,
     dynamicProps: String,
   });
   ```
   ```html
   <!--ParentChild.vue-->
   <p>{{ dynamicProps }}</p>
   ```
3. Dynamic props 출력 확인

---

# 2. Component Events

---

## 개요

- 부모는 자식에게 데이터를 전달(Pass Props)하며, 자식은 자신에게 일어난 일을 부모에게 알림(Emit event)
  ### 부모가 prop 데이터를 변경하도록 소리쳐야 한다.

### 1. `$emit()`

- 자식 컴포넌트가 이벤트를 발생시켜 부모 컴포넌트로 데이터를 전달하는 역할의 메서드
- '$' 표기는 Vue 인스턴스나 컴포넌트 내에서 제공되는 전역 속성이나 메서드를 식별하기 위한 접두어

### 2. emit 메서드 구조

#### `$emit(event, ...args)`

1. event : 커스텀 이벤트 이름
2. args : 추가 인자

---

## Event 발신 및 수신

### 1. 이벤트 발신 및 수신 (Emitting and Listening to Events)

1. `$emit`을 사용하여 템플릿 표현식에서 직접 사용자 정의 이벤트를 발신

   ```html
   <button @click="$emit('someEvent')"></button>
   ```

2. 그러면 부모는 v-on을 사용하여 수신할 수 있음

   ```html
   <ParentComp @some-event="someCallback" />
   ```

### 2. 이벤트 발신 및 수신하기

1. ParentChild에서 someEvent라는 이름의 사용자 정의 이벤트를 발신

   ```html
   <!--ParentChild.vue-->
   <button @click="$emit('someEvent')"></button>
   ```

2. ParentChild의 부모 Parent는 `v-on`을 사용하여 발신된 이벤트를 수신

   - 수신 후 처리할 로직 및 콜백함수 호출

   ```html
   <!--Parent.vue-->
   <ParentChild
     @some-event="someCallback"
     my-msg="message"
     :dynamic-props="name"
   />
   ```

   ```javascript
   // Parent.vue
   const someCallback = function () {
     console.log("ParentChild가 발신한 이벤트를 수신했어요.");
   };
   ```

3. 이벤트 수신 결과 확인

---

## 'emit'Event 선언

### 1. emit 이벤트 선언

- `defineEmits()`를 사용하여 명시적으로 발신할 이벤트를 선언할 수 있음
- script에서 `$emit` 메서드를 접근할 수 없기 때문에 `defineEmits()`는 `$emit` 대신 사용할 수 있는 동등한 함수를 반환

```html
<script setup>
  const emit = defineEmits(["someEvent", "myFocus"]);
  const buttonClick = function () {
    emit("someEvent");
  };
</script>
```

### 2. 이벤트 선언하기

- 이벤트 선언 방식으로 추가 버튼 작성 및 결과 확인

```html
<!--ParentChild.vue-->
<script setup>
  const emit = defineEmits(["someEvent"]);
  const buttonClick = function () {
    emit("someEvent");
  };
</script>
```

```html
<!--ParentChild.vue-->
<button @click="buttonClick">클릭</button>
```

---

## Event 인자

### 1. 이벤트 인자 (Event Arguments)

- 이벤트 발신 시 추가 인자를 전달하여 값을 제공할 수 있음

### 2. 이벤트 인자 전달하기

1. ParentChild에서 이벤트를 발신하여 Parent로 추가 인자 전달하기

   ```javascript
   // ParentChild.vue
   const emit = defineEmits(["someEvent", "emitArgs"]);

   const emitArgs = function () {
     emit("emitArgs", 1, 2, 3);
   };
   ```

   ```html
   <!--ParentChild.vue-->
   <button @click="emitArgs">추가 인자 전달</button>
   ```

2. ParentChild에서 발신한 이벤트를 Parent에서 수신

   ```html
   <!--Parent.vue-->
   <ParentChild
     @some-event="someCallback"
     @emit-args="getNumbers"
     my-msg="message"
     :dynamic-props="name"
   />
   ```

   ```javascript
   // Parent.vue
   const getNumbers = function () {
     console.log(args);
     console.log(`ParentChild가 전달한 추가인자 ${args}를 수신했어요.`);
   };
   ```

3. 추가 인자 전달 확인

---

## Event 세부사항

### 1. Event Name Casing

1. 선언 및 발신 시 (-> `camelCase`)
   ```html
   <button @click="buttonClick">클릭</button>
   ```
   ```javascript
   const emit = defineEmits(["someEvent"]);
   emit("someEvent");
   ```
2. 부모 컴포넌트에서 수신 시(-> `kebab-case`)

   ```html
   <ParentChild @some-event="..." />
   ```

---

## emit Event 실습

### 1. emit Event 실습

- 최하단 컴포넌트 ParentGrandChild에서 Parent 컴포넌트의 name 변수 변경 요청하기

### 2. emit 이벤트 실습 구현

1. ParentGrandChild에서 이름 변경을 요청하는 이벤트 발신

   ```javascript
   // ParentGrandChild
   const emit = defineEmits(["updateName"]);

   const updateName = function () {
     emit("updateName");
   };
   ```

   ```html
   <!--ParentGrandChild-->
   <button @click="updateName">이름 변경</button>
   ```

2. 이벤트 수신 후 이름을 변경을 요청하는 이벤트 발신

   ```javascript
   // ParentChild.vue
   const emit = defineEmits(["updateName"]);

   const updateName = function () {
     emit("updateName");
   };
   ```

   ```html
   <!--ParentChild.vue-->
   <ParentGrandChild :my-msg="myMsg" @update-name="updateName" />
   ```

3. 이벤트 수신 후 이름 변수 변경 메서드 호출

   - 해당 변수를 prop으로 받는 모든 곳에서 자동 업데이트

   ```html
   <ParentChild @update-name="updateName" />
   ```

   ```javascript
   const updateName = function () {
     name.value = "Bella";
   };
   ```

4. 버튼 클릭 후 결과 확인

---

# 참고

---

### 1. 정적 & 동적 props 주의사항

1. 첫 번째는 정적 props로 문자열로써의 "1"을 전달
2. 두 번째는 동적 props로 숫자로써의 1을 전달

```html
<!-- 1 -->
<SomeComponent num-props="1" />
<!-- 2 -->
<SomeComponent :num-props="1" />
```

### 2. Prop 선언을 객체 선언 문법으로 권장하는 이유

1. prop에 타입을 지정하는 것은 컴포넌트를 가독성이 좋게 문서화하는데 도움이 되며,
   다른 개발자가 잘못된 유형을 전달할 때에 브라우저 콘솔에 경고를 출력하도록 함
2. 추가로 prop에 대한 유효성 검사로써 활용 가능

- https://vuejs.org/guide/components/props.html#prop-vaildation

```javascript
defineProps({
    // 여러 타입 허용
    propB: [String, Number],

    // 문자열 필수
    propC: {
        type: String,
        required:true,
    }

    // 기본 값을 가지는 숫자형
    propD: {
        type: Number,
        default: 10
    }
});
```

### 3. emit 이벤트도 객체 선언 문법으로 작성 가능

- props 타입 유효성 검사와 유사하게 emit 이벤트 또한 객체 구문으로 선언된 경우 유효성 검사를 할 수 있음
- https://vuejs.org/guide/components/events.html#events-validation

```javascript
const emit = defineEmits({
  // 유효성 검사 없음
  click: null,

  // submit 이벤트 유효성 검사
  submit: ({ email, password }) => {
    if (email && password) {
      return true;
    } else {
      console.warn("submit 이벤트가 옳지 않음");
      return false;
    }
  },
});

const submitForm = function (email, password) {
  emit("submit", { email, password });
};
```

---
