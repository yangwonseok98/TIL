# Django Authentication System 2
## INDEX
1. 회원 가입
2. 회원 탈퇴
3. 회원 정보 수정
4. 비밀번호 변경
5. 로그인 사용자에 대한 접근 제한
---
## 회원가입
- 회원 가입
    - User 객체를 Create 하는 과정
- `UserCreationForm()`
    - 회원 가입시 사용자 입력 데이터를 받을 built-in ModelForm
- 회원 가입 페이지 작성
    ```python
    # accounts/urls.py
    from django.urls import path
    from . import views

    app_name = 'accounts'
    urlpatterns = [
        ...
        path('signup/', views.signup, name='signup')
    ]
    ```
    ```python
    # accounts/views.py
    from django.contrib.auth.forms import UserCreationForm
    def signup(request):
    if request.method == 'POST':
        pass
    else:
        form = UserCreationForm()
    context = {
        'form': form
    }
    return render(request,'accounts/signup.html',context)
    ```
    ```html
    <!--acounts/signup.html-->
    <h1>회원가입</h1>
    <form action="{% url 'accounts:signup' %}" method="POST">
      {% csrf_token %}
      {{ form.as_p }}
      <input type="submit">
    </form>
    ```
- 회원 가입 로직 작성
    ```python
    # accounts/views.py
    def signup(request):
        if request.method == 'POST':
            form = UserCreationForm(request.POST)
            if form.is_valid():
                form.save()
                return redirect('articles:index')
        else:
            form = UserCreationForm()
        context = {
            'form': form
        }
        return render(request,'accounts/signup.html',context)
    ```
- 회원 가입 로직 에러
    - 회원 가입 진행 후 에러 페이지 확인
    - Manager isn't available;'auth.User' has been swapped for 'accounts.User'
    - 회원 가입에 사용하는 UserCreateForm이 우리가 대체한 커스텀 유저 모델이 아닌 기존 유저 모델로 인해 작성된 클래스이기 때문
        -   https://github.com/django/django/blob/main/django/contrib/auth/forms.py#L84
- 커스텀 유저 모델을 사용하려면 다시 작성해야 하는 Form
    1. `UserCreationForm`
    2. `UserChangeForm`
    - 두 Form 모두 `class Meta: model = User` 가 작성된 Form이기 때문
- 회원 가입 로직 작성
    ```python
    # accounts/forms.py
    from django.contrib.auth import get_user_model
    from django.contrib.auth.forms import UserCreationForm, UserChangeForm

    class CustomUserCreationForm(UserCreationForm):
        class Meta(UserCreationForm.Meta):
            model = get_user_model()

    class CustomUserChangeForm(UserChangeForm.Meta):
        class Meta(UserChangeForm):
            model = get_user_model()
    ```
- `get_user_model()`
    - "현재 프로젝트에서 활성화된 사용자 모델(active user model)"을 반환하는 함수
- User 모델을 직접 참조하지 않는 이유
    - get_user_model()을 사용해 User 모델을 참조하면 커스텀 User 모델을 자동으로 반환해주기 때문
    - Django는 User 클래스를 직접 참조하는 대신 get_user_model()을 사용해 참조해야 한다고 필수적으로 강조하고 있음
    - User model 참조에 대한 자세한 내용은 추후 모델 관계에서 다룰 예정
- 회원 가입 로직 작성
    - 커스텀 form 적용
    ```python
    # accounts/views.py
    from .forms import CustomUserCreationForm

    def signup(request):
        if request.method == 'POST':
            form = CustomUserCreationForm(request.POST)
            if form.is_valid():
                form.save()
                return redirect('articles:index')
        else:
            form = CustomUserCreationForm()
        context = {
            'form': form
        }
        return render(request,'accounts/signup.html',context)
    ```
---
## 회원 탈퇴
- 회원 탈퇴
    - User 객체를 Delete하는 과정
- 회원 탈퇴 로직 작성
    ```python
    # accounts/urls.py
    from django.urls import path
    from . import views

    app_name = 'accounts'
    urlpatterns = [
        ...
        path('delete/', views.delete, name='delete'),
    ]
    ```
    ```python
    # accounts/views.py
    def delete(request):
        request.user.delete()
        return redirect('articles:index')
    ```
    ```html
    <!--accounts/index.html-->
      <form action="{% url 'accounts:delete' %}" method='POST'>
        {% csrf_token %}
        <input type="submit" value='회원탈퇴'>
      </form>
    ```
---
## 회원 정보 수정
- 회원 정보 수정
    - User 객체를 Update 하는 과정
- `UserChangeForm()`
    - 회원정보 수정 시 사용자 입력 데이터를 받음
    - built-in ModelForm
- 회원 정보 수정 페이지 작성
    ```python
    # accounts/urls.py
    from django.urls import path
    from . import views

    app_name = 'accounts'
    urlpatterns = [
        ...
        path('update/', views.update, name='update'),
    ]
    ```
    ```python
    # accounts/views.py
    from .forms import CustomUserCreationForm, CustomUserChangeForm

    def update(request):
        if request.method == 'POST':
            pass
        else:
            form = CustomUserChangeForm()
        context = {
            'form': form
        }
        return render(request, 'accounts/update.html', context)
    ```
    ```html
    <!--accounts/update.html-->
    <h1>회원정보수정</h1>
    <form action="{% url 'accounts:update' %}" method="POST">
      {% csrf_token %}
      {{ form.as_p }}
      <input type="submit">
    </form>
    ```
- UserChangeForm 사용 시 문제점
    - User 모델의 모든 정보들(fields)까지 모두 출력되어 수정이 가능하기 때문에 일반 사용자들이 접근해서는 안되는 정보는 출력하지 않도록 해야 함
    - CustomUserChangeForm에서 접근 가능한 필드를 조정
- CustomUserChangeForm 출력 필드 재정의
    - User Model의 필드 목록 확인
        - https://docs.djangoproject.com/en/4.2/ref/contrib/auth/
    ```python
    # accounts/forms.py
    from django.contrib.auth import get_user_model
    from django.contrib.auth.forms import UserCreationForm, UserChangeForm

    class CustomUserChangeForm(UserChangeForm):
        class Meta(UserChangeForm.Meta):
            model = get_user_model()
            fields = ('first_name', 'last_name', 'email')
    ```
- 회원정보 수정 로직 작성
    ```python
    # accounts/views.py
    from .forms import CustomUserCreationForm, CustomUserChangeForm

    def update(request):
        if request.method == 'POST':
            form = CustomUserChangeForm(request.POST, instance=request.user)
            if form.is_valid():
                form.save()
                return redirect('articles:index')
        else:
            form = CustomUserChangeForm(instance=request.user)
        context = {
            'form': form
        }
        return render(request, 'accounts/update.html', context)
    ```
---
## 비밀번호 변경
- 비밀번호 변경
    - 인증된 사용자의 Session 데이터를 Update 하는 과정
- `PasswordChangeForm()`
    - 비밀번호 변경 시 사용자 입력 데이터를 받을 built-in Form
- 비밀번호 변경 페이지 작성
    - django는 비밀번호 변경 페이지를 회원정보 수정 form에서 별도 주소로 안내
    `/user_pk/password/`
    ```python
    # project/urls.py
    from django.contrib import admin
    from django.urls import path, include
    from accounts import views

    urlpatterns = [
        ...
        path('<int:user_pk>/password/', views.change_password, name='change_password'),
    ]

    ```
    ```python
    # accounts/views.py
    from django.contrib.auth.forms import AuthenticationForm, PasswordChangeForm

    def change_password(request, user_pk):
        if request.method == 'POST':
            pass
        else:
            form = PasswordChangeForm()
        context = {
            'form' : form
        }
        return render(request, 'accounts/change_password.html', context)
    ```
    ```html
    <!--accounts/change_password.html-->
    <h1>비밀번호 변경</h1>
    <form action="{% url 'change_password' user.pk %}" method="POST">
      {% csrf_token %}
      {{ form.as_p }}
      <input type="submit">
    </form>
    ```
- 비밀번호 변경 로직 작성
    ```python
    # accounts/views.py
    from django.contrib.auth.forms import AuthenticationForm, PasswordChangeForm

    def change_password(request, user_pk):
        if request.method == 'POST':
            form = PasswordChangeForm(request.user, request.POST)
            if form.is_valid():
                form.save()
                return redirect('articles:index')
        else:
            form = PasswordChangeForm(request.user)
        context = {
            'form' : form
        }
        return render(request, 'accounts/change_password.html', context)
    ```
---
### 세션 무효화 방지하기
- 암호 변경 시 세션 무효화
    - 비밀번호가 변경되면 기존 세션과의 회원 인증 정보가 일치하지 않게 되어 버려 로그인 상태가 유지되지 못하고 로그아웃 처리됨
    - 비밀번호가 변경되면서 기존 세션과의 회원 인증 정보가 일치하지 않기 때문
- `update_session_auth_hash(request, user)`
    - 암호 변경 시 세션 무효화를 막아주는 함수
    - 암호가 변경되면 새로운 password의 Session Date로 기존 session을 자동으로 갱신
- update_session_auth_hash 적용
    ```python
    # accounts/views.py
    from django.contrib.auth.forms import AuthenticationForm, PasswordChangeForm
    from django.contrib.auth import update_session_auth_hash

    def change_password(request, user_pk):
        if request.method == 'POST':
            form = PasswordChangeForm(request.user, request.POST)
            if form.is_valid():
                user = form.save()
                update_session_auth_hash(request, user)
                return redirect('articles:index')
        else:
            form = PasswordChangeForm(request.user)
        context = {
            'form' : form
        }
        return render(request, 'accounts/change_password.html', context)
    ```
---
## 인증된 사용자에 대한 접근 제한
- 로그인 사용자에 대해 접근은 제한하는 2가지 방법
    1. `is_authenticated` 속성
    2. `login_required` 데코레이터
- `is_authenticated`
    - 사용자가 인증 되었는지 여부를 알 수 있는 User model의 속성
    - 모든 User 인스턴스에 대해 항상 True인 읽기 전용 속성이며, 비인증 사용자에 대해서는 항상 False
- `is_authenticated` 적용하기
    - 로그인과 비 로그인 상태에서 화면에 출력되는 링크를 다르게 설정하기
        ```html
        <!--articles/index.html-->
        {% if request.user.is_authenticated %}
            <h3>{{ user.username }}님 안녕하세요!</h3>

            <form action="{% url 'accounts:logout' %}" method="POST">
                {% csrf_token %}
                <input type="submit" value="LOGOUT">
            </form>
            <form action="{% url 'accounts:delete' %}" method='POST'>
                {% csrf_token %}
                <input type="submit" value='회원탈퇴'>
            </form>
            <a href="{% url 'accounts:update' %}">회원정보수정</a>
            <hr>
            <a href="{% url 'articles:create' %}">CREATE</a>
            <hr>
        {% else %}
            <a href="{% url 'accounts:login' %}">LOGIN</a>
            <hr>
            <a href="{% url 'accounts:signup' %}">SIGNUP</a>
            <hr>
        {% endif %}
        ```
    - 인증된 사용자라면 로그인/회원가입 로직을 수행할 수 없도록 하기
        ```python
        # accounts/views.py
        def login(request):
            if request.user.is_authenticated:
                return redirect('articles:index')
            ...

        def signup(request):
            if request.user.is_authenticated:
                return redirect('articles:index')
            ...

        ```
- `login_required`
    - 인증된 사용자에 대해서만 view 함수를 실행시키는 데코레이터
    - 비인증 사용자의 경우 `/accounts/login/` 주소로 `redirect` 시킴
- `login_required` 적용하기
    - 인증되 사용자만 게시글을 작성/수정/삭제 할 수 있도록 수정
        ```python
        # articles/views.py
        from django.contrib.auth.decorators import login_required

        @login_required
        def create(request):
            ...

        @login_required
        def delete(request, pk):
            ...

        @login_required
        def update(request, pk):
            ...

        ```
        ```python
        # accounts/views.py
        from django.contrib.auth.decorators import login_required

        @login_required
        def logout(request):
            ...
            
        @login_required
        def delete(request):
            ...

        @login_required
        def update(request):
            ...

        @login_required
        def change_password(request, user_pk):
            ...
        ```
