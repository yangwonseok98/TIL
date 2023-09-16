# Fundamentals of Bootstrap

---

## INDEX

> **INDEX**
> 
> - Bootstrap
>     - 개요
>     - Typography
>     - Colors
>     - Component
> - Semantic Web
>     - 개요
>     - Semantic in HTML
>     - Semantic in CSS

---

## Bootstrap

> **개요**
> 
> - Bootstrap
>     - CSS 프론트엔드 프레임워크(Toolkit)
>         - 미리 만들어진 다양한 디자인 요소들을 제공하여
>         웹 사이트를 빠르고 쉽게 개발할 수 있도록 함
> 
> - The world most popular front-end open source
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled.png)
>     
> 
> - Bootstrap 사용해보기
>     1. Bootstrap 공식 문서
>         - https://getbootstrap.com/
>     2. Docs → Introduction → Quick start
>     3. 2번 “Include Bootstrap’s CSS and JS” 코드 확인 및 가져오기
>         - https://getbootstrap.com/docs/5.3/getting-started/introduction/#quick-start
>         - head와 body에 bootstrap CDN이 포함된 코드 블록
>     
>     ```python
>     <!doctype html>
>     <html lang="en">
>       <head>
>         <meta charset="utf-8">
>         <meta name="viewport" content="width=device-width, initial-scale=1">
>         <title>Bootstrap demo</title>
>         <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-4bw+/aepP/YC94hEpVNVgiZdgIC5+VKNBQNGCHeKRQN+PtmoHDEXuppvnDJzQIu9" crossorigin="anonymous">
>       </head>
>       <body>
>         <h1>Hello, world!</h1>
>         <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-HwwvtgBNo3bZJJLYd8oVXjrBZt8cqVSpeBNS5n7C8IVInixGAoxmnlMuBnhbgrkm" crossorigin="anonymous"></script>
>       </body>
>     </html>
>     ```
>     
> - Bootstrap 기본 사용법
>     
>     `<p class=”mt-5”>Hello, world!</p>`
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%201.png)
>     
> - Bootstrap에서 클래스 이름으로 Spacing을 표현하는 방법
>     - Property
>         
>         
>         | m | margin |
>         | --- | --- |
>         | p | padding |
>     - Sides
>         
>         
>         | t | top |
>         | --- | --- |
>         | b | bottom |
>         | s | left |
>         | e | right |
>         | y | top, bottom |
>         | x | left, right |
>         | blank | 4 sides |
>     - Size
>         
>         
>         | 0 | 0 rem | 0px |
>         | --- | --- | --- |
>         | 1 | 0.25 rem | 4px |
>         | 2 | 0.5 rem | 8px |
>         | 3 | 1 rem | 16px |
>         | 4 | 1.5 rem | 24px |
>         | 5 | 3 rem | 48px |
>         | auto | auto | auto |
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%202.png)
>     
> 
> **Bootstrap에는 특정한 규칙이 있는 클래스 이름으로 이미 스타일 및 레이아웃이 작성되어 있음**
> 

> **Typography**
> 
> - Typography
>     - 제목, 본문 텍스트, 목록 등
> 
> - Display headings
>     - 기존 Heading보다 더 눈에 띄는 제목이 필요할 경우(더 크고 약간 다른 스타일)
>         
>         ```html
>         <!-- display heading -->
>           <h1 class="display-1">Display 1</h1>
>           <h1 class="display-2">Display 2</h1>
>           <h1 class="display-3">Display 3</h1>
>           <h1 class="display-4">Display 4</h1>
>           <h1 class="display-5">Display 5</h1>
>           <h1 class="display-6">Display 6</h1>
>         ```
>         
>         ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%203.png)
>         
> 
> - Inline text elements
>     - HTML inline 요소에 대한 스타일
>         
>         ```html
>         <!-- inline text element -->
>           <p>You can use the mark tag to <mark>highlight</mark> text.</p>
>           <p><del>This line of text is meant to be treated as deleted text.</del></p>
>           <p><s>This line of text is meant to be treated as no longer accurate.</s></p>
>           <p><ins>This line of text is meant to be treated as an addition to the document.</ins></p>
>           <p><u>This line of text will render as underlined.</u></p>
>           <p><small>This line of text is meant to be treated as fine print.</small></p>
>           <p><strong>This line rendered as bold text.</strong></p>
>           <p><em>This line rendered as italicized text.</em></p>
>         ```
>         
>         ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%204.png)
>         
>         1. Hightlight
>             - `<mark></mark>`
>         2. 취소선
>             - `<del></del>`
>             - `<s></s>`
>         3. 밑줄
>             - `<ins></ins>`
>             - `<u></u>`
>         4. 작게
>             - `<small></small>`
>         5. 진하게
>             - `<strong></strong>`
>         6. 기울이기(강조)
>             - `<em></em>`
>         
> - Lists
>     - HTML list 요소에 대한 스타일
>         
>         ```html
>         <!-- list -->
>           <ul class="list-unstyled">
>             <li>This is a list.</li>
>             <li>It appears completely unstyled.</li>
>             <li>Structurally, it's still a list.</li>
>             <li>However, this style only applies to immediate child elements.</li>
>             <li>Nested lists:
>               <ul>
>                 <li>are unaffected by this style</li>
>                 <li>will still show a bullet</li>
>                 <li>and have appropriate left margin</li>
>               </ul>
>             </li>
>             <li>This may still come in handy in some situations.</li>
>           </ul>
>         ```
>         
>         ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%205.png)
>         

> **Colors**
> 
> - Bootstrap Color system
>     - Bootstrap이 지정하고 제공하는 색상 시스템
> 
> - Colors
>     - Text, Border, Background 및 다양한 요소에 사용하는 Bootstrap의 색상 키워드
>         
>         ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%206.png)
>         
>         ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%207.png)
>         
> - Text colors
>     
>     ```html
>     <!-- text colors -->
>       <p class="text-primary">.text-primary</p>
>       <p class="text-primary-emphasis">.text-primary-emphasis</p>
>       <p class="text-secondary">.text-secondary</p>
>       <p class="text-secondary-emphasis">.text-secondary-emphasis</p>
>       <p class="text-success">.text-success</p>
>       <p class="text-success-emphasis">.text-success-emphasis</p>
>       <p class="text-danger">.text-danger</p>
>       <p class="text-danger-emphasis">.text-danger-emphasis</p>
>       <p class="text-warning bg-dark">.text-warning</p>
>       <p class="text-warning-emphasis">.text-warning-emphasis</p>
>       <p class="text-info bg-dark">.text-info</p>
>       <p class="text-info-emphasis">.text-info-emphasis</p>
>       <p class="text-light bg-dark">.text-light</p>
>       <p class="text-light-emphasis">.text-light-emphasis</p>
>       <p class="text-dark bg-white">.text-dark</p>
>       <p class="text-dark-emphasis">.text-dark-emphasis</p>
>     ```
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%208.png)
>     
> - Background colors
>     
>     ```html
>     <!-- background colors -->
>       <div class="p-3 mb-2 bg-primary text-white">.bg-primary</div>
>       <div class="p-3 mb-2 bg-primary-subtle text-emphasis-primary">.bg-primary-subtle</div>
>       <div class="p-3 mb-2 bg-secondary text-white">.bg-secondary</div>
>       <div class="p-3 mb-2 bg-secondary-subtle text-emphasis-secondary">.bg-secondary-subtle</div>
>       <div class="p-3 mb-2 bg-success text-white">.bg-success</div>
>       <div class="p-3 mb-2 bg-success-subtle text-emphasis-success">.bg-success-subtle</div>
>       <div class="p-3 mb-2 bg-danger text-white">.bg-danger</div>
>       <div class="p-3 mb-2 bg-danger-subtle text-emphasis-danger">.bg-danger-subtle</div>
>       <div class="p-3 mb-2 bg-warning text-dark">.bg-warning</div>
>       <div class="p-3 mb-2 bg-warning-subtle text-emphasis-warning">.bg-warning-subtle</div>
>       <div class="p-3 mb-2 bg-info text-dark">.bg-info</div>
>       <div class="p-3 mb-2 bg-info-subtle text-emphasis-info">.bg-info-subtle</div>
>       <div class="p-3 mb-2 bg-light text-dark">.bg-light</div>
>       <div class="p-3 mb-2 bg-light-subtle text-emphasis-light">.bg-light-subtle</div>
>       <div class="p-3 mb-2 bg-dark text-white">.bg-dark</div>
>       <div class="p-3 mb-2 bg-dark-subtle text-emphasis-dark">.bg-dark-subtle</div>
>     ```
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%209.png)
>     
> - Bootstrap 실습
>     - 너비와 높이가 각각 200px인 정사각형 작성하기
>     (너비와 높이를 제외한 스타일은 모두 bootstrap으로 작성하기)
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
>       <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/css/bootstrap.min.css" rel="stylesheet"
>         integrity="sha384-4bw+/aepP/YC94hEpVNVgiZdgIC5+VKNBQNGCHeKRQN+PtmoHDEXuppvnDJzQIu9" crossorigin="anonymous">
>       <style>
>         .box {
>           width: 200px;
>           height: 200px;
>         }
>       </style>
>     </head>
>     
>     <body>
>       <div class="box border border-dark bg-info m-3"></div>
>     
>       <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/js/bootstrap.bundle.min.js"
>         integrity="sha384-HwwvtgBNo3bZJJLYd8oVXjrBZt8cqVSpeBNS5n7C8IVInixGAoxmnlMuBnhbgrkm"
>         crossorigin="anonymous"></script>
>     </body>
>     
>     </html>
>     ```
>     

> **Component**
> 
> - Bootstrap Component
>     - Bootstrap에서 제공하는 **UI 관련 요소**
>     
>     **UI 관련 요소**
>     
>     **→ 버튼, 네비게이션 바, 카드, 폼, 드롭다운 등**
>     
> - 대표 Component 사용해보기
>     - Alerts
>     - Badges
>     - Buttons
>     - Cards
>     - Navbar
>     
>     ```html
>     <!DOCTYPE html>
>     <html lang="en">
>     
>     <head>
>       <meta charset="UTF-8">
>       <meta name="viewport" content="width=device-width, initial-scale=1.0">
>       <title>Document</title>
>       <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/css/bootstrap.min.css" rel="stylesheet"
>       integrity="sha384-4bw+/aepP/YC94hEpVNVgiZdgIC5+VKNBQNGCHeKRQN+PtmoHDEXuppvnDJzQIu9" crossorigin="anonymous">
>     
>     </head>
>     
>     <body>
>       <!-- navbar -->
>       <nav class="navbar navbar-expand-lg bg-body-tertiary" data-bs-theme="dark">
>         <div class="container-fluid">
>           <a class="navbar-brand" href="#">Navbar</a>
>           <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
>             <span class="navbar-toggler-icon"></span>
>           </button>
>           <div class="collapse navbar-collapse" id="navbarSupportedContent">
>             <ul class="navbar-nav me-auto mb-2 mb-lg-0">
>               <li class="nav-item">
>                 <a class="nav-link active" aria-current="page" href="#">Home</a>
>               </li>
>               <li class="nav-item">
>                 <a class="nav-link" href="#">Link</a>
>               </li>
>               <li class="nav-item dropdown">
>                 <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
>                   Dropdown
>                 </a>
>                 <ul class="dropdown-menu">
>                   <li><a class="dropdown-item" href="#">Action</a></li>
>                   <li><a class="dropdown-item" href="#">Another action</a></li>
>                   <li><hr class="dropdown-divider"></li>
>                   <li><a class="dropdown-item" href="#">Something else here</a></li>
>                 </ul>
>               </li>
>               <li class="nav-item">
>                 <a class="nav-link disabled" aria-disabled="true">Disabled</a>
>               </li>
>             </ul>
>             <form class="d-flex" role="search">
>               <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
>               <button class="btn btn-outline-success" type="submit">Search</button>
>             </form>
>           </div>
>         </div>
>       </nav>
>       <div class="alert alert-primary" role="alert">
>         A simple primary alert—check it out!
>       </div>
>       <div class="alert alert-secondary" role="alert">
>         A simple secondary alert—check it out!
>       </div>
>       <div class="alert alert-success" role="alert">
>         A simple success alert—check it out!
>       </div>
>       <div class="alert alert-danger" role="alert">
>         A simple danger alert—check it out!
>       </div>
>       <div class="alert alert-warning" role="alert">
>         A simple warning alert—check it out!
>       </div>
>       <div class="alert alert-info" role="alert">
>         A simple info alert—check it out!
>       </div>
>       <div class="alert alert-light" role="alert">
>         A simple light alert—check it out!
>       </div>
>       <div class="alert alert-dark" role="alert">
>         A simple dark alert—check it out!
>       </div>
>     
>       <!-- badge -->
>       <span class="badge text-bg-primary">Primary</span>
>       <span class="badge text-bg-secondary">Secondary</span>
>       <span class="badge text-bg-success">Success</span>
>       <span class="badge text-bg-danger">Danger</span>
>       <span class="badge text-bg-warning">Warning</span>
>       <span class="badge text-bg-info">Info</span>
>       <span class="badge text-bg-light">Light</span>
>       <span class="badge text-bg-dark">Dark</span>
>     
>       <!-- buttons -->
>       <button type="button" class="btn btn-primary">Primary</button>
>       <button type="button" class="btn btn-secondary">Secondary</button>
>       <button type="button" class="btn btn-success">Success</button>
>       <button type="button" class="btn btn-danger">Danger</button>
>     
>       <!-- card -->
>       <div class="card" style="width: 18rem;">
>         <img src="..." class="card-img-top" alt="...">
>         <div class="card-body">
>           <h5 class="card-title">Card title</h5>
>           <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
>           <a href="#" class="btn btn-primary">Go somewhere</a>
>         </div>
>       </div>
>     
>       <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/js/bootstrap.bundle.min.js"
>         integrity="sha384-HwwvtgBNo3bZJJLYd8oVXjrBZt8cqVSpeBNS5n7C8IVInixGAoxmnlMuBnhbgrkm"
>         crossorigin="anonymous"></script>
>     </body>
>     
>     </html>
>     ```
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%2010.png)
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%2011.png)
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%2012.png)
>     
> - Component 이점
>     - 일관된 디자인을 제공하여
>     웹 사이트의 구성 요소를 구축하는 데 유용하게 활용

---

## Semantic Web

> **개요**
> 
> - Semantic Web
>     - 웹 데이터를 의미론적으로 구조화된 형태로 표현하는 방식
>     
>     “이 요소가 시각적으로 어떻게 보여 질까?” → **“ 이 요소가 가진 목적과 역할은 무엇일까?”** 
>     

> **Semantic in HTML**
> 
> - “문서의 최상위 제목”
>     - 단순히 최상위 제목**”처럼”** 보이게 출력하는 것
>         
>         ```html
>         <span style="font-size: 30px;">Heading</span>
>         ```
>         
>     
>     - 페이지 최상위 제목 의미를 제공하는 semantic 요소 h1
>         - 브라우저에 의해 제목처럼 보이도록 스타일이 지정됨
>         
>         ```html
>         <h1>Heading</h1>
>         ```
>         
>     
> - HTML Semantic Element
>     - 기본적인 모양과 기능 이외에 의미를 가지는 HTML 요소
>     
>     → 검색엔진 및 개발자가 웹 페이지 콘텐츠를 이해하기 쉽도록
>     
> - Semantic element
>     - header
>     - nav
>     - main
>     - article
>     - section
>     - aside
>     - footer
>     
> - Semantic element 예시
>     
>     ```html
>     <body>
>       <header>
>         <h1>Header</h1>
>       </header>
>     
>       <nav>
>         <ul>
>           <li><a href="#">Home</a></li>
>           <li><a href="#">About Us</a></li>
>           <li><a href="#">Contact</a></li>
>         </ul>
>       </nav>
>     
>       <main>
>         <article>
>           <h2>Article Title</h2>
>           <p>Article content goes here...</p>
>         </article>
>         <aside>
>           <h3>Aside</h3>
>           <ol>
>             <li><a href="#">Lorem, ipsum.</a></li>
>             <li><a href="#">Lorem, ipsum.</a></li>
>             <li><a href="#">Lorem, ipsum.</a></li>
>           </ol>
>         </aside>
>       </main>
>     
>       <footer>
>         <p>&copy; All rights reserved.</p>
>       </footer>
>     
>     </body>
>     ```
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%2013.png)
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%2014.png)
>     

> **Semantic in CSS**
> 
> - OOCSS [Object Oriented CSS]
>     - 객체 지향적 접근법을 적용하여 CSS를 구성하는 방법론
>     
> - CSS 방법론
>     - CSS를 효율적이고 유지 보수가 용이하게 작성하기 위한 일련의 가이드라인
>     
> - OOCSS 기본 원칙
>     1. 구조와 스킨을 분리
>     2. 컨테이너와 콘텐츠를 분리
> 
> - 구조와 스킨을 분리
>     - 구조와 스킨을 분리함으로써 재사용 가능성을 높임
>     - 모든 버튼의 **공통** 구조를 정의 + **각각**의 스킨(배경색과 폰트 색상)을 정의
>         
>         ```css
>         /* bad */
>         .blue-button{
>         	border : none;
>         	font-size : 1em;
>         	padding : 10px 20px;
>         	background-color: blue;
>         	color: white;
>         }
>         ```
>         
>         ```css
>         /* good */
>         .button {
>         	border: none;
>         	font-size: 1em;
>         	padding: 10px 20px;
>         }
>         
>         .button-blue{
>         	background-color: blue;
>         	color: white;
>         }
>         
>         .button-red{
>         	background-color: red;
>         	color: white;
>         }
>         ```
>         
> 
> - 컨테이너와 콘텐츠 분리
>     - 객체에 직접 적용하는 대신 객체를 둘러싸는 컨테이너에 스타일을 적용
>     - 스타일을 정의할 때 위치에 의존적인 스타일을 사용하지 않도록 함
>     - 콘텐츠를 다른 컨테이너로 이동 시키거나 재 배치할 때 스타일이 깨지는 것을 방지
>     - 예시
>         - .header 와 .footer 클래스가 폰트 크기와 색 둘다 영향을 줌.
>             - .container .title 이 폰트 크기 담당(콘텐츠 스타일)
>             - .header와 .footer가 폰트 크기 담당(컨테이너 스타일)
>         
>         ```css
>         /* bad */
>         .header h2{
>         	font-size: 24px;
>         	color: white;
>         }
>         
>         .footer h2{
>         	font-size: 24px;
>         	color: black;
>         }
>         ```
>         
>         ```css
>         /* good */
>         .container .title{
>         	font-size: 24px;
>         }
>         
>         .header{
>         	color: white;
>         }
>         
>         .footer{
>         	color: black;
>         }
>         ```
>         
>     
> - OOCSS 예시
>     
>     ```css
>     <!DOCTYPE html>
>     <html lang="en">
>     
>     <head>
>       <meta charset="UTF-8">
>       <meta http-equiv="X-UA-Compatible" content="IE=edge">
>       <meta name="viewport" content="width=device-width, initial-scale=1.0">
>       <title>Document</title>
>       <style>
>         /* 기본 Card 구조 */
>         .card {
>           border: 1px solid #ccc;
>           border-radius: 4px;
>           padding: 16px;
>           width: 50%;
>         }
>     
>         /* Card 제목 */
>         .card-title {
>           font-size: 20px;
>           font-weight: bold;
>           margin-bottom: 8px;
>         }
>     
>         /* Card 설명 */
>         .card-description {
>           font-size: 16px;
>           margin-bottom: 16px;
>         }
>     
>         /* 기본 버튼 구조 */
>         .btn {
>           display: inline-block;
>           border-radius: 4px;
>           padding: 8px 16px;
>           font-size: 1rem;
>           font-weight: 400;
>           color: #212529;
>           text-align: center;
>           text-decoration: none;
>           cursor: pointer;
>         }
>     
>         /* 파란 배경 버튼 */
>         .btn-blue {
>           background-color: #007bff;
>           color: #fff;
>         }
>     
>         /* 빨간 배경 버튼 */
>         .btn-red {
>           background-color: #cb2323;
>           color: #fff;
>         }
>       </style>
>     </head>
>     
>     <body>
>       <div class="card">
>         <p class="card-title">Card Title</p>
>         <p class="card-description">This is a card description.</p>
>         <button class="btn btn-blue">Learn More</button>
>         <button class="btn btn-red">Learn More</button>
>       </div>
>     </body>
>     
>     </html>
>     ```
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%2015.png)
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%2016.png)
>     

---

## 참고

> **참고**
> 
> - CDN(Content Delivery Network)
>     - 지리적 제약 없이 빠르고 안전하게 콘텐츠를 전송할 수 있는 전송 기술
>     - 서버와 사용자 사이의 물리적인 거리를 줄여 콘텐츠 로딩에 소요되는 시간을 최소화
>     (웹 페이지 로드 속도를 높임)
>     - 지리적으로 사용자와 가까운 CDN 서버에 콘텐츠를 저장해서 사용자에게 전달
> 
> - Bootstrap CDN
>     1. Bootstrap 홈페이지 - Download - “Compiled CSS and JS” Download
>     2. CDN을 통해 가져오는 bootstrap css와 js 파일을 확인
>     3. bootstrap.css 파일을 참고하여, 현재까지 작성한 클래스에 적용된 스타일을 직접 확인
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%2017.png)
>     
>     ![Untitled](Fundamentals%20of%20Bootstrap%20a25fbeddd6764158829fc5a803fbaeae/Untitled%2018.png)
>     
> - Bootstrap을 사용하는 이유
>     - 가장 인기 있고 잘 정립된 CSS 프레임워크
>     - 사전에 디자인 된 다양한 컴포넌트 및 기능
>         - 빠른 개발과 유지보수
>     - 손쉬운 반응형 웹 디자인 구현
>     - 커스터마이징(Customizing)이 용이
>     - 크로스 브라우징(Cross Browsing)지원
>         - 모든 주요 브라우저에서 작동하도록 설계되어 있음
>     
> - 책임과 역할
>     - HTML : 콘텐츠의 구조와 의미
>     - CSS : 레이아웃과 디자인
>     
> - 의미론적인 마크업의 이점
>     - “검색엔진 최적화(SEO)”
>         - 검색 엔진이 해당 웹 사이트를 분석하기 쉽게 만들어 검색 순위에 영향을 줌
>     - “웹 접근성(Web Accessibility)”
>         - 시각 장애 사용자가 스크린 리더기로 웹 페이지를 사용할 때 추가적으로 도움

---