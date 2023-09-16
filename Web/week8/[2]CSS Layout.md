# CSS Layout

---

## INDEX

> **INDEX**
> 
> - CSS Box Model
>     - 구성요소
>     - 박스 타입
>     - 기타 display 속성
> - CSS Layout Position
>     - CSS Position
> - CSS Layout Flexbox
>     - 구성 요소
>     - 레이아웃 구성

---

## CSS Box Model

> **CSS Box Model**
> 
> - **CSS Box Model**
>     - 모든 HTML 요소를 사각형 박스로 표현하는 개념
> 
> - 원이 아니라 네모 박스를 깎은 것
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled.png)
>     
> 
> - 박스 요소들로 구조화 된 웹 페이지
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%201.png)
>     

> **구성 요소**
> 
> - CSS Box Model
>     - 모든 HTML 요소를 사각형 박스로 표현하는 개념
>         
>         1.**내용(content)**, 2.**안쪽 여백(padding)**, 3.**테두리(border)**, 4.**외부간격(margin)**으로 구성되는 개념
>         
> 
> - Box 구성 요소
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%202.png)
>     
> 
> - Box 구성의 방향 별 명칭
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%203.png)
>     
> 
> - Box 구성 요소 예시
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html lang="en">
>         <head>
>             <meta charset="UTF-8">
>             <meta name="viewport" content="width=device-width, initial-scale=1.0">
>             <title>Document</title>
>             <style>
>                 .box1 {
>                     width: 200px;
>                     padding-left: 25px;
>                     padding-bottom: 25px;
>                     margin-left: 25px;
>                     margin-top: 50px;
>                     border-width: 3px;
>                     border-style: solid;
>                     border-color: black;
>                 }
>                 .box2 {
>                     width: 200px;
>                     padding: 25px 50px;
>                     margin: 25px auto;
>                     border: 1px dashed black;
>                 }
>             </style>
>         </head>
>         <body>
>             <div class="box1">box1</div>
>             <div class="box2">box2</div>
>         </body>
>         </html>
>         ```
>         
>     
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%204.png)
>         
>     
> - width & height 속성
>     - 요소의 너비와 높이를 지정
>     - 이때 지정되는 요소의 너비와 높이는 콘텐츠 영역을 대상으로 함
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%205.png)
>         
> 
> - CSS가 width 값을 계산하는 기준
>     - CSS는 border가 아닌 content의 크기를 width 값으로 지정
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%206.png)
>         
> 
> - box-sizing 속성
>     1. content-box
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%207.png)
>         
>     2. border-box
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%208.png)
>         
> 
> - box-sizing 예시
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html lang="en">
>         <head>
>             <meta charset="UTF-8">
>             <meta name="viewport" content="width=device-width, initial-scale=1.0">
>             <title>Document</title>
>             <style>
>                 .box{
>                     width: 100px;
>                     border: 2px solid black;
>                     padding: 10px;
>                     margin: 2px;
>                     background-color: lightgray;
>                 }
>                 .content-box{
>                     box-sizing: content-box;
>                 }
>                 .border-box{
>                     box-sizing: border-box;
>                 }
>             </style>
>         </head>
>         <body>
>             <div class = "box content-box">content-box</div>
>             <div class = "box border-box">border-box</div>
>         </body>
>         </html>
>         ```
>         
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%209.png)
>         

> **박스 타입**
> 
> - 박스 타입 : Block & Inline
>     - Block
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2010.png)
>         
>     - Inline
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2011.png)
>         
>     
> - Normal flow
>     - CSS를 적용하지 않았을 경우 웹페이지 요소가 기본적으로 배치되는 방향
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2012.png)
>         
> 
> - 박스 타입 예시
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html lang="en">
>         <head>
>             <meta charset="UTF-8">
>             <meta name="viewport" content="width=device-width, initial-scale=1.0">
>             <title>Document</title>
>             <style>
>                 a,
>                 span,
>                 img {
>                     border: 3px solid red;
>                 }
>                 h1,
>                 p,
>                 div{
>                     border: 1px solid blue;
>                 }
>             </style>
>         </head>
>         <body>
>             <h1>Normal flow</h1>
>             <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit.</p>
>             <div>
>                 <p>block 요소는 기본적으로 부모 요소의 너비 100%를 차지하며, 자식 콘텐츠의 최대 높이를 취한다.</p>
>                 <p>block 요소의 총 너비와 총 높이는 content + padding + border width/height다.</p>
>             </div>
>             <p>block 요소는 서로 margins로 구분된다.</p>
>             <p>inline 요소는 <span>이 것 처럼</span> 자체 콘텐츠의 너바와 높이만 차지한다.
>             그리고 inline 요소는 <a href="#">width나 height 속성을 지정할 수 없다.</a>
>             </p>
>             <p>
>                 물론 이미지도 <img src="₩"> 인라인 요소다.
>                 단, 이미지는 다른 inline 요소와 달리 width나 height로 크기를 조정할 수 있다.
>             </p>
>             <p>
>                 만약, inline 요소의 크기를 제어하려면 block 요소로 변경하거나 inline-block 요소로 설정해주어야 한다.
>             </p>
>         
>         </body>
>         </html>
>         ```
>         
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2013.png)
>         
>     
> - block 타입 특징
>     - 항상 새로운 행으로 나뉨
>     - width와 height 속성을 사용하여 너비와 높이를 지정할 수 있음
>     - 기본적으로 width 속성을 지정하지 않으면 박스는 inline 방향으로 사용가능한 공간을 모두 차지함.
>         
>         (너비를 사용가능한 공간의 100%로 채우는 것)
>         
>     - 대표적인 block 타입 태그
>         
>         `h1~6`, `p`, `div`
>         
> 
> - inline 타입 특징
>     - 새로운 행으로 나뉘지 않음
>     - width와 height 속성을 사용할 수 없음
>     - 수직방향
>         - padding, margins, borders가 적용되지만 다른 요소를 밀어낼 수는 없음
>     - 수평 방향
>         - padding, margin, borders가 적용되어 다른 요소를 밀어낼 수 있음
>     - 대표적인 inline 타입 태그
>         
>         `a`, `img`, `span`
>         
>     
> - 속성에 따른 수평 정렬
>     1. `margin-right: auto;` or `text-align: left;`
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2014.png)
>         
>     2. `margin-left: auto;` or `text-align: right;`
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2015.png)
>         
>     3. `margin-right: auto; margin-left: auto;` or `text-align: center;`
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2016.png)
>         

> **기타 display 속성**
> 
> - 기타 display 속성
>     1. inline-block
>     2. none
> 
> - inline-block
>     - inline과 block 요소 사이의 중간 지점을 제공하는 display 값
>     - block 요소의 특징을 가짐
>         - width 및 height 속성 사용 가능
>         - padding, margin 및  border 로 인해 다른 요소가 밀려남
>     - 요소가 **줄 바꿈 되는 것을 원하지 않**으면서 **너비와 높이를 적용**하고 싶은 경우에 사용
> 
> - inline-block 예시
>     - 코드
>     
>     ```html
>     <!DOCTYPE html>
>     <html lang="en">
>     
>     <head>
>       <meta charset="UTF-8">
>       <meta http-equiv="X-UA-Compatible" content="IE=edge">
>       <meta name="viewport" content="width=device-width, initial-scale=1.0">
>       <title>Document</title>
>       <style>
>         span {
>           margin: 20px;
>           padding: 20px;
>           width: 80px;
>           height: 50px;
>           background-color: lightblue;
>           border: 2px solid blue;
>           display: inline-block;
>         }
>     
>         ul>li {
>           background-color: crimson;
>           padding: 10px 20px;
>           display: inline-block;
>         }
>     
>         .container {
>           text-align: center;
>         }
>     
>         .box {
>           display: inline-block;
>           width: 100px;
>           height: 100px;
>           background-color: #4CAF50;
>           margin: 10px;
>         }
>       </style>
>     </head>
>     
>     <body>
>       <!-- 1. 이제 다른 요소를 밀어낼 수 있는 span -->
>       <p>Lorem ipsum dolor sit amet <span>consectetur</span> adipisicing elit. Animi iusto enim officia exercitationem
>         dolorque, quasi velit, dolores, tempora illum odio necessitatibus. Fugit,
>         cumque eligendi!</p>
>     
>       <!-- 2. 리스트 요소를 가로로 정렬 -->
>       <ul>
>         <li><a href="#">link</a></li>
>         <li><a href="#">link</a></li>
>         <li><a href="#">link</a></li>
>       </ul>
>     
>       <!-- 3. div 요소를 가로로 정렬 -->
>       <div class="container">
>         <div class="box"></div>
>         <div class="box"></div>
>         <div class="box"></div>
>       </div>
>     </body>
>     
>     </html>
>     ```
>     
>     - 화면
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2017.png)
>     
> - none
>     - 요소를 화면에 표시하지 않고, 공간조차 부여되지 않음
> 
> - none 예시
>     - 코드
>     
>     ```html
>     <!DOCTYPE html>
>     <html lang="en">
>     
>     <head>
>       <meta charset="UTF-8">
>       <meta name="viewport" content="width=device-width, initial-scale=1.0">
>       <title>Document</title>
>       <style>
>         .box {
>           width: 100px;
>           height: 100px;
>           background-color: red;
>           border: 2px solid black;
>         }
>     
>         .none {
>           display: none;
>         }
>       </style>
>     </head>
>     
>     <body>
>       <div class="box">1</div>
>       <div class="box none">2</div>
>       <div class="box">3</div>
>     </body>
>     
>     </html>
>     ```
>     
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2018.png)
>         

---

## CSS Layout Position

> **CSS Layout**
> 
> - CSS Layout
>     - 각 요소의 **위치**와 **크기를 조정**하여 웹 페이지의 디자인을 결정하는 것
>     - Display, Position, Float, Flexbox 등

> **CSS Position**
> 
> - CSS Position
>     - 요소를 Normal Flow에서 제거하여 다른 위치로 배치하는 것
>     - 다른 요소 위에 올리기, 화면의 특정 위치에 고정시키기 등
> 
> - Position 이동 방향
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2019.png)
>     
> 
> - Position 유형
>     1. static
>     2. relative
>     3. absolute
>     4. fixed
>     5. sticky
> 
> - Position 유형별 특징
>     1. static
>         - 기본 값
>         - 요소를 Normal Flow에 따라 배치
>         
>     2. relative
>         - 요소를 Normal Flow에 따라 배치
>         - 자기 자신을 기준으로 이동
>         - 요소가 차지하는 공간은 static일 때와 같음
>         
>     3. absolute
>         - 요소를 Normal Flow에서 제거
>         - 가장 가까운 relative 부모 요소를 기준으로 이동
>         - 문서에서 요소가 차지하는 공간이 없어짐
>     
>     1. fixed
>         - 요소를 Normal Flow에서 제거
>         - 현재 화면영역(view port)을 기준으로 이동
>         - 문서에서 요소가 차지하는 공간이 없어짐
>     
>     1. sticky
>         - 요소를 Normal Flow에 따라 배치
>         - 요소가 일반적인 문서 흐름에 따라 배치되다가 스크롤이 특정 임계점에 도달하면 그 위치에서 고정됨(fixed)
>         - 만약 다음 sticky 요소가 나오면 다음 sticky 요소가 이전 sticky요소의 자리를 대체
>             - 이전 sticky 요소가 고정되어 있던 위치와 다음 sticky 요소가 고정되어야 할 위치가 겹치게 되기 때문
> 
> - Position 예시
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html>
>         
>         <head>
>           <title>CSS Position</title>
>           <style>
>             * {
>               box-sizing: border-box;
>             }
>         
>             body {
>               height: 1500px;
>             }
>         
>             .container {
>               position: relative;
>               height: 300px;
>               width: 300px;
>               border: 1px solid black;
>             }
>         
>             .box {
>               height: 100px;
>               width: 100px;
>               border: 1px solid black;
>             }
>         
>             .static {
>               position: static;
>               background-color: lightcoral;
>             }
>         
>             .absolute {
>               position: absolute;
>               background-color: lightgreen;
>               top: 100px;
>               left: 100px;
>             }
>         
>             .relative {
>               position: relative;
>               background-color: lightblue;
>               top: 100px;
>               left: 100px;
>             }
>         
>             .fixed {
>               position: fixed;
>               background-color: gray;
>               top: 0;
>               right: 0;
>             }
>           </style>
>         </head>
>         
>         <body>
>           <div class="container">
>             <div class="box static">Static</div>
>             <div class="box absolute">Absolute</div>
>             <div class="box relative">Relative</div>
>             <div class="box fixed">Fixed</div>
>           </div>
>         </body>
>         
>         </html>
>         ```
>         
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2020.png)
>         
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html lang="en">
>         
>         <head>
>           <meta charset="UTF-8">
>           <meta http-equiv="X-UA-Compatible" content="IE=edge">
>           <meta name="viewport" content="width=device-width, initial-scale=1.0">
>           <title>Document</title>
>           <style>
>             body {
>               height: 1500px;
>             }
>         
>             .sticky {
>               position: sticky;
>               top: 0;
>               background-color: lightblue;
>               padding: 20px;
>               border: 2px solid black;
>             }
>           </style>
>         </head>
>         
>         <body>
>           <h1>Sticky positioning</h1>
>           <div>
>             <div class="sticky">첫 번째 Sticky</div>
>             <div>
>               <p>내용1</p>
>               <p>내용2</p>
>               <p>내용3</p>
>             </div>
>             <div class="sticky">두 번째 Sticky</div>
>             <div>
>               <p>내용4</p>
>               <p>내용5</p>
>               <p>내용6</p>
>             </div>
>             <div class="sticky">세 번째 Sticky</div>
>             <div>
>               <p>내용7</p>
>               <p>내용8</p>
>               <p>내용9</p>
>             </div>
>           </div>
>         </body>
>         
>         </html>
>         ```
>         
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2021.png)
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2022.png)
>         
>     
> - 실제 Position 사용 예시 - absolute
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2023.png)
>     
> - 실제 Position 사용 예시 - fixed
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2024.png)
>     
> 
> - 실제 Position 사용 예시 - sticky
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2025.png)
>     
> - absolute 예시
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2026.png)
>         
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html lang="en">
>         
>         <head>
>           <meta charset="UTF-8">
>           <meta name="viewport" content="width=device-width, initial-scale=1.0">
>           <title>Document</title>
>           <style>
>             .card {
>               width: 300px;
>               height: 200px;
>               border: 1px solid black;
>               position: relative;
>             }
>         
>             .card-content {
>               padding: 10px;
>             }
>         
>             .badge {
>               background-color: red;
>               color: white;
>               padding: 5px 10px;
>               position: absolute;
>               top: 0;
>               right: 0;
>             }
>           </style>
>         </head>
>         
>         <body>
>           <div class="card">
>             <div class="card-content">
>               <h3>Card Title</h3>
>               <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
>               <span class="badge">New</span>
>             </div>
>           </div>
>         </body>
>         
>         </html>
>         ```
>         
> 
> - z-index
>     - 요소가 겹쳤을 때 어떤 요소 순으로 위에 나타낼 지 결정
> 
> - z-index 특징
>     - 정수 값을 사용해 z축 순서를 지정
>     - 더 큰 값을 가진 요소가 작은 값의 요소를 덮음
> 
> - z-index 예시
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html lang="en">
>         
>         <head>
>           <meta charset="UTF-8">
>           <meta http-equiv="X-UA-Compatible" content="IE=edge">
>           <meta name="viewport" content="width=device-width, initial-scale=1.0">
>           <title>Document</title>
>           <style>
>             .container {
>               position: relative;
>             }
>         
>             .box {
>               position: absolute;
>               width: 100px;
>               height: 100px;
>             }
>         
>             .red {
>               background-color: red;
>               top: 50px;
>               left: 50px;
>               z-index: 3;
>             }
>         
>             .green {
>               background-color: green;
>               top: 100px;
>               left: 100px;
>               z-index: 2;
>             }
>         
>             .blue {
>               background-color: blue;
>               top: 150px;
>               left: 150px;
>               z-index: 1;
>             }
>           </style>
>         </head>
>         
>         <body>
>           <div class="container">
>             <div class="box red"></div>
>             <div class="box green"></div>
>             <div class="box blue"></div>
>           </div>
>         </body>
>         
>         </html>
>         ```
>         
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2027.png)
>         

---

## CSS Layout Flexbox

> **개요**
> 
> - CSS Flexbox
>     - 요소를 행과 열 형태로 배치하는 1차원 레이아웃 방식
>     - ‘공간 배열’ & ‘정렬’

> **구성 요소**
> 
> - 요소를 행과 열 형태로 배치하는 **1차원** 레이아웃 방식
> 
> - Flexbox 기본 사항
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2028.png)
>     
>     - main axis(주 축)
>         - flex item 들이 배치되는 기본 축
>         - main start에서 시작하여 main end 방향으로 배치
>     
>     - cross axis(교차 축)
>         - main axis에 수직인 축
>         - cross start에서 시작하여 cross end 방향으로 배치
>     
>     - Flex Container
>         - `display: flex;` 혹은 `display: inline-flex;` 가 설정된 부모 요소
>         - 이 컨테이너의 1차 자식 요소들이 Flex item이 됨
>         - flexbox 속성 값들을 사용하여 자식 요소 Flex Item들을 배치
>     
>     - Flex Item
>         - Flex Container 내부에 레이아웃 되는 항목

> **Flexbox 속성**
> 
> - Flex Container 관련 속성
>     - `display`
>     - `flex-direction`
>     - `flex-wrap`
>     - `justify-content`
>     - `align-items`
>     - `align-content`
> - Flex Item 관련 속성
>     - `align-self`
>     - `flex-grow`
>     - `flex-basis`
>     - `order`
> 
> - 목적에 따른 분류
>     - 배치
>         - `flex-direction`
>         - `flex-wrap`
>     - 공간 분배
>         - `justify-content`
>         - `align-content`
>     - 정렬
>         - `align-items`
>         - `align-self`
> 
> - 속성 명 Tip
>     - `justify` - 주축
>     - `align` - 교차 축

> **레이아웃 구성**
> 
> 1. Flex Container 지정
>     - flex item은 기본적으로 행으로 나열
>     - flex item은 주축의 시작 선에서 시작
>     - flex item은 교차죽의 크기를 채우기 위해 늘어남
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2029.png)
>         
>     
> 2. flex-direction 지정
>     - flex item이 나열되는 방향을 지정
>     - column으로 지정할 경우 주 축이 변경됨
>     - -reverse로 지정하면 시작 선과 끝 선이 서로 바뀜
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2030.png)
>         
>     
> 3. flex-wrap
>     - flex item 목록이 flex container의 하나의 행에 들어가지 않을 경우 다른 행에 배치할 지 여부 설정
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2031.png)
>         
> 
> 1. justify-content
>     - 주 축을 따라 flex item과 주위에 공간을 분배
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2032.png)
>         
> 2. align-content
>     - 교차 축을 따라 flex item과 주위에 공간을 분배
>         - flex-wrap이 wrap 또는 wrap-reverse로 설정된 여러 행에만 적용됨
>         - 한 줄 짜리 행에는(flex-wrap이 nowrap으로 설정된 경우) 효가 없음
>             
>             ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2033.png)
>             
> 
> 1. align-items
>     - 교차 축을 따라 flex item 행을 정렬
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2034.png)
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2035.png)
>         
> 
> 1. align-self
>     - 교차 축을 따라 개별 flex item을 정렬
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2036.png)
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2037.png)
>         
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html lang="en">
>         
>         <head>
>           <meta charset="UTF-8">
>           <meta http-equiv="X-UA-Compatible" content="IE=edge">
>           <meta name="viewport" content="width=device-width, initial-scale=1.0">
>           <title>Document</title>
>           <style>
>             .container {
>               height: 500px;
>               border: 1px solid black;
>               display: flex;
>               /* flex-direction: row; */
>               /* flex-direction: column; */
>               /* flex-direction: row-reverse; */
>               /* flex-direction: column-reverse; */
>         
>               /* flex-wrap: nowrap; */
>               /* flex-wrap: wrap; */
>         
>               /* justify-content: flex-start; */
>               /* justify-content: center; */
>               /* justify-content: flex-end; */
>         
>               /* align-content: flex-start; */
>               /* align-content: center; */
>               /* align-content: flex-end; */
>         
>               /* align-items: flex-start; */
>               /* align-items: center; */
>               /* align-items: flex-end; */
>             }
>         
>             .post {
>               background-color: grey;
>               border: 1px solid black;
>               margin: 0.5rem;
>               padding: 0.5rem;
>             }
>         
>             .item1 {
>               /* align-self: center; */
>             }
>         
>             .item2 {
>               /* align-self: flex-end; */
>             }
>           </style>
>         </head>
>         
>         <body>
>           <div class="container">
>             <div class="post item1">
>               <h2>Post Title 1</h2>
>               <p>Post Content 1</p>
>             </div>
>             <div class="post item2">
>               <h2>Post Title 2</h2>
>               <p>Post Content 2</p>
>             </div>
>             <div class="post item3">
>               <h2>Post Title 3</h2>
>               <p>Post Content 3</p>
>             </div>
>             <div class="post item4">
>               <h2>Post Title 4</h2>
>               <p>Post Content 4</p>
>             </div>
>           </div>
>         
>         </body>
>         
>         </html>
>         ```
>         
> 
> 1. flex-grow
>     - 남는 행 여백을 비율에 따라 각 flex item에 분배
>         - 아이템이 컨테이너 내에서 확장하는 비율을 지정
>     - flex-grow의 반대는 flex-shrink
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html lang="en">
>         
>         <head>
>           <meta charset="UTF-8">
>           <meta http-equiv="X-UA-Compatible" content="IE=edge">
>           <meta name="viewport" content="width=device-width, initial-scale=1.0">
>           <title>Document</title>
>           <style>
>             .container {
>               display: flex;
>               width: 100%;
>             }
>         
>             .item {
>               height: 100px;
>               color: white;
>               font-size: 3rem;
>             }
>         
>             .item-1 {
>               background-color: red;
>               flex-grow: 1;
>             }
>         
>             .item-2 {
>               background-color: green;
>               flex-grow: 2;
>             }
>         
>             .item-3 {
>               background-color: blue;
>               flex-grow: 3;
>             }
>         
>           </style>
>         </head>
>         
>         <body>
>           <div class="container">
>             <div class="item item-1">1</div>
>             <div class="item item-2">2</div>
>             <div class="item item-3">3</div>
>           </div>
>         </body>
>         
>         </html>
>         ```
>         
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2038.png)
>         
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2039.png)
>     
> 
> 1. flex-basis
>     - flex item의 초기 크기 값을 지정
>     - flex-basis와 width 값을 동시에 적용한 경우 flex-basis가 우선
>         - 코드
>             
>             ```html
>             <!DOCTYPE html>
>             <html lang="en">
>             
>             <head>
>               <meta charset="UTF-8">
>               <meta http-equiv="X-UA-Compatible" content="IE=edge">
>               <meta name="viewport" content="width=device-width, initial-scale=1.0">
>               <title>Document</title>
>               <style>
>                 .container {
>                   display: flex;
>                   width: 100%;
>                 }
>             
>                 .item {
>                   height: 100px;
>                   color: white;
>                   font-size: 3rem;
>                 }
>             
>                 .item-1 {
>                   background-color: red;
>                   flex-basis: 300px;
>                 }
>             
>                 .item-2 {
>                   background-color: green;
>                   flex-basis: 600px;
>                 }
>             
>                 .item-3 {
>                   background-color: blue;
>                   flex-basis: 300px;
>                 }
>             
>               </style>
>             </head>
>             
>             <body>
>               <div class="container">
>                 <div class="item item-1">1</div>
>                 <div class="item item-2">2</div>
>                 <div class="item item-3">3</div>
>               </div>
>             </body>
>             
>             </html>
>             ```
>             
>         - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2040.png)
>         

> **flex-wrap 응용**
> 
> - 반응형 레이아웃
>     - 다양한 디바이스와 화면 크기에 자동으로 적응하여 콘텐츠를 최적으로 표시하는 웹 레이아웃 방식
> 
> - 반응형 레이아웃 작성
>     - flex-wrap을 사용해 반응형 레이아웃 작성(feat. flex-grow & flex-basis)
>     - 코드
>         
>         ```html
>         <!DOCTYPE html>
>         <html lang="en">
>         
>         <head>
>           <meta charset="UTF-8">
>           <meta http-equiv="X-UA-Compatible" content="IE=edge">
>           <meta name="viewport" content="width=device-width, initial-scale=1.0">
>           <title>Document</title>
>           <style>
>             .card {
>               width: 80%;
>               border: 1px solid black;
>               /* 1 */
>               display: flex;
>               /* 2 */
>               flex-wrap: wrap;
>             }
>         
>             img {
>               width: 100%;
>             }
>         
>             .thumbnail {
>               /* 3 */
>               flex-basis: 700px;
>               /* 4 */
>               flex-grow: 1;
>               /* flex: 1 700px; */
>             }
>         
>             .content {
>               /* 3 */
>               flex-basis: 350px;
>               /* 4 */
>               flex-grow: 1;
>               /* flex: 1 350px; */
>             }
>         
>           </style>
>         </head>
>         
>         <body>
>           <div class="card">
>             <img class="thumbnail" src="images/sample.jpg" alt="sample">
>             <div class="content">
>               <h2>Heading</h2>
>               <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Perspiciatis minus sed expedita ut nihil tempora
>                 neque autem odio eos, repudiandae blanditiis, molestiae consequatur. Adipisci illo dolor repellat alias
>                 maiores.
>                 Aut?</p>
>             </div>
>           </div>
>         </body>
>         
>         </html>
>         ```
>         
>     - 화면
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2041.png)
>         

---

### 정리

> **flex-direction**
> 
> 
> ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2042.png)
> 

> **flex-wrap**
> 
> 
> ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2043.png)
> 

> **justify-content**
> 
> 
> ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2044.png)
> 

> **align-content**
> 
> 
> ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2045.png)
> 

> **align-items**
> 
> 
> ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2046.png)
> 

> **align-self**
> 
> 
> ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2047.png)
> 

---

## 참고

> **참고**
> 
> - shorthand 속성
>     - ‘border’
>         - border-width, border-style, border-color를 한번에 설정하기 위한 속성
>         
>         ```css
>         /* 작성 순서는 영향을 주지 않음 */
>         border: 2px solid black;
>         ```
>         
>     
>     - ‘margin’ & ‘padding’
>         - 4방향의 속성을 각각 지정하지 않고 한번에 지정할 수 있는 속성
>         
>         ```css
>         /* 4개 - 상우하좌*/
>         margin: 10px 20px 30px 40px;
>         padding: 10px 20px 30px 40px;
>         
>         /* 3개 - 상/좌우/하 */
>         margin: 10px 20px 30px;
>         padding: 10px 20px 30px;
>         
>         /* 2개 - 상하/좌우 */
>         margin: 10px 20px;
>         padding: 10px 20px;
>         
>         /* 1개 - 공통 */
>         margin: 10px;
>         padding: 10px;
>         ```
>         
>     - “flex-flow”
>         
>         ```css
>         .container{
>         	flex-flow: flex-direction flex-wrap;
>         }
>         ```
>         
>     
>     - “flex”
>         
>         ```css
>         /* One value, unitless number: flex-grow */
>         flex: 2;
>         
>         /* One value, length or percentage: flex-basis */
>         flex: 10rem;
>         flex: 30%;
>         
>         /* Two values: flex-grow | flex-basis */
>         flex: 1 30px;
>         
>         /* Two values: flex-grow | flex-shrink */
>         flex: 2 2;
>         
>         /* Three values: flex-grow | flex-shrink | flex-basis */
>         flex: 2 2 10%;
>         ```
>         
>     
> - Margin collapsing(마진 상쇄)
>     - 두 block 타입 요소의 margin top과 bottom이 만나 더 큰 margin으로 결합되는 현상
>     - 웹 개발자가 레이아웃을 더욱 쉽게 관리할 수 있도록 함
>         - 각 요소에 대한 상/하 margin을 각각 설정하지 않고 한 요소에 대해서만 설정하기 위함
>     
>     ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2048.png)
>     
>     - 예시
>         - 두 요소 모두 margin 20px이지만 실제 두 요소의 상/하 거리는 40이 아닌 20으로 상쇄
>         
>         ![Untitled](CSS%20Layout%200a2d3d36adae43b6aea00150d3d06912/Untitled%2049.png)
>         
> - Position의 역할
>     - 전체 페이지에 대한 레이아웃을 구성하는 것이 아닌
>     페이지의 특정 항목의 위치를 조정하는 것에 관한 것
>     
> - justify-items 및 justify-self 속성이 없는 이유
>     - “필요 없음”
>     margin auto를 통해 정렬 및 배치가 가능

---