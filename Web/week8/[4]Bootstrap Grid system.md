# Bootstrap Grid system

---

## INDEX

> **INDEX**
> 
> - Bootstrap Grid system
>     - 개요
>     - Grid system 클래스와 기본 구조
> - Grid system for responsive web
>     - 개요
>     - Grid system Breakpoints

---

## Bootstrap Grid system

> **개요**
> 
> - Bootstrap Grid system
>     - 웹 페이지의 **레이아웃을 조정**하는 데 사용 되는 **12개의 컬럼**으로 구성된 시스템
>     
> - Grid system 목적
>     - 반응형 디자인을 지원해 웹 페이지를 모바일, 태블릿, 데스크탑 등 다양한 기기에서 적절하게 표시할 수 있도록 도움
>     
> - 12개의 컬럼 사용 예시
>     - [https://news.google.com](https://news.google.com)
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled.png)
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%201.png)
>     

> **Grid system 클래스와 기본 구조**
> 
> - Grid sytem 기본 요소
>     1. Container : Column들을 담고 있는 공간
>     2. Column : 실제 컨텐츠를 포함하는 부분
>     3. Gutter : 컬럼과 컬럼 사이의 여백 영역
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%202.png)
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%203.png)
>     
>     - 1개의 row 안에 12칸의 column 영역이 구성
>     각 요소는 12칸 중 몇개를 차지할 것인지 지정됨
>         
>         `class="container"`
>         
>         `class="row"`
>         
>         `class="col-[num]"`
>         
>         ```html
>         <div class="container">
>         	<div class="row">
>         		<div class="col-4"></div>
>         		<div class="col-4"></div>
>         		<div class="col-4"></div>
>         	</div>
>         </div>
>         ```
>         
>         ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%204.png)
>         
>     
>     - Gutters
>         - Grid system에서 column 사이에 여백 영역
>         - x축은 padding, y축은 margin으로 여백 생성
> 
> - Grid System 실습
>     
>     ```html
>     <!DOCTYPE html>
>     <html lang="en">
>     
>     <head>
>       <meta charset="UTF-8">
>       <meta http-equiv="X-UA-Compatible" content="IE=edge">
>       <meta name="viewport" content="width=device-width, initial-scale=1.0">
>       <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet"
>         integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD" crossorigin="anonymous">
>       <style>
>         .box {
>           border: 1px solid black;
>           background-color: lightblue;
>           text-align: center;
>         }
>       </style>
>     </head>
>     
>     <body>
>       <h2 class="text-center">Basic</h2>
>       <div class="container">
>         <div class="row">
>           <div class="box col">col</div>
>           <div class="box col">col</div>
>           <div class="box col">col</div>
>         </div>
>         <div class="row">
>           <div class="box col-4">col-4</div>
>           <div class="box col-4">col-4</div>
>           <div class="box col-4">col-4</div>
>         </div>
>         <div class="row">
>           <div class="box col-2">col-2</div>
>           <div class="box col-8">col-8</div>
>           <div class="box col-2">col-2</div>
>         </div>
>       </div>
>     
>       <hr>
>     
>       <h2 class="text-center">Nesting</h2>
>       <div class="container">
>         <div class="row">
>           <div class="box col-4">col-4</div>
>           <div class="box col-8">
>             <div class="row">
>               <div class="box col-6">col-6</div>
>               <div class="box col-6">col-6</div>
>               <div class="box col-6">col-6</div>
>               <div class="box col-6">col-6</div>
>             </div>
>           </div>
>         </div>
>       </div>
>     
>       <hr>
>     
>       <h2 class="text-center">Offset</h2>
>       <div class="container">
>         <div class="row">
>           <div class="box col-4">col-4</div>
>           <div class="box col-4 offset-4">col-4 offset-4</div>
>         </div>
>         <div class="row">
>           <div class="box col-3 offset-3">col-3 offset-3</div>
>           <div class="box col-3 offset-3">col-3 offset-3</div>
>         </div>
>         <div class="row">
>           <div class="box col-6 offset-3">col-6 offset-3</div>
>         </div>
>       </div>
>     
>       <hr>
>     
>       <h2 class="text-center">Gutters(gx-0)</h2>
>       <div class="container">
>         <div class="row gx-0">
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>         </div>
>       </div>
>     
>       <br>
>     
>       <h2 class="text-center">Gutters(gy-5)</h2>
>       <div class="container">
>         <div class="row gy-5">
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>         </div>
>       </div>
>     
>       <br>
>     
>       <h2 class="text-center">Gutters(g-5)</h2>
>       <div class="container">
>         <div class="row g-5">
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>           <div class="col-6">
>             <div class="box">col</div>
>           </div>
>         </div>
>       </div>
>     
>       <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"
>         integrity="sha384-w76AqPfDkMBDXo30jS1Sgez6pr3x5MlQ1ZAGC+nuZB+EYdgRZgiwxhTBTkF7CXvN"
>         crossorigin="anonymous"></script>
>     </body>
>     
>     </html>
>     ```
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%205.png)
>     

---

## Grid system for responsive web

> **개요**
> 
> - Responsive Web Design
>     - 디바이스 종류나 화면 크기에 상관없이, 어디서든 일관된 레이아웃 및 사용자 경험을 제공하는 디자인 기술
>     - Bootstrap grid system에서는 **12개의 column**과 **6개 breakpoints**를 사용하여 반응형 웹 디자인을 구현

> **Grid system Breakpoints**
> 
> - Grid system breakpoints
>     - 웹 페이지를 다양한 화면 크기에서 적절하게 배치하기 위한 분기점
>     
>     → 화면 너비에 따라 6개의 분기점 제공`(xs, sm, md, lg, xl, xxl)`
>     
>     - 각 breakpoints 마다 설정된 최대 너비 값 “이상으로” 화면이 커지면 grid system 동작이 변경됨
>         
>         ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%206.png)
>         
>     
> - Breakpoints 실습
>     
>     ```html
>     <!DOCTYPE html>
>     <html lang="en">
>     
>     <head>
>       <meta charset="UTF-8">
>       <meta http-equiv="X-UA-Compatible" content="IE=edge">
>       <meta name="viewport" content="width=device-width, initial-scale=1.0">
>       <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet"
>         integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD" crossorigin="anonymous">
>       <style>
>         .box {
>           border: 1px solid black;
>           background-color: lightblue;
>           text-align: center;
>         }
>       </style>
>     </head>
>     
>     <body>
>       <h2 class="text-center">Breakpoints</h2>
>       <div class="container">
>         <div class="row">
>           <div class="box col-12 col-sm-6 col-md-2 col-lg-4">
>             col
>           </div>
>           <div class="box col-12 col-sm-6 col-md-8 col-lg-4">
>             col
>           </div>
>           <div class="box col-12 col-sm-6 col-md-2 col-lg-4">
>             col
>           </div>
>           <div class="box col-12 col-sm-6 col-md-12 col-lg-12">
>             col
>           </div>
>         </div>
>     
>         <hr>
>     
>         <h2 class="text-center">Breakpoints + offset</h2>
>         <div class="row g-4">
>           <div class="box col-12 col-sm-4 col-md-6">
>             col
>           </div>
>           <div class="box col-12 col-sm-4 col-md-6">
>             col
>           </div>
>           <div class="box col-12 col-sm-4 col-md-6">
>             col
>           </div>
>           <div class="box col-12 col-sm-4 offset-sm-4 col-md-6 offset-md-0">
>             col
>           </div>
>         </div>
>       </div>
>     
>       <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"
>         integrity="sha384-w76AqPfDkMBDXo30jS1Sgez6pr3x5MlQ1ZAGC+nuZB+EYdgRZgiwxhTBTkF7CXvN"
>         crossorigin="anonymous"></script>
>     </body>
>     
>     </html>
>     ```
>     
>     - xs
>         
>         ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%207.png)
>         
>     - sm
>         
>         ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%208.png)
>         
>     - md
>         
>         ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%209.png)
>         
>     - lg
>         
>         ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%2010.png)
>         
> 
> - Media Query로 작성된 Grid system의 breakpoints
>     
>     ```css
>     /* Small devices (landscape phones, 576px and up) */
>     @media (min-width: 576px){
>     	...
>     }
>     /* Medium devices (tablets, 768px and up) */
>     @media (min-width: 768px){
>     	...
>     }
>     /* Large devices (desktops, 992px and up) */
>     @media (min-width: 992px){
>     	...
>     }
>     /* X-Large devices (large desktops, 1200px and up) */
>     @media (min-width: 1200px){
>     	...
>     }
>     /* XX-Large devices (large desktops, 1400px and up) */
>     @media (min-width: 1400px){
>     	...
>     }
>     ```
>     
>     **Grid System은 화면 크기에 따라 12개의 칸을 각 요소에 나누어 주는 것**
>     

---

## CSS Layout 정리

> **CSS Layout 정리**
> 
> - 어떤 레이아웃 기술이 사용 되었는지 구성해보기
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%2011.png)
>     
>     - Grid System
>         
>         ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%2012.png)
>         
>     - Flexbox
>         
>         ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%2013.png)
>         
>     - Position
>         
>         ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%2014.png)
>         
>     
>     <aside>
>     💡 각각의 기술은 용도와 장단점이 있음
>     
>     각 기술은 독립적인 용도를 가지지 않으며,
>     어떤 기술이 적합한 도구가 될지는 특정 상황에 따라 다름
>     
>     이를 파악하기 위해서는 충분한 개발 경험이 필요
>     
>     </aside>
>     

---

## 참고

> **참고**
> 
> - The Grid System
>     - CSS가 아닌 편집 디자인에서 나온 개념으로
>     구성 요소를 잘 배치해서 시각적으로 좋은 결과물을 만들기 위함
>     - 기본적으로 안쪽에 있는 요소들의 오와 열을 맞추는 것에서 기인
>     - 정보 구조와 배열을 체계적으로 작성하여 정보의 질서를 부여하는 시스템
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%2015.png)
>     
> - Grid cards
>     - `row-cols` 클래스를 사용하여 행당 표시할 열(카드) 수를 손쉽게 제어할 수 있음
>     
>     ```html
>     <!DOCTYPE html>
>     <html lang="en">
>     
>     <head>
>       <meta charset="UTF-8">
>       <meta http-equiv="X-UA-Compatible" content="IE=edge">
>       <meta name="viewport" content="width=device-width, initial-scale=1.0">
>       <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet"
>         integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD" crossorigin="anonymous">
>     </head>
>     
>     <body>
>       <h2 class="text-center">Grid Cards</h2>
>       <div class="container">
>         <div class="row row-cols-1 row-cols-sm-3 row-cols-md-2 g-4">
>           <div class="col">
>             <div class="card">
>               <div class="card-body">
>                 <h5 class="card-title">Card title</h5>
>                 <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional
>                   content. This content is a little bit longer.</p>
>               </div>
>             </div>
>           </div>
>           <div class="col">
>             <div class="card">
>               <div class="card-body">
>                 <h5 class="card-title">Card title</h5>
>                 <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional
>                   content. This content is a little bit longer.</p>
>               </div>
>             </div>
>           </div>
>           <div class="col">
>             <div class="card">
>               <div class="card-body">
>                 <h5 class="card-title">Card title</h5>
>                 <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional
>                   content.</p>
>               </div>
>             </div>
>           </div>
>           <div class="col offset-sm-4 offset-md-0">
>             <div class="card">
>               <div class="card-body">
>                 <h5 class="card-title">Card title</h5>
>                 <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional
>                   content. This content is a little bit longer.</p>
>               </div>
>             </div>
>           </div>
>         </div>
>       </div>
>     
>       <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"
>         integrity="sha384-w76AqPfDkMBDXo30jS1Sgez6pr3x5MlQ1ZAGC+nuZB+EYdgRZgiwxhTBTkF7CXvN"
>         crossorigin="anonymous"></script>
>     </body>
>     
>     </html>
>     ```
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%2016.png)
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%2017.png)
>     
>     ![Untitled](Bootstrap%20Grid%20system%20405ed64bf76f4fdcb466ccb93028411f/Untitled%2018.png)
>     

---