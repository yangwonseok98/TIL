# Django Template & URLs

---

## INDEX

> **INDEX**
> 
> - Django Template
>     - Template System
>     - 템플릿 상속
>     - HTML form (요청과 응답)
> - Django URLs
>     - Django URLs
>     - 변수와 URL
>     - App과 URL
>     - URL 이름 지정
>     - URL 이름 공간

---

## Django Template

### Template System

> **Template System**
> 
> - Django Template system
>     - 데이터 **표현**을 제어하면서, **표현**과 관련된 부분을 담당
> 
> - HTML의 콘텐츠를 변수 값에 따라 바꾸고 싶다면?
>     
>     ```python
>     def index(request):
>     	context = {
>     		'name': 'jane'
>     	}
>     	return render(request, 'articles/index.html', context)
>     ```
>     
>     ```html
>     <body>
>     	<h1>Hello, {{name}}</h1>
>     </body>
>     ```
>     
> - Django Template Language(DTL)
>     - Template에서 조건, 반복, 변수 등의 프로그래밍적 기능을 제공하는 시스템
> 
> - DTL Syntax
>     1. Variable
>             
>         - render 함수의 세번째 인자로 딕셔너리 데이터를 사용
>         - 딕셔너리 key에 해당하는 문자열이 template에서 사용 가능한 변수명이 됨
>         - dot(.)를 사용하여 변수 속성에 접근할 수 있음
>         
>           `{{variable}}`
>         
>     2. Filters
>         
>         
>         - 표시할 변수를 수정할 때 사용
>         - chained가 가능하며 일부 필터는 인자를 받기도 함
>         - 약 60개의 built-in-template filters를 제공
>         
>           `{{variable|filter}}`
>
>           `{{name|turncatewords:30}}`
>         
>         
>         
>     3. Tags
>         
>         
>          - 반복 또는 논리를 수행하여 제어 흐름을 만듦
>         - 일부 태그는 시작과 종료 태그가 필요
>         - 약 24개의 built-in template tags를 제공
>         
>           `{% tag %}`
>
>           `{% if %} {% endif %}`
>         
>     4. Comments
>         
>         
>          - DTL에서의 주석
>
>               `<h1>Hello, {#name#}</h1>`
>
>               ```
>               {% comment %} 
>               {% if name == 'Sophia' %}
>               {% endif %} 
>               {% endcomment %}
>               ```
>         
> - DTL 예시
>    ```python
>    # project/urls.py
>    from django.contrib import admin
>    from django.urls import path
>    from articles import views # articles 패키지에서 views 모듈을 가져오는 것
>
>    urlpatterns = [
>        path('admin/', admin.site.urls),
>        path('articles/', views.index),  
>        path('dinner/', views.dinner),  # 새로운 경로 등록
>    ]
>    ```
>
>   ```python 
>   from djnago.shortcuts import render
>   import random
>   def dinner(request):
>        foods = ['국밥', '국수', '카레', '탕수육']
>        picked = random.choice(foods)
>        context = {
>            'foods': foods,
>            'picked': picked,
>        }
>        return render(request, 'articles/dinner.html', context)
>   ```
>
>   ```html
>   <!-- articles/templates/articles/dinner.html -->
>   <p>{{picked}} 메뉴는 {{picked|length}}글자 입니다.</p>
>   <h2>메뉴판</h2>
>   <ul>
>       {% for food in foods%}
>           <li>{{food}}</li>
>       {% endfor %}
>   </ul>
>   {% if foods|length == 0 %}
>       <p>메뉴가 소진되었습니다.</p>
>   {% else %}
>       <p>아직 메뉴가 남았습니다.</p>
>   {% endif %}
>   ```
---

### 템플릿 상속

> **템플릿 상속**
> 
> - 기본 템플릿 구조의 한계
>     - 만약 모든 템플릿에 bootstrap을 적용하려면?
>     - 모든 템플릿에 bootstrap CDN을 작성해야 할까?
> 
> - 템플릿 상속 (Template inheritance)
>     - **페이지의 공통 요소를 포함**하고,
>     - **하위 템플릿이 재정의 할 수 있는 공간**을 정의하는
>     - 기본 ‘skeleton’ 템플릿을 작성하여 상속 구조를 구축
> 
> - 상속 구조 구축
>     - skeleton 역할의 상위 템플릿 작성
>   
>       ```html
>       <!-- articles/templates/articles/base.html -->
>       <!DOCTYPE html>
>       <html lang="en">
>       <head>
>           <meta charset="UTF-8">
>           <meta name="viewport" content="width=device-width,initial-scale=1.0">
>           <title>Document</title>
>       </head>
>       <body>
>           {% block content %} 
>           <!--여기에 하위템플릿이 들어 갈 것 -->
>           {% endblock content %}
>       </body>
>       </html>
>       ```   
>     
>     - 기존 하위 템플릿의 변화
>         
>       ```html
>       <!-- articles/templates/articles/index.html-->
>       {% extends "articles/base.html" %}
>       {% block content %}
>           <h1>Hello, {{name}}</h1>
>       {% endblock content %}
>       ```
>         
>       ```html
>       <!-- articles/templats/articles/dinner.html -->
>       {% extends "articles/base.html" %}
>       {% block content %}
>           <p>{{picked}} 메뉴는 {{picked|length}}글자 입니다.</p>
>           <h2>메뉴판</h2>
>           <ul>
>               {% for food in foods%}
>                   <li>{{food}}</li>
>               {% endfor %}
>           </ul>
>           {% if foods|length == 0 %}
>               <p>메뉴가 소진되었습니다.</p>
>           {% else %}
>               <p>아직 메뉴가 남았습니다.</p>
>           {% endif %}
>       {% endblock content %}
>       ```
>         
>     
> - ‘extends’ tag
>     
>   `{% extends 'path' %}`
>     
>     - 자식(하위) 템플릿이 부모 템플릿을 확장한다는 것을 알림
>     - **반드시 템플릿 최상단에 작성되어야 함 (2개 이상 사용 불가)**
> 
> - ‘block’ tag
>     
>   `{% block name %}{% endblock name%}`
>     
>     - 하위 템플릿에서 재정의 할 수 있는 블록을 정의
>     (하위 템플릿이 작성할 수 있는 공간을 지정)
>     - 하위 템플릿이 재정의 할 수 있는 block 공간
>         
---

### HTML form (요청과 응답)

> **HTML form (요청과 응답)**
> 
> - 데이터를 보내고 가져오기 [Sending and Retrieving form data]
>     - HTML form element를 통해 사용자와 애플리케이션 간의 상호작용 이해하기
> 
> - HTML form은 HTTP 요청을 서버에 보내는 가장 편리한 방법
>     
> - 실제 웹 서비스에서 form이 사용되는 예시
>     - 네이버 & 구글의 로그인 form
>         
> - ‘form’ element
>     - 사용자로부터 할당된 데이터를 서버로 전송
>     - 웹에서 사용자 정보를 입력하는 여러 방식
>     (text, password, checkbox 등)을 제공
> 
> - fake Naver 실습
>     
>   ```python
>   # project/urls.py
>   from django.contrib import admin
>   from django.urls import path
>   from articles import views 
>   
>   urlpatterns = [
>       path('admin/', admin.site.urls),
>       path('articles/', views.index),  
>       path('dinner/', views.dinner),
>       path('search/', views.search),  # 새로운 경로
>   ]
>   ```
>   
>   ```python
>   # articles/views.py
>   def search(request):
>       return render(request, 'articles/search.html')
>   ```
>     
>   ```html
>   <!--articles/templates/articles/search.html-->
>   {% extends "articles/base.html" %}
>   {% block content %}
>       <form action="">
>           <label for="message">검색어</label>
>           <input type="text" id='message' name='message'>
>           <input type="submit" value="submit">
>       </form>
>   {% endblock content %}
>   ```
>     
>     - input에 hello를 입력하고 제출 버튼을 누른 후 브라우저의 url 변화 확인
>             
>       `http://127.0.0.1:8000/search/?message=hello`
>            
>     - Naver 에서 검색 후 URL 확인
>         
>       `https://search.naver.com/search.naver?query=hello`
>         
>       ```html
>       <!--articles/templates/articles/search.html-->
>       {% extends "articles/base.html" %}
>       {% block content %}
>           <form action="https://search.naver.com/search.naver/">
>               <label for="message">검색어</label>
>               <input type="text" id='message' name='query'>
>               <input type="submit" value="submit">
>           </form>
>       {% endblock content %}
>       ```     
>     
> - form의 핵심 속성 2가지
>     - ‘action’ & ‘method’
>     - 데어터를 **어디(action)**로 **어떤 방식(method)**으로 요청할지
> 
> - action과 method
>     - action
>         
>         
>          - 입력 데이터가 전송될 URL을 지정 (목적지)
>         - 만약 이 속성을 지정하지 않으면 데이터는 현재 form이 있는 페이지의 URL로 보내짐
>         
>         
>         
>     - method
>         
>         
>          - 데이터를 어떤 방식으로 보낼 것인지 정의
>         - 데이터의 HTTP request methods (GET, POST)를 지정
>         
>         
>         
> 
> - ‘input’ element
>     - 사용자의 데이터를 입력 받을 수 있는 요소
>     (type 속성 값에 따라 다양한 유형의 입력 데이터를 받음)
> 
> - ‘name’ attribute
>     - input의 핵심 속성
>     - 입력한 데이터에 붙이는 이름(key)
>     - 데이터를 제출했을 때 서버는 name 속성에 설정된 값을 통해서만 사용자가 입력한 데이터에 접근할 수 있음
> 
> - Query String Parameters
>     - 사용자의 입력 데이터를 URL 주소에 파라미터를 통해 서버로 보내는 방법
>     - 문자열은 앰퍼샌드(&)로 연결된 key=value 쌍으로 구성되며
>     기본 URL과 물음표(?) 로 구분됨
>     - 예시
>         
>       `https://host:port/path?key=value&key=value`
>         

> **form 활용**
> 
> - 사용자 입력 데이터를 받아 그대로 출력하는 서버 만들기
>     - view 함수는 몇 개가 필요할까?
>         - 2개
>         
>     
>     - throw 로직 작성
>         
>       ```python
>       # project/urls.py
>       from django.contrib import admin
>       from django.urls import path
>       from articles import views 
>       
>       urlpatterns = [
>           path('admin/', admin.site.urls),
>           path('throw/',views.throw), # throw 관련 url 작성
>           path('catch/',views.catch),
>       ]
>       ```
>
>       ```python
>       # articles/views.py
>       def throw(request):
>           return render(request, 'articles/throw.html')
>       ```
>
>       ```html
>       <!-- articles/templates/articles/throw.html-->
>       {% extends "articles/base.html" %}
>       {% block content %}
>           <h1>Throw</h1>
>           <form action="/catch/" method='GET'>
>               <input type="text" name='message'>
>               <input type="submit" value='제출'>
>           </form>
>       {% endblock content %}
>       ```
>     
>     - catch 로직 작성
>         - throw 페이지에서 요청한 사용자 입력 데이터는 어떻게 가져와야 할까?
>
>       ```python
>       # project/urls.py
>       from django.contrib import admin
>       from django.urls import path
>       from articles import views 
>       
>       urlpatterns = [
>           path('admin/', admin.site.urls),
>           path('throw/',views.throw), 
>           path('catch/',views.catch), # catch 관련 url 작성
>       ]
>       ```
>         
>       ```python
>       # articles/views.py
>       def catch(request):
>           message = request.GET.get('message')
>           context = {
>               'message' : message
>           }
>           return render(request, 'articles/catch.html', context)
>       ```
>         
>       ```html
>       <!--articles/templates/articles/catch.html-->
>       {% extends "articles/base.html" %}
>       {% block content %}
>           <h1>Catch</h1>
>           <p>{{message}}를 받았다!</p>
>       {% endblock content %}
>       ```
>     
> - HTTP request 객체
>     - form으로 전송한 데이터 뿐만 아니라 모든 요청 관련 데이터가 담겨 있음
>     (view 함수의 첫 번째 인자)
> 
> - request 객체 살펴보기
>     
>   ```python
>   # articles/views.py
>   def catch(request):
>       print(request)
>       print(type(request))
>       print(dir(request))
>       print(request.GET)
>       print(request.GET.get('message'))
>       message = request.GET.get('message')
>       context = {
>           'message' : message
>       }
>       return render(request, 'articles/catch.html', context)
>   ```
>
>   ```plain text
>   <WSGIRequest: GET '/catch/?message=%EB%B0%A9%EA%B0%80%EB%B0%A9%EA%B0%80'>
>   <class 'django.core.handlers.wsgi.WSGIRequest'>
>   ['COOKIES', 'FILES', 'GET', 'META', 'POST', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', '_current_scheme_host', '_encoding', '_get_full_path', '_get_post', '_get_raw_host', '_get_scheme', '_initialize_handlers', '_load_post_and_files', '_mark_post_parse_error', '_messages', '_read_started', '_set_content_type_params', '_set_post', '_stream', '_upload_handlers', 'accepted_types', 'accepts', 'body', 'build_absolute_uri', 'close', 'content_params', 'content_type', 'csrf_processing_done', 'encoding', 'environ', 'get_full_path', 'get_full_path_info', 'get_host', 'get_port', 'get_signed_cookie', 'headers', 'is_secure', 'method', 'parse_file_upload', 'path', 'path_info', 'read', 'readline', 'readlines', 'resolver_match', 'scheme', 'session', 'upload_handlers', 'user']
>   <QueryDict: {'message': ['방가방가']}>
>   방가방가
>   ```
>     
> - form 데이터를 가져오는 방법
>     
>   `request.GET.get('message')`
>   - `request.GET` : 쿼리 딕셔너리
>   - `.get('message')` : 딕셔너리 get 메서드를 사용해 키값 조회
>     

---

### 참고

> **참고**
> 
> - 추가 템플릿 경로 지정
>     - 템플릿 기본 경로 외 커스텀 경로 추가하기
>         
>       ```python
>       # project/settings.py
>       TEMPLATES = [
>           {
>               'BACKEND': 'django.template.backends.django.DjangoTemplates',
>               'DIRS': [BASE_DIR/'templates',], # 추가하고 싶은 경로 추가
>               'APP_DIRS': True,
>               'OPTIONS': {
>                   'context_processors': [
>                       'django.template.context_processors.debug',
>                       'django.template.context_processors.request',
>                       'django.contrib.auth.context_processors.auth',
>                       'django.contrib.messages.context_processors.messages',
>                   ],
>               },
>           },
>       ]
>       ```
>           
>       - BASE_DIR/templates 로 base.html 파일옮기기
>       - base.html 을 상속받는 모든 html 파일의`{% extends articles/base.html %}` 을
>
>           `{%extends base.html %` 로 변경
>     
> 
> - BASE_DIR
>     - settings에서 경로 지정을 편하게 하기 위해 최상단 지점을 지정해 놓은 변수
>         
>         ![Untitled](Django%20Template%20&%20URLs%20img/Untitled%2030.png)
>         
> 
> - DTL 주의사항
>     - Python처럼 일부 프로그래밍 구조(if, for 등)를 사용할 수 있지만
>     명칭을 그렇게 설계 했을 뿐이지 Python 코드로 실행되는 것이 아니며
>     Python과는 관련 없음
>     - 프로그래밍적 로직이 아니라 프레젠테이션을 위한 것임을 명심할 것
>     - 프로그래밍적 로직은 되도록 view 함수에서 작성 및 처리
>     - 공식 문서를 참고해 다양한 태그와 필터 사용해보기
>         - https://docs.djangoproject.com/en/4.2/ref/templates/builtins/

---

## Django URLs

### Django URLs

> **Django URLs**
> 
> - 요청과 응답에서 Django URLs의 역할
>     
>     ![Untitled](Django%20Template%20&%20URLs%20img/Untitled%2031.png)
>     
> 
> - URL dispatcher (운항 관리자, 분배기)
>     - URL 패턴을 정의하고
>     해당 패턴이 일치하는 요청을 처리할 view 함수를 연결(매핑)

---

### 변수와 URL

> **변수와 URL**
> 
> - 현재 URL 관리의 문제점
>     - 템플릿의 많은 부분이 중복되고, URL의 일부만 변경되는 상황이라면
>     계속해서 비슷한 URL과 템플릿을 작성해 나가야 할까?
>       ```python
>       # project/setting.py
>       urlpatterns = [
>           path('articles/1/', ...),
>           path('articles/2/', ...), 
>           path('articles/3/', ...),
>           path('articles/4/', ...),
>           path('articles/5/', ...), 
>           ...,
>       ]
>       ```
>         
> - Variable Routing
>     - URL 일부에 변수를 포함시키는 것
>     (변수는 view 함수의 인자로 전달 할 수 있음)
> 
> - Variable routing 작성법
>     
>   - `<path_converter:variable_name>`
>       - `path('articles/<int:num>', views.detail)`
>
>       - `path('hello/<str:name>/, view.greeting)`
>     
>   - path converter
>         - URL 변수의 타입을 지정
>         (str, int 등 5가지 타입 지원)
>     
> - Variable routing 실습
>     - 실습 1
>         
>       ```python
>       # project/urls.py
>       from django.contrib import admin
>       from django.urls import path
>       from articles import views 
>       
>       urlpatterns = [
>           path('hello/<str:name>/', views.hello)
>       ]
>       ```
>
>       ```python
>       # articles/views.py
>       def hello(request, name):
>           context = {
>               'name': name
>           }
>           return render(request, 'articles/hello.html', context)
>       ```
>
>       ```html
>       <!--articles/templates/articles/hello.html-->
>       {% extends "base.html" %}
>       {% block content %}
>           <h1>Greeting</h1>
>           <p>{{name}}님 안녕하세요!</p>
>       {% endblock content %}
>       ```
>         
>     - 실습 2
>         
>       ```python
>       # project/urls.py
>       from django.contrib import admin
>       from django.urls import path
>       from articles import views 
>       
>       urlpatterns = [
>           path('articles/<int:num>/', views.detail)
>       ]
>       ```
>
>       ```python
>       # articles/views.py
>       def detail(request, num):
>           context = {
>               'num' : num
>           }
>           return render(request, 'articles/detail.html', context)
>       ```
>
>       ```html
>       <!--articles/templates/articles/detail.html-->
>       {% extends "base.html" %}
>       {% block content %}
>           <h1>Detail</h1>
>           <h3>{{num}}번 글 입니다.</h3>
>       {% endblock content %}
>       ```
>         
---

### App과 URL

> **App과 URL**
> 
> - App URL mapping
>     - 각 앱에 URL을 정의하는 것
>     - 프로젝트와 각 앱 URL을 나누어 관리를 편하게 하기 위함
> 
> - 2번째 앱 pages 생성 후 발생할 수 있는 문제
>     - view 함수 이름이 같거나 같은 패턴의 url 주소를 사용하게 되는 경우
>     - 아래 코드와 같이 해결할 수 있으나 더 좋은 방법이 필요
>     - **“URL을 각자 app에서 관리하자”**
>          
> - 기존 url 구조
>     
>     ![Untitled](Django%20Template%20&%20URLs%20img/Untitled%2038.png)
>     
> - 변경된 url 구조
>     
>     ![Untitled](Django%20Template%20&%20URLs%20img/Untitled%2039.png)
>     
> - url 구조 변화
>     
>   ```python
>   # project/urls.py
>   from django.contrib import admin
>   from django.urls import path, include
>   
>   urlpatterns = [
>       path('admin', admin.site.urls),
>       path('articles/', include('articles.urls')),
>       path('pages/', include('pages.urls')),
>   ]
>   ```
>
>   ```python
>   # articles/urls.py
>   from django.urls import path
>   from . import views
>   
>   urlpatterns = [
>       path('dinner/', views.dinner),
>       path('search/', views.search),
>       path('throw/', views.throw),
>       path('catch/', views.catch),
>       path('<int:num>/', views.detail),
>       path('hello/<str:name>/', views.hello)
>   ]
>   ```
>
>   ```python
>   # pages/urls.py
>   from django.urls import path
>   from . import views
>   
>   urlpatterns = [
>       path('index/', views.index)
>   ]
>   ```
>     
>     - include()
>         - 프로젝트 내부 앱들의 URL을 참조할 수 있도록 매핑하는 함수
>         - URL의 일치하는 부분까지 잘라내고,
>         남은 문자열 부분은 후속 처리를 위해 include된 URL로 전달
>     
>     - include 적용
>         - 변경된 프로젝트의 urls.py
>             
>           ```python
>           # project/urls.py
>           from django.contrib import admin
>           from django.urls import path, include
>           
>           urlpatterns = [
>               path('admin', admin.site.urls),
>               path('articles/', include('articles.urls')),
>               path('pages/', include('pages.urls')),
>           ]
>           ```            
---

### URL 이름 지정

> **URL 이름 지정**
> 
> - url 구조 변경에 따른 문제점
>     - 기존 ‘articles/’ 주소가 ‘articles/index/’로 변경됨에 따라 해당 주소를 사용하는 모든 위치를 찿아가 변경해야 함
>     - **“URL에 이름을 지어주면 이름만 기억하면 되지 않을까?”**
>       
>       ```python
>       # project/urls.py
>       from django.contrib import admin
>       from django.urls import path, include
>       
>       urlpatterns = [
>           path('admin', admin.site.urls),
>           path('articles/', include('articles.urls')),
>           path('pages/', include('pages.urls')),
>       ]
>       ```
>   
>       ```python
>       # articles/urls.py
>       from django.urls import path
>       from . import views
>       
>       urlpatterns = [
>           path('index/', views.index, name='index')
>       ]
>       ```
>     
> - Naming URL patterns
>     - URL에 이름을 지정하는 것
>     (path 함수의 name 인자를 정의해서 사용)
>     
> - Naming URL patterns 적용
>     - path 함수의 name 키워드 인자를 정의해서 사용
>     
>       ```python
>       # articles/urls.py
>       from django.urls import path
>       from . import views
>       
>       urlpatterns = [
>           path('index/', views.index, name='index'),
>           path('dinner/', views.dinner, name='dinner'),
>           path('search/', views.search, name='search'),
>           path('throw/', views.throw, name='throw'),
>           path('catch/', views.catch, name='catch'),
>           path('<int:num>/', views.detail, name='detail'),
>           path('hello/<str:name>/', views.hello, name='hello')
>       ]
>       ```
>
>       ```python
>       # pages/urls.py
>       from django.urls import path
>       from . import views
>       
>       urlpatterns = [
>           path('index/', views.index, name='index')
>       ]
>       ```
>     
> - URL 표기 변화
>     - href 속성 값 뿐만 아니라 form의 action 속성처럼 url을 작성하는 모든 위치에서 변경
>         
>       ```html
>       <!--articles/templates/articles/index.html-->
>       {% extends "base.html" %}
>       {% block content %}
>           <h1>Hello, {{name}}</h1>
>           <a href="{% url "dinner" %}">dinner</a>
>           <a href="{% url "search" %}">search</a>
>           <a href="{% url "throw" %}">throw</a>
>       {% endblock content %}
>       ```       
> 
> - ‘url’ tag
>     
>   `{% url "url-name" arg1 arg2 .. %}`
>     
>     - 주어진 URL 패턴의 이름과 일치하는 절대 경로 주소를 반환
> 
> - url 태그 적용 후 브라우저 출력 확인
>     
>     ![Untitled](Django%20Template%20&%20URLs%20img/Untitled%2046.png)
>     

---

### URL 이름 공간

> **URL 이름 공간**
> 
> - URL 이름 지정 후 남은 문제
>     - articles 앱의 url 이름과 pages 앱의 url 이름이 같은 상황
>     - 단순히 이름만으로는 완벽하게 분리할 수 없음
>     - “이름에 성(키, key)을 붙이자”
>     
>       ```python
>       # articles/urls.py
>       from django.urls import path
>       from . import views
>       
>       urlpatterns = [
>           path('index/', views.index, name='index'),
>           path('dinner/', views.dinner, name='dinner'),
>           path('search/', views.search, name='search'),
>           path('throw/', views.throw, name='throw'),
>           path('catch/', views.catch, name='catch'),
>           path('<int:num>/', views.detail, name='detail'),
>           path('hello/<str:name>/', views.hello, name='hello')
>       ]
>       ```
>
>       ```python
>       # pages/urls.py
>       from django.urls import path
>       from . import views
>       
>       urlpatterns = [
>           path('index/', views.index, name='index')
>       ]
>       ```
>     
> - ‘app_name’ 속성 지정
>     - app_name 변수 값 설정
>     
>       ```python
>       # articles/urls.py
>       from django.urls import path
>       from . import views
>       
>       app_name = 'articles'
>       urlpatterns = [
>           path('index/', views.index, name='index'),
>           path('dinner/', views.dinner, name='dinner'),
>           path('search/', views.search, name='search'),
>           path('throw/', views.throw, name='throw'),
>           path('catch/', views.catch, name='catch'),
>           path('<int:num>/', views.detail, name='detail'),
>           path('hello/<str:name>/', views.hello, name='hello')
>       ]
>       ```
>
>       ```python
>       # pages/urls.py
>       from django.urls import path
>       from . import views
>       
>       app_name = 'pages'
>       urlpatterns = [
>           path('index/', views.index, name='index')
>       ]
>       ```
>     
> - URL tag의 최종 변화
>     - 마지막으로 url 태그가 사용하는 모든 곳의 표기 변경하기
>         
>       `{% url 'index' %}` 에서
>
>       `{% url 'articles:index %}` 로
>         
---

### 참고

> **참고**
> 
> - Trailing Slashes
>     - Django는 URL 끝에 ‘/’가 없다면 자동으로 붙임(Django의 url 설계 철학)
>     - “기술적인 측면에서, [foo.com/bar](http://foo.com/bar) 와 [foo.com/bar/](http://foo.com/bar/) 는 서로 다른 URL”
>         - 검색 엔진 로봇이나 웹 트래픽 분석 도구에서는 이 두 조소를 서로 다른 페이지로 봄
>     - 그래서 Django는 검색 엔진이 혼동하지 않게 하기 위해 붙이는 것을 선택한 것
>     - 그러나 모든 프레임워크가 이렇게 동작하는 것은 아니니 주의

---