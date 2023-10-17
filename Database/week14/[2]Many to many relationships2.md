# Many to many relationships 2
## INDEX
1. Many to many relationships 2
    - 팔로우
2. Django Fixtures
    - Fixtures
3. Improve query
    - 쿼리 개선
---
## 팔로우
### 1. 프로필
1. 프로필 페이지
    - 각 회원의 개인 프로필 페이지에 팔로우 기능을 구현하기 위해 프로필 페이지를 먼저 구현
2. 프로필 구현
    1. url 작성
        ```python
        # accounts/urls.py
        urlpatterns = [
            ...
            path('profile/<username>/', views.profile, name='profile'),
        ]
        ```
    2. view 함수 작성
        ```python
        # accounts/views.py
        def profile(request, username):
            users = get_user_model()
            person = users.objects.get(username=username)
            context = {
                'person': person
            }
            return render(request, 'accounts/profile.html', context)        
        ```
    3. profile 템플릿 작성
        ```html
        <h1>{{person.username}}님의 프로필</h1>
        <hr>
        <h2>작성한 게시글</h2>
            {% for article in person.article_set.all %}
                <p>{{article.title}}</p>
            {% endfor %}
        <hr>
        <h2>작성한 댓글</h2>
            {% for comment in person.comment_set.all %}
                <p>{{comment.content}}</p>
            {% endfor %}
        <hr>
        <h2>좋아요를 누른 게시글</h2>
            {% for article in person.like_articles.all %}
                <p>{{article.title}}</p>
            {% endfor %}
        <hr>
        ```
    4. 프로필 페이지로 이동할 수 있는 링크 작성
        ```html
        <a href="{% url 'accounts:profile' request.user.username %}">내 프로필</a>
        <p>작성자 : <a href="{% url 'accounts:profile' article.user.username%}">{{ article.user }}</a></p>
        ```
    5. 프로필 페이지 결과 확인
---
### 2. 팔로우 기능 구현
1. User(M) - User(N)
    - 0명 이상의 회원은 0명 이상의 회원과 관련
    - 회원은 0명 이상의 팔로워를 가질 수 있고, 0명 이상의 다른 회원들을 팔로잉 할 수 있음
2. 팔로우 기능 구현
    1. ManyToManyField 작성
        ```python
        # accounts/models/py
        class User(AbstractUser):
            followings = models.ManyToManyField('self', symmetrical=False, related_name='followers')
        ```
        - 참조
            - 내가 팔로우하는 사람들 (팔로잉, followings)
        - 역참조
            - 상대방 입장에서 나는 팔로워 중 한 명 (팔로워, followers)
        - 바뀌어도 상관 없으나 관계 조회 시 생각하기 편한 방향으로 정한 것
    2. Migrations 진행 후 중개 테이블 확인
    3. url 작성
        ```python
        # accounts/urls.py
        urlpatterns = [
            ...
            path('<int:user_pk>/follow/', views.follow, name='follow'),
        ]
        ```
    4. view 함수 작성
        ```python
        # accounts/views.py
        @login_required
        def follow(request, user_pk):
            User = get_user_model()
            person = User.objects.get(pk=user_pk)
            if person != request.user:
                if request.user in person.followers.all():
                    person.followers.remove(request.user)
                else:
                    person.followers.add(request.user)
            return redirect('accounts:profile', person.username)
        ```
    5. 프로필 유저의 팔로잉, 팔로워 수 & 팔로우, 언팔로우 버튼 작성
        ```html
        <div>
            팔로잉 : {{person.followings.all|length}} / 팔로워 : {{person.followers.all|length}}
        </div>
        {% if request.user != person %}
            <div>
                <form action="{% url "accounts:follow" person.pk%}" method='POST'>
                    {% csrf_token %}
                    {% if request.user in person.followers.all %}
                        <input type="submit" value='Unfollow'>
                    {% else %}
                        <input type="submit" value='Follow'>
                    {% endif %}
                </form>
            </div>
        {% endif %}
        ```
    6. 팔로우 버튼 클릭 후 팔로우 버튼 변화 및 중개 테이블 데이터 확인
---
## 참고
1. `.exists()`
    - QuerySet에 결과가 포함되어 있으면 `True`를 반환하고 결과가 포함되어 있지 않으면 `False`를 반환
    - 큰 QuerySet에 있는 특정 객체 검색에 유용
2. `.exists()` 적용 예시
    1. like 함수
        - 적용 전
            ```python
            # articles/views.py
            def likes(request, article_pk):
                article = Article.objects.get(pk=article_pk)
                if request.user in article.like_users.all():
                    article.like_users.remove(request.user)
                else:
                    article.like_users.add(request.user)
                return redirect('articles:index')
            ```
        - 적용 후
            ```python
            # articles/views.py
            def likes(request, article_pk):
                article = Article.objects.get(pk=article_pk)
                if article.like_users.filter(pk=request.user.pk).exists():
                    article.like_users.remove(request.user)
                else:
                    article.like_users.add(request.user)
                return redirect('articles:index')
            ```
    2. follow 함수
        - 적용 전
            ```python
            # accounts/views.py
            @login_required
            def follow(request, user_pk):
                User = get_user_model()
                person = User.objects.get(pk=user_pk)
                if person != request.user:
                    if request.user in person.followers.all():
                        person.followers.remove(request.user)
                    else:
                        person.followers.add(request.user)
                return redirect('accounts:profile', person.username)
            ```
        - 적용 후
            ```python
            # accounts/views.py
            @login_required
            def follow(request, user_pk):
                User = get_user_model()
                person = User.objects.get(pk=user_pk)
                if person != request.user:
                    if person.followers.filter(pk=request.user.pk).exists():
                        person.followers.remove(request.user)
                    else:
                        person.followers.add(request.user)
                return redirect('accounts:profile', person.username)
            ```
---
## Fixtures
1. Fixtures
    - Django가 데이터베이스로 가져오는 방법을 알고 있는 데이터 모음
        - 데이터베이스 구조에 맞추어 작성 되어있음
2. 초기 데이터 제공
    - Fixtures의 사용 목적
3. 초기 데이터의 필요성
    - 협업 하는 유저 A, B가 있다고 생각해 보기
        1. A가 먼저 프로젝트를 작업 후 github에 push
            - .gitignore 로 인해 DB는 업로드하지 않기 때문에 A가 생성한 데이터도 업로드X
        2. B가 github에서 A가 push한 프로젝트를 pull(혹은 clone)
            - 결과적으로 B는 DB가 없는 프로젝트를 받게 됨
    - 이처럼 Django 프로젝트의 앱을 처음 설정할 때 동일하게 준비 된 데이터로 데이터베이스를 미리 채우는 것이 필요한 순간이 있음
    - fixtures를 사용해 앱에 초기 데이터(initial data)를 제공
---
### Fixtuers 활용
1. 사전 준비
    - M:N 까지 모두 작성된 Django 프로젝트에서 유저, 게시글, 댓글 등 각 데이터를 최소 2~3개 이상 생성해두기
2. fixtures 관련 명령어
    1. `dumpdata` - 생성 (데이터 추출)
    2. `loaddata` - 로드 (데이터 입력)
3. `dumpdata`
    - 데이터베이스의 모든 데이터를 추출
    - 추출한 데이터는 json 형식으로 저장
    - 작성 예시
        ```shell
        $ python manage.py dumpdata [app_name[.ModelName][app_name[.ModelName]..]] > filename.json
        ```
4. `dumpdata 활용`
    ```shell
    $ python manage.py dumpdata --indent 4 articles.article > articles.json
    ```
    ```shell
    $ python manage.py dumpdata --indent 4 accounts.user > users.json
    $ python manage.py dumpdata --indent 4 articles.comment > comments.json
    ```
5. `loaddata`
    - Fixtures 데이터를 데이터베이스로 불러오기
6. Fixtures 파일 기본 경로
    - `app_name/fixtures`
    - Django는 설치된 모든 app의 디렉토리에서 fixtures 폴더 이후의 경로로 fixtures 파일을 찾아 load
7. `loaddata` 활용
    1. db.sqlite3 파일 삭제 후 migrate 진행
        ```python
        # 해당 위치로 fixture 파일 이동
        articles/
            fixture/
                articles.json
                users.json
                comments.json
        ```
    2. load 후 데이터가 잘 입력되었는지 확인
        ```shell
        $ python manage.pt loaddata articles.json users.json comments.json
        ```
8. `loaddata` 순서 주의사항
    1. 만약 `loaddata`를 한번에 실행하지 않고 하나씩 실행한다면 모델 관계에 따라 load 하는 순서가 중요할 수 있음
        - comment는 article에 대한 key 및 user에 대한 key가 필요
        - article은 user에 대한 key가 필요
    2. 즉, 현재 모델 관계에서는 user -> article -> comment 순으로 data를 넣어야 오류가 발생하지 않음
    ```shell
    $ python manage.pt loaddata users.json
    $ python manage.pt loaddata articles.json
    $ python manage.pt loaddata comments.json
    ```
---
## 참고
1. 모든 모델을 한번에 dump 하기
    ```shell
    $ python manage.py dumpdata --indent 4 articles.article articles.comment accounts.user > data.json
    ```

    ```shell
    $ python manage.py dumpdata --indent 4 > data.json
    ```

2. loaddata 시 encoding codec 관련 에러가 발생하는 경우
- 2가지 방법 중 택 1
    1. dumpdata시 추가 옵션 작성
        ```shell
        $ python -Xutf8 manage.pt dumpdata [생략]
        ```
    2. 메모장 활용
        1. 메모장으로 json 파일 열기
        2. "다른 이름으로 저장" 클릭
        3. 인코딩을 UTF8로 선택 후 저장
    ### Fixtures 파일을 직접 만들지 말 것
    - 반드시 dumpdata 명령어를 사용하여 생성
---
## 쿼리 개선
### 사전 준비
1. Improve query
    - 같은 결과를 얻기 위해 DB 측에 보내는 쿼리 개수를 점차 줄여 조회하기
2. 사전 준비
    - 데이터
        - 게시글 10개 / 댓글 100개 / 유저 5개
    - 모델 관계
        - N:1 - Article:User / Comment:Article / Comment:Article
        - N:M - Aritlce:User
    ```shell
    $ python manage.ppy migrate
    $ python manage.py loaddata users.json articles.json comments.json
    ```
3. 서버 확인
---
### `annotate`
### `select_related`
### `prefetch_related`
### `select_related_prefetch_related`
---