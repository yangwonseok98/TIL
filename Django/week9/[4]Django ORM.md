# Django ORM

---

## INDEX

> **INDEX**
> 
> 1. ORM
> 2. QuerySet API
> 3. QuerySet API 실습
>     - Create
>     - Read
>     - Update
>     - Delete

---

## ORM

> **ORM**
> 
> - ORM [Object-Relational-Mapping]
>     - 객체 지향 프로그래밍 언어를 사용하여
>     호환되지 않는 유형의 시스템 간에 데이터를 변환하는 기술
> 
> - ORM의 역할
>     
>     ![Untitled](Django%20ORM%20img/Untitled.png)
>     

---

## QuerySet API

> **QuerySet API**
> 
> - QuerySet API
>     - ORM에서 데이터를 검색, 필터링, 정렬 및 그룹화 하는데 사용하는 도구
>     - API를 사용하여 SQL이 아닌 Python 코드로 데이터를 처리
>     
>     ![Untitled](Django%20ORM%20img/Untitled%201.png)
>     
> - QuerySet API 구문
>     - ex)
>         
>         `<Model class>.<Manager><QuerysetAPI>`
>         
>         `Article.objects.all()`
>         
> 
> - Query
>     - 데이터베이스에 특정한 데이터를 보여 달라는 요청
>     - “쿼리문을 작성한다.”
>     → 원하는 데이터를 얻기 위해 데이터베이스에 요청을 보낼 코드를 작성한다.
>     - 파이썬으로 작성한 코드가 ORM에 의해 SQL로 변환되어 데이터베이스에 전달되며, 데이터베이스의 응답 데이터를 ORM이 QuerySet이라는 자료 형태로 변환하여 우리에게 전달
>     
> - QuerySet
>     - 데이터베이스에게서 전달 받은 객체 목록(데이터 모음)
>         - 순회가 가능한 데이터로써 1개 이상의 데이터를 불러와 사용할 수 있음
>     - Django ORM을 통해 만들어진 자료형
>     - 단, 데이터베이스가 단일한 객체를 반환 할 때는 
>     QuerySet이 아닌 모델(Class)의 인스턴스로 반환 됨
>     
> - **Python의 모델 클래스와 인스턴스를 활용해
> DB에 데이터를 저장, 조회, 수정, 삭제하는 것**

---

## QuerySet API 실습

### Create

> **Create**
> 
> - QuerySet API 실습 사전 준비
>     - 외부 라이브러리 설치 및 설정
>         
>         `$ pip install ipython`
>         
>         `$ pip install django-extensions`
>         
>         - 프로젝트 내부의 [settings.py](http://settings.py) 파일에 INSTALLED_APPS 에 ‘django_extensions’ 추가
>             
>             ```python
>             # settings.py
>             
>             INSTALLED_APPS = [
>             	'articles',
>             	'django_extensions',
>             	...,
>             ]
>             ```
>             
>         
>         `$ pip freeze > requirements.txt`
>         
> 
> - Django shell
>     - Django 환경 안에서 실행되는 python shell
>         
>         (입력하는 QuerySet API 구문이 Django 프로젝트에 영향을 미침)
>         
> 
> - Django shell 실행
>     
>     `$ python manage.py shell_plus`
>     
> - 객체를 데이터베이스에 저장하는 메서드
>     
>     `save()`
>     
> - 데이터 객체를 만드는(생성하는) 3가지 방법
>     - 첫 번째 방법
>         
>         ```python
>         # 특정 테이블에 새로운 행을 추가하여 데이터 추가
>         >>> articles = Article() # Article(class)로부터 article(instance) 생성
>         >>> article
>         <Article: Article object (None)>
>         
>         >>> article.title = 'first' # 인스턴수 변수(title)에 값을 할당
>         >>> article.content = 'django!' # 인스턴스 변수(content)에 값을 할당
>         
>         # save를 하지 않으면 아직 DB에 값이 저장되지 않음
>         >>> article
>         <Article: Article object (None)>
>         
>         >>> Article.objects.all()
>         <QuerySet []>
>         
>         # save를 호출하고 확인하면 저장된 것을 확인할 수 있다.
>         >>> article.save()
>         >>> article
>         <Article: Article object (1)>
>         >>> article.id
>         1
>         >>> article.pk
>         1
>         >>> Article.objects.all()
>         <QuerySet [Article: Article object (1)]>
>         
>         # 인스턴스 article을 활용하여 인스턴스 변수 활용하기
>         >>> article.title
>         'first'
>         >>> article.content
>         'django!'
>         >>> article.created_at
>         datetime.datetime(2023, 6, 30, 6, 55, 42, 322526, tzinfo=datetime.timezone.utc)
>         ```
>         
>     - 두 번째 방법
>         - save 메서드를 호출해야 비로소 DB에 데이터가 저장 됨
>         - 테이블에 한 줄(행, 레코드)이 쓰여진 것
>         
>         ```python
>         >>> article = Article(title='second', content='django!')
>         
>         # 아직 저장되지 않음
>         >>> article
>         <Article: Article object (None)>
>         
>         # save를 호출해야 저장됨
>         >>> article.save()
>         >>> article
>         <Article: Article object (2)>
>         >>> Article.objects.all()
>         <QuerySet [<Article: Article object (1)>, <Article: Article object (2)>]>
>         
>         # 값 확인
>         >>> article.pk
>         2
>         >>> article.title
>         'second'
>         >>> article.content
>         'django!'
>         ```
>         
>     - 세 번째 방법
>         - QuerySet API 중 create() 메서드 활용
>         
>         ```python
>         # 위 2가지 방법과 달리 바로 저장 이후 바로 생성된 데이터가 반환된다.
>         >>> Article.objects.create(title='third', content='django!')
>         <Article: Article object (3)>
>         ```
>         

---

### Read

> **Read**
> 
> - 전체 데이터 조회
>     
>     `all()`
>     
>     ```python
>     >>> Article.objects.all()
>     <QuerySet [<Article: Article object (1)>, <Article: Article object (2)>]>
>     
>     ```
>     
> 
> - 단일 데이터 조회
>     
>     `get()`
>     
>     ```python
>     >>> Article.objects.get(pk=1)
>     <Article: Article object (1)>
>     
>     >>> Article.objects.get(pk=100)
>     DoesNotExist: Article matching query does not exist.
>     
>     >>> Article.objects.get(content='django!')
>     MultipleObjectsReturned: get() returned more than one Article -- it returned 2!
>     ```
>     
>     - get() 특징
>         - 객체를 찾을 수 없다면 DoesNotExist 예외를 발생 시키고,
>         둘 이상의 객체를 찾으면 MultipleObjectsReturned 예외를 발생 시킴
>         - 위와 같은 특징을 가지고 있기 때문에 **Primary Key와 같이
>         고유성(uniqueness)을 보장하는 조회에서 사용**해야 함
> 
> - 특정 조건 데이터 조회
>     
>     `filter()`
>     
>     ```python
>     >>> Article.objects.filter(content)
>     <QuerySet [<Article: Article object (1)>, <Article: Article object (2)>]>
>     
>     >>> Articles.objects.filter(titile='abc')
>     <QuerySet []>
>     
>     >>> Articles.objects.filter(title='first')
>     <QuerySet [<Article: Article object (1)>]>
>     ```
>     

---

### Update

> **Update**
> 
> - 데이터 수정
>     - 인스턴스 변수를 변경 후 save 메서드 호출
>     
>     ```python
>     # 수정할 인스턴스 조회
>     >>> article = Article.objects.get(pk=1)
>     
>     # 인스턴스 변수를 변경
>     >>> article.title = 'byebye'
>     
>     # 저장
>     >>> article.save()
>     
>     # 정상적으로 변경된 것을 확인
>     >>> article.title
>     'byebye'
>     ```
>     

---

### Delete

> **Delete**
> 
> - 데이터 삭제
>     - 삭제하려는 데이터 조회 후 delete 메서드 호출
>     
>     ```python
>     # 삭제할 인스턴스 조회
>     >>> article = Articles.objects.get(pk=1)
>     
>     # delete 메서드 호출 (삭제 된 객체가 반환)
>     >>> article.delete()
>     (1, {'articles.Article' : 1})
>     
>     # 삭제한 데이터는 더이상 조회할 수 없음
>     >>> Article.objects.get(pk=1)
>     DoesNotExist: Article matching query does not exist.
>     ```
>     

---

## 참고

> **참고**
> 
> - Field lookups
>     - 특정 레코드에 대한 조건을 설정하는 방법
>     - QuerySet 메서드 filter(), exclude() 및 get()에 대한 키워드 인자로 지정됨
>         - [https://docs.djangoproject.com/en/4.2/ref/models/querysets/ -field-lookups](https://docs.djangoproject.com/en/4.2/ref/models/querysets/)
>     
>     ```python
>     # Field lookups 예시
>     
>     # "content 컬럼에 'dja'가 포함된 모든 데이터 조회"
>     >>> Article.objects.filter(content__contains='dja')
>     ```
>     
> - ORM, QuerySet API를 사용하는 이유
>     - 데이터 베이스 쿼리를 추상화하여 Django 개발자가 데이터 베이스와 직접 상호작용 하지 않아도 되도록 함
>     - 데이터 베이스와의 결합도를 낮추고 개발자가 더욱 직관적이고 생산적으로 개발할 수 있도록 도움
> 
> - QuerySet API 관련 문서
>     - [https://docs.djangoproject.com/en/4.2/ref/models/querysets/](https://docs.djangoproject.com/en/4.2/ref/models/querysets/)
>     - [https://docs.djangoproject.com/en/4.2/topics/db/queries/](https://docs.djangoproject.com/en/4.2/topics/db/queries/)

---