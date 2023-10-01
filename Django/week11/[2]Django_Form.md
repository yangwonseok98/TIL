# Django Form
## INDEX
> **INDEX**
>   1. 개요
>   2. Django Form
>   3. Django ModelForm
>   4. Handling HTTP requests
---
## 개요
> - HTML 'form'
>   - 지금까지 사용자로부터 데이터를 받기위해 활용한 방법
>   - 그러나 비정상적 혹은 악의적인 요청을 필터링 할 수 없음
>   - 유효한 데이터인지에 대한 확인이 필요
> - 유효성 검사
>   - 수집한 데이터가 정확하고 유효한지 확인하는 과정
> - 유효성 검사 구현
>   - 유효성 검사를 구현하기 위해서는 입력 값, 형식, 중복, 범위, 보안 등 많은 것들을 고려해야 함
>   - 이런 과정과 기능을 직접 개발하는 것이 아닌 Django가 제공하는 Form을 사용
---
## Django Form
### Form class
> - Django Form
>   - 사용자 입력 데이터를 수집하고,
>   - 처리 및 유효성 검사를 수행하기 위한 도구
>   - 유효성 검사를 단순화하고 자동화 할 수 있는 기능을 제공
> - Form class 정의
>
>   ```python
>   # articles/forms.py
>   from django import forms
>   
>   class ArticleForm(forms.Form):
>       title = forms.CharField(max_length=20)
>       content = forms.CharField()
>   ```
>
> - Form class를 적용한 new 로직
>
>   ```python
>   # articles/views.py
>   from django.shortcuts import render, redirect
>   from .models import Article
>   from .forms import ArticleForm
>   
>   # Create your views here.
>   def index(request):
>       articles = Article.objects.all()
>       context = {
>           'articles' : articles
>       }
>       return render(request, 'index.html', context)
>   
>   def detail(request, pk):
>       article = Article.objects.get(pk=pk)
>       context={
>           'article': article
>       }
>       return render(request, 'detail.html', context)
>   
>   def new(request):
>       form = ArticleForm()
>       context = {
>           'form' : form
>       }
>       return render(request, 'new.html', context)
>   
>   def create(request):
>       title = request.POST.get('title')
>       content = request.POST.get('content')
>       article = Article(title=title, content=content)
>       article.save()
>       return redirect('articles:detail', article.pk)
>   
>   def delete(request, pk):
>       article = Article.objects.get(pk=pk)
>       article.delete()
>       return redirect('articles:index')
>   
>   def edit(request, pk):
>       article = Article.objects.get(pk=pk)
>       context = {
>           'article': article
>       }
>       return render(request, 'edit.html', context)
>   
>   def update(request, pk):
>       title = request.POST.get('title')
>       content = request.POST.get('content')
>       article = Article.objects.get(pk=pk)
>       article.title = title
>       article.content = content
>       article.save()
>       return redirect('articles:detail', pk)
>   ```
>
>   ```html
>   <!--templates/new.html-->
>   {% extends "base.html" %}
>   {% block content %}
>       <h1>NEW</h1>
>       <form action="{% url "articles:create"%}" method='POST'>
>           {% csrf_token %}
>           {{form}}
>           <input type="submit" value='제출'>
>       </form>
>       <hr>
>       <a href="{% url "articles:index" %}">[back]</a>
>   {% endblock content %}
>   ```
>
>   ![img4](Django_Form_img/img4.PNG)
>
> - Form rendering options
>   - label, input 쌍을 특정 HTML 태그로 감싸는 옵션
>   - https://docs.djangoproject.com/en/4.2/topics/form/#form-rendering-options
>
>   ```html
>   <!--templates/new.html-->
>   {% extends "base.html" %}
>   {% block content %}
>       <h1>NEW</h1>
>       <form action="{% url "articles:create"%}" method='POST'>
>           {% csrf_token %}
>           {{form.as_p}}
>           <input type="submit" value='제출'>
>       </form>
>       <hr>
>       <a href="{% url "articles:index" %}">[back]</a>
>   {% endblock content %}
>   ```
>
>   ![img6](Django_Form_img/img6.PNG)
>
---
### widgets
> - Widgets
>   - HTML 'input' element의 표현 담장
> - Widgets 사용
>   - Widget은 단순히 input 요소의 속성 및 출력되는 부분을 변경하는 것
>   - https://docs.djangoproject.com/ko/4.2/ref/forms/widgets/#built-in-widgets
>
>   ```python
>   # articles/forms.py
>   from django import forms
>   
>   class ArticleForm(forms.Form):
>       title = forms.CharField(max_length=20)
>       content = forms.CharField(widget=forms.Textarea)
>   ```
>   ![img7](Django_Form_img/img7.PNG)
>
---
## Django ModelForm
> - Form vs ModelForm
>   - Form
>       - 사용자 입력 데이터를 DB에 저장하지 않을 때 (ex. 로그인)
>   - ModelForm
>       - 사용자 입력 데이터를 DB에 저장해야 할 때 (ex. 게시글, 회원가입)
> - ModelForm
>   - Model과 연결된 Form을 자동으로 생성해주는 기능을 제공
>   - Form + Model
> - ModelForm class 정의
>   - 기존 ArticleForm 클래스 수정
>
>       ```python
>       # articles/forms.py
>       from django import forms
>       from .models import Article
>       
>       class ArticleForm(forms.ModelForm):
>           class Meta:
>               model = Article
>               fields = '__all__'
>       ```
>
> - ModelForm class 적용
>
>   ![img9](Django_Form_img/img9.PNG)
>
> - Meta class
>   - ModelForm의 정보를 작성하는 곳
> - 'fields' 및 'exclude'속성
>   - exclude 속성을 사용하여 모델에서 포함하지 않을 필드를 지정할 수도 있음
>
>       ```python
>       # articles/forms.py
>       from django import forms
>       from .models import Article
>       
>       class ArticleForm(forms.ModelForm):
>           class Meta:
>               model = Article
>               fields = ('title',)
>       ```
>
>       ```python
>       # articles/forms.py
>       from django import forms
>       from .models import Article
>       
>       class ArticleForm(forms.ModelForm):
>           class Meta:
>               model = Article
>               exclude = ('title',)
>       ```
>
> - ModelForm을 적용한 create 로직
>
>   ```python
>   # articles/views.py
>   from django.shortcuts import render, redirect
>   from .models import Article
>   from .forms import ArticleForm
>   
>   def create(request):
>       form = ArticleForm(request.POST)
>       if form.is_valid():
>           article = form.save()
>           return redirect('articles:detail', article.pk)
>       context = {
>           'form': form
>       }
>       return render(request, 'new.html', context)
>   ```
>
>   - 제목 input에 공백을 입력 후 에러 메시지 출력 확인 (유효성 검사의 결과)
>
>       ![img12](Django_Form_img/img12.PNG)
>
> - is_valid()
>   - 여러 유효성 검사를 실행하고,
>   - 데이터가 유효한지 여부를 Boolean으로 반환
> - 공백 데이터가 유효하지 않은 이유와 에러메시지가 출력되는 과정
>
>   ![img13](Django_Form_img/img13.PNG)
>
> - ModelForm을 적용한 edit 로직
>   
>   ```python
>   # articles/views.py
>   from django.shortcuts import render, redirect
>   from .models import Article
>   from .forms import ArticleForm
>   
>   def edit(request, pk):
>       article = Article.objects.get(pk=pk)
>       form = ArticleForm(instance=article)
>       context = {
>           'article': article,
>           'form': form,
>       }
>       return render(request, 'edit.html', context)
>   ```
>   
>   ```html
>   {% extends "base.html" %}
>   {% block content %}
>      <h1>Edit</h1>
>      <form action="{% url "articles:update" article.pk%}" method='POST'>
>          {% csrf_token %}
>          {{form.as_p}}
>          <input type="submit" value='제출'>
>      </form>
>      <hr>
>      <a href="{% url "articles:index" %}">[back]</a>
>   {% endblock content %}
>   ```
>
> - ModelForm을 적용한 update 로직
>
>   ```python
>   # articles/views.py
>   from django.shortcuts import render, redirect
>   from .models import Article
>   from .forms import ArticleForm
>   
>   def update(request, pk):
>       article = Article.objects.get(pk=pk)
>       form = ArticleForm(request.POST, instance=article)
>       if form.is_valid():
>           form.save()
>           return redirect('articles:detail', article.pk)
>       context = {
>           'article': article,
>           'form': form
>       }
>       return render(request, 'edit.html', context)
>   ```
>
> - save()
>   - 데이터베이스 객체를 만들고 저장
> - save() 메서드가 생성과 수정을 구분하는 법
>   - 키워드 인자 instance 여부를 통해 생성할 지, 수정할 지를 결정
>
>       ```python
>       # CREATE
>       form = ArticleForm(request.POST)
>       form.save()
>
>       # UPDATE
>       form = ArticleForm(request.POST, instance=article)
>       form.save()
>       ```
>
> - Django Form 정리
>   - "사용자로부터 데이터를 수집하고 처리하기 위한 강력하고 유연한 도구"
>   - HTML form의 생성, 데이터 유효성 검사 및 처리를 쉽게 할 수 있도록 도움
---
## 참고
> - ModelForm 키워드 인자 data와 instance 살펴보기
>   - https://github.com/django/django/blob/main/django/forms/models.py#L341
> - Widget 응용
>
>   ```python
>   # articles/forms.py
>   from django import forms
>   from .models import Article
>   
>   class ArticleForm(forms.ModelForm):
>       title = forms.CharField(
>           label = '제목',
>           widget = forms.TextInput(
>               attrs={
>                   'class': 'my-title',
>                   'placeholder': 'Enter the title',
>                   'maxlenght': 20,
>               }
>           )
>       )
>       content = forms.CharField(
>           label = '내용',
>           widget = forms.Textarea(
>               attrs={
>                   'class': 'my-content',
>                   'placeholder': 'Enter the content',
>                   'rows': 5,
>                   'cols': 50,
>               }
>           )
>       )
>       class Meta:
>           model = Article
>           fields = '__all__'
>   ```
>
---
## Handling HTTP requests
### view 함수 구조 변화
> - new & create view 함수가 공통점과 차이점
>   - 공통점
>       - "데이터 생성을 구현하기 위함"
>   - 차이점
>       - "new는 GET method 요청만을,
>       - create는 POST method 요청만을 처리"
>
> - **HTTP request method 차이점을 활용해 view 함수 구조 변경**
>   - new & create 함수 결합
>
>       ```python
>       def new(request):
>           form = ArticleForm()
>           context = {
>               'form' : form
>           }
>           return render(request, 'new.html', context)
>       ```
>
>       ```python
>       def create(request):
>           form = ArticleForm(request.POST)
>           if form.is_valid():
>               article = form.save()
>               return redirect('articles:detail', article.pk)
>           context = {
>               'form': form
>           }
>           return render(request, 'new.html', context)
>       ```
>
>       ```python
>       def create(request):
>           if request.method == 'POST':
>               form = ArticleForm(request.POST)
>               if form.is_valid():
>                   article = form.save()
>                   return redirect('articles:detail', article.pk)
>           else:
>               form = ArticleForm()
>           context = {
>               'form': form
>           }
>           return render(request, 'new.html', context)
>       ```
>
> - 새로운 create view 함수
>   - new와 create view 함수의 공통점과 차이점을 기반으로 하나의 함수로 결합
>   - 두 함수의 유일한 차이점이었던 request mothod에 따른 분기
>   - POST 일 때는 과거 create 함수 구조였던 객체 생성 및 저장 로직 처리
>   - POST가 아닐 때는 과거 단순히 form 인스턴스 생성
>   - context에 담기는 form은
>       1. is_valid를 통과하지 못해 에러메시지를 담은 form이거나
>       2. else 문을 통한 form 인스턴스
>
>   ```python
>   def create(request):
>       if request.method == 'POST':
>           form = ArticleForm(request.POST)
>           if form.is_valid():
>               article = form.save()
>               return redirect('articles:detail', article.pk)
>       else:
>           form = ArticleForm()
>       context = {
>           'form': form
>       }
>       return render(request, 'new.html', context)
>   ```
>
> - 기존 new 관련 코드 수정
>   - 사용하지 않는 new url 제거
>
>       ```python
>       # articles/urls.py
>       from django.urls import path
>       from . import views
>       app_name = 'articles'
>       urlpatterns = [
>           path('', views.index, name='index'),
>           path('<int:pk>/', views.detail, name='detail'),
>           # path('new/', views.new, name='new'),
>           path('create/', views.create, name='create'),
>           path('<int:pk>/delete/', views.delete, name='delete'),
>           path('<int:pk>/edit/', views.edit, name='edit'),
>           path('<int:pk>/update/', views.update, name='update')
>       ]
>       ```
>
>   - new url을 create url로 변경
>
>       ```html
>       <!--templates/index.html-->
>       {% extends "base.html" %}
>       {% block content %}
>           <h1>Articles</h1>
>           <a href="{% url "articles:create" %}">NEW</a>
>           <hr>
>           {% for article in articles %}
>               <p>글 번호 : {{article.pk}}</p>
>               <a href="{% url "articles:detail" article.pk %}">
>                   <p>글 제목 : {{article.title}}</p>
>               </a>
>               <p>글 내용 : {{article.content}}</p>
>               <hr>
>           {% endfor %}
>       {% endblock content %}
>       ```
>
>       ```html
>       <!--templates/create.html-->
>       {% extends "base.html" %}
>       {% block content %}
>           <h1>CREATE</h1>
>           <form action="{% url "articles:create"%}" method='POST'>
>               {% csrf_token %}
>               {{form.as_p}}
>               <input type="submit" value='제출'>
>           </form>
>           <hr>
>           <a href="{% url "articles:index" %}">[back]</a>
>       {% endblock content %}
>       ```
>
>   - new 템플릿을 create 템플릿으로 변경
>
>       ```python
>       def create(request):
>           if request.method == 'POST':
>               form = ArticleForm(request.POST)
>               if form.is_valid():
>                   article = form.save()
>                   return redirect('articles:detail', article.pk)
>           else:
>               form = ArticleForm()
>           context = {
>               'form': form
>           }
>           return render(request, 'create.html', context)
>       ```
>
> - request method에 따른 요청의 변화
>
>   ![img24](Django_Form_img/img24.PNG)
>
> - 새로운 update view 함수
>   - 기존 edit과 update view 함수 결합
>     
>       ```python
>       def update(request, pk):
>           article = Article.objects.get(pk=pk)
>           if request.method == 'POST':
>               form = ArticleForm(request.POST, instance=article)
>               if form.is_valid():
>                   form.save()
>                   return redirect('articles:detail', article.pk)
>           else:
>               form = ArticleForm(instance=article)
>           context = {
>               'article': article,
>               'form': form
>           }
>           return render(request, 'edit.html', context)
>       ```
>
> - 기존 edit 관련 코드 수정
>   - 사용하지 않는 edit url 제거
>
>       ```python
>       # articles/urls.py
>       from django.urls import path
>       from . import views
>       app_name = 'articles'
>       urlpatterns = [
>           path('', views.index, name='index'),
>           path('<int:pk>/', views.detail, name='detail'),
>           # path('new/', views.new, name='new'),
>           path('create/', views.create, name='create'),
>           path('<int:pk>/delete/', views.delete, name='delete'),
>           # path('<int:pk>/edit/', views.edit, name='edit'),
>           path('<int:pk>/update/', views.update, name='update')
>       ]
>       ```
>
>   - edit 템플릿을 update 템플릿으로 변경
>
>       ```html
>       <!--templates/detail.html-->
>       {% extends "base.html" %}
>       {% block content %}
>           <h1>DETAIL</h1>
>           <h2>{{article.pk}} 번째 글</h2>
>           <hr>
>           <p>제목 : {{article.title}}</p>
>           <p>내용 : {{article.content}}</p>
>           <p>작성 시각 : {{article.created_at}}</p>
>           <p>수정 시각 : {{article.updated_at}}</p>
>           <hr>
>           <a href="{% url "articles:update" article.pk%}">UPDATE</a>
>           <form action="{% url "articles:delete" article.pk %}" method='POST'>
>               {% csrf_token %}
>               <input type="submit" value='delete'>
>           </form>
>           <a href="{% url "articles:index" %}">[back]</a>
>       {% endblock content %}
>       ```
> 
>       ```html
>       <!--templates/update.html-->
>       {% extends "base.html" %}
>       {% block content %}
>           <h1>UPDATE</h1>
>           <form action="{% url "articles:update" article.pk%}" method='POST'>
>               {% csrf_token %}
>               {{form.as_p}}
>               <input type="submit" value='제출'>
>           </form>
>           <hr>
>           <a href="{% url "articles:index" %}">[back]</a>
>       {% endblock content %}
>       ```
>
---
