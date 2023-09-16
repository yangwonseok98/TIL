# Fundamentals_of_HTML_and_CSS

---

## INDEX

> **INDEX**
> 
> 1. 웹 소개
> 2. 웹 구조화
>     - HTML
>     - HTML 의 구조
>     - 텍스트 구조
> 3. 웹 스타일링
>     - CSS
>     - CSS 선택자
>     - 우선순위
>     - 상속

---

## 웹 소개

> **웹 소개**
> 
> - **World Wide Web**
>     - 인터넷으로 연결된 컴퓨터들이 정보를 공유하는 거대한 정보 공간
>     
> - **Web**
>     - Web site, Web application 등을 통해 사용자들이 정보를 검색하고 상호 작용하는 기술
>     
> - **Web site**
>     - 인터넷에서 여러 개의 Web page가 모인 것으로, 사용자들에게 정보나 서비스를 제공하는 공간
>     
> - **Web page**
>     - HTML, CSS등의 웹 기술을 이용하여 만들어진, **“Web site”를 구성하는 하나의 요소**

> **Web page 구성 요소**
> 
> 1. **HTML** : “Structure”
> 2. **CSS** : “Styling”
> 3. **Javascript** : “Behavior”

---

## 웹 구조화

> **HTML**
> 
> - **HTML(Hyper Text Markup Language)**
>     - 웹 페이지의 의미와 **구조**를 정의하는 언어
>     
> - **Hyper text**
>     - 웹 페이지를 다른 페이지로 연결하는 링크
>     - 참조를 통해 사용자가 한 문서에서 **다른 문서로 즉시 접근할 수 있는 텍스트**
>     
> - **Markup Language**
>     - 태그 등을 이용하여 문서나 데이터의 **구조를 명시하는 언어**
>     - ex) HTML, Markdown

---

> **Structure of HTML**
> 
> - HTML 구조
>     1. **<!DOCTYPE html>**
>         - 해당 문서가 html 문서라는 것을 나타냄
>     2. **<html></html>**
>         - 전체 페이지의 콘텐츠를 포함
>     3. **<head></head>**
>         - HTML 문서에 관련된 설명, 설정 등
>         - 사용자에게 보이지 않음
>     4. **<body></body>**
>         - 페이지에 표시되는 모든 콘텐츠
>     5. **<title></title>**
>         - 브라우저 탭 및 즐겨찾기 시 표시되는 제목으로 사용
>     6. **HTML Element(요소)**
>         
>         ![스크린샷 2023-09-03 오후 12.20.59.png](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-09-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_12.20.59.png)
>         
>         - 하나의 요소는 여는 태그와 닫는 태그 그리고 그 안의 내용으로 구성됨
>         - 닫는 태그는 태그 이름 앞에 슬래시가 포함되며 닫는 태그가 없는 태그도 존재
>     7. HTML Attributes(속성)
>         
>         ![스크린샷 2023-09-03 오후 12.22.39.png](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-09-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_12.22.39.png)
>         
>         1. 규칙
>             - 속성은 요소 이름과 속성 사이에 공백이 있어야 함.
>             - 하나 이상의 속성들이 있는 경우엔 속성 사이에 공백으로 구분함.
>             - 속성 값은 열고 닫는 따옴표로 감싸야 함.
>         2. 목적
>             - 나타내고 싶지 않지만 추가적인 기능, 내용을 담고 싶을 때 사용
>             - CSS에서 해당 요소를 선택하기 위한 값으로 활용됨
> 
> - HTML 구조 예시
>     
>     ![스크린샷 2023-09-03 오후 12.58.16.png](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-09-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_12.58.16.png)
>     
>     ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled.png)
>     

---

> **Text Structure**
> 
> - **HTML Text structure**
>     - HTML의 주요 목적 중 하나는 **텍스트 구조와 의미**를 제공하는 것
>     
> - **HTML(Hyper Text Markup Language)**
>     - 웹 페이지의 의미와 **구조**를 정의하는 언어
>         
>         ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%201.png)
>         
>         - 예를 들어 h1 요소는 단순히 텍스트를 크게만 만드는 것이 아닌 현재 **문서의 최상위 제목**이라는 의미를 부여하는 것
>         
> - **대표적인 HTML Text structure**
>     1. **Heading & Paragraphs**
>         - h1~6, p
>     2. **Lists**
>         - ol, ul, li
>     3. **Emphasis & Importance**
>         - em, strong
>         
> - HTML Text structure 예시
>     
>     ```html
>     <!DOCTYPE html>
>     <html lang="en">
>     <head>
>     	<meta charset = "UTF-8">
>     	<title>My page</title>
>     </head>
>     <body>
>     	<h1>Main Heading</h1>
>         <h2>Sub Heading</h2>
>         <p>This is my page</p>
>         <p>This is</p> <em>emphasis</em>
>         <p>Hi <strong>my name</strong> is Air</p>
>         <ol>
>             <li>파이썬</li>
>             <li>알고리즘</li>
>             <li>웹</li>
>         </ol>
>     </body>
>     </html>
>     ```
>     
>     ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%202.png)
>     

---

## 웹 스타일링

> **CSS**
> 
> - CSS(Cascading Style Sheet)
>     - 웹 페이지의 **디자인**과 **레이아웃**을 구성하는 언어
>     
> - CSS를 적용하지 않은 웹 사이트 모습
>     
>     ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%203.png)
>     
> 
> - CSS 구문
>     
>     ```css
>     h1{
>     	color: red;
>     	font-size: 30px;
>     }
>     ```
>     
>     1. 선택자(Selector) - h1
>     2. 선언(Declaration) - color: red;
>     3. 속성(Property) - font-size
>     4. 값(Value) - 30px
>     
> - CSS 적용 방법
>     1. 인라인(Inline) 스타일
>         - HTML 요소 안에 style 속성 값으로 작성
>             
>             ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%204.png)
>             
>     2. 내부(Internal) 스타일
>         - head 태그 안에 style 태그 작성
>             
>             ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%205.png)
>             
>     3. 외부(External) 스타일
>         - 별도의 CSS 파일 생성 후 HTML link 태그를 사용해 불러 오기
>             
>             ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%206.png)
>             
>             ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%207.png)
>             

---

> **CSS 선택자**
> 
> - CSS Selectors
>     - HTML 요소를 선택하여 스타일을 적용할 수 있도록 하는 선택자
> 
> - CSS Selectors 종류
>     - 기본 선택자
>         1. 전체(*) 선택자
>         2. 요소(tag) 선택자
>         3. 클래스(class) 선택자
>         4. 아이디(id) 선택자
>         5. 속성(attr) 선택자
>     - 결합자 (Combinators)
>         1. 자손 결합자(” “(space))
>         2. 자식 결합자(>)
> 
> - CSS Selectors 특징
>     - 전체 선택자 (*)
>         - HTML 모든 요소를 선택
>     - 요소 선택자
>         - 지정한 모든 태그를 선택
>     - 클래스 선택자(’.’(dot))
>         - 주어진 클래스 속성을 가진 모든 요소를 선택
>     - 아이디 선택자(’#’)
>         - 주어진 아이디 속성을 가진 요소를 선택
>         - 문서에는 주어진 아이디를 가진 요소가 하나만 있어야 함
>     - 자손 결합자(” “(space))
>         - 첫 번째 요소의 자손 요소들 선택
>         - 예) p span은 <p>안에 있는 모든 <span>를 선택 (하위 레벨 상관 없이)
>     - 자식 결합자(”>”)
>         - 첫 번째 요소의 직계 자식만 선택
>         - 예) ul > li은 <ul> 안에 있는 모든 <li>를 선택 (한 단계 아래 자식들만)
>     - 예시
>         
>         ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%208.png)
>         
>         ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%209.png)
>         
>         ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2010.png)
>         
>         ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2011.png)
>         
>         ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2012.png)
>         

---

> **우선순위**
> 
> - Specificity (우선순위)
>     - 동일한 요소에 적용 가능한 같은 스타일을 두 가지 이상 작성 했을 때 어떤 규칙이 적용 되는지 결정하는 것
>     - Specificity 예시
>         - 동일한 h1 태그에 다음과 같이 스타일이 작성된다면 h1 태그 내용의 색은 red가 적용됨
>             
>             ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2013.png)
>             
> 
> - CSS (**Cascading** Style Sheet)
>     - 웹 페이지의 디자인과 레이아웃을 구성하는 언어
>     
> - Cascade (계단식)
>     - 동일한 우선순위를 같는 규칙이 적용될 때 CSS에서 **마지막에 나오는 규칙이 사용**됨
>     - Cascade 예시
>         - h1 태그 내용의 색은 purple이 적용됨
>             
>             ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2014.png)
>             
> 
> - 우선순위가 높은 순
>     1. Importance
>         - !important
>     2. Inline 스타일
>     3. 선택자
>         - id 선택자 > class 선택자 > 요소 선택자
>     4. 소스 코드 순서
> 
> - 우선순위 예시
>     
>     ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2015.png)
>     
>     ![스크린샷 2023-09-03 오후 1.50.53.png](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-09-03_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_1.50.53.png)
>     
>     ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2016.png)
>     
> - !important
>     - 다른 우선순위 규칙보다 우선하여 적용하는 키워드
>     - **Cascade의 구조를 무시하고 강제로 스타일을 적용하는 방식이므로 사용을 권장하지 않음**

---

> **상속**
> 
> - CSS 상속
>     - 기본적으로 CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속해 재 사용성을 높임
> 
> - 상속 여부
>     - 상속 되는 속성
>         - Text 관련 요소(font, color, text-align), opacity, visibility 등
>     - 상속 되지 않는 속성
>         - Box model 관련 요소(width, height, border, box-sizing,…)
>         - position 관련 요소(position, top/right/bottom/left, z-index) 등
>     
> - 상속 예시
>     
>     ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2017.png)
>     
>     ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2018.png)
>     
>     ![Untitled](Fundamentals_of_HTML_and_CSS%204b31e7caf09842a69f7eeb41433dc5e3/Untitled%2019.png)
>     
> - CSS 상속 여부는 MDN 문서에서 확인하기
>     - MDN 각 속성별 문서 하단에 상속 여부를 확인할 수 있음

---

## 참고

> **참고**
> 
> - HTML 관련사항
>     1. 요소(태그) 이름은 대소문자를 구분하지 않지만 “소문자” 사용을 권장
>     2. 속성의 따옴표는 작은 따옴표와 큰 따옴표를 구분하지 않지만 “큰 따옴표” 권장
>     3. HTML은 프로그래밍 언어와 달리 에러를 반환하지 않기 때문에 작성 시 주의
> 
> - CSS 인라인(inline) 스타일은 사용하지 말 것
>     - CSS와 HTML 구조 정보가 혼합되어 작성되기 때문에 코드를 이해하기 어렵게 만듦
> 
> - CSS의 모든 속성을 외우는 것이 아님
>     - 자주 사용되는 속성은 그리 많지 않으며 주로 활용 하는 속성 위주로 사용하다 보면 자연스럽게 익히게 됨
>     - 그 외 속성들은 개발하면 필요할 때마다 검색해서 학습 후 사용할 것
> 
> - 속성은 되도록 ‘class’ 만 사용할 것
>     - id, 요소 선택자 등 여러 선택자들과 함께 사용할 경우 우선순위 규칙에 따라 예기치 못한 스타일 규칙이 적용되어 전반적인 유지보수가 어려워지기 때문
>     - 문서에서 단 한번 유일하게 적용될 스타일에 경우에만 id 선택자 사용을 고려

---