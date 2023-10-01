# Django Model

---

## INDEX

> **INDEX**
> 
> 1. Model
> 2. Migrations
> 3. Admin site

---

## Model

> **Model**
> 
> - Model 을 통한 DB(데이터베이스) 관리
>     
>     ![Untitled](Django%20Model%20img/Untitled.png)
>     
> 
> - Django Model
>     - DB의 테이블을 정의하고 데이터를 조작할 수 있는 기능들을 제공
>     - 테이블 구조를 설계하는 ‘청사진(blueprint)’
> 
> - model 클래스 작성
>     
>   ```python
>   # articles/models.py
>   from django.db import models
>   
>   # Create your models here.
>   class Article(models.Model):
>       title = models.CharField(max_length=10)
>       content = models.TextField()
>   ```
>     
> - model 클래스 살펴보기
>     - 작성한 모델 클래스는 최종적으로 DB에 테이블 구조를 만듦
>     - `django.db.models` 모듈의 Model 이라는 부모 클래스를 상속 받음
>     - Model은 model에 관련된 모든 코드가 이미 작성 되어있는 클래스
>         - [https://github.com/django/django/blob/main/django/db/models/base.py#L459](https://github.com/django/django/blob/main/django/db/models/base.py#L459)
>     - 개발자는 가장 중요한 테이블 구조를 어떻게 설계할 지에 대한 코드만 작성하도록 하기 위한 것 (프레임워크의 이점)
>     
>     - 클래스 변수 명
>         - 테이블의 각 “필드(열) 이름”
>
>         - `title`
>         - `content`
>         
>     - model Field 클래스
>         - 테이블 필드의 “데이터 타입”
>         - [https://docs.djangoproject.com/en/4.2/ref/models/fields/](https://docs.djangoproject.com/en/4.2/ref/models/fields/)
>         
>         - `models.CharField()`
>         - `models.TextField()`
>         
>     - model Field 클래스의 키워드 인자 (필드 옵션)
>         - 테이블 필드의 “제약 조건” 관련 설정
>         - [https://docs.djangoproject.com/en/4.2/ref/models/fields/#field-options](https://docs.djangoproject.com/en/4.2/ref/models/fields/#field-options)
>         
>         - `max_length = 10`
>         
> - 제약 조건
>     - 데이터가 올바르게 저장되고 관리되도록 하기 위한 규칙
>     - ex) 숫자만 저장되도록, 문자가 100자 까지만 저장되도록 하는 등

---

## Migrations

> **Migrations**
> 
> - Migrations
>     - model 클래스의 변경 사항(필드 생성, 수정 삭제 등)을 DB에 최종 반영하는 방법
> 
> - Migrations 과정
>     
>     ![Untitled](Django%20Model%20img/Untitled%207.png)
>     
> - Migrations 핵심 명렁어 2가지
>     - `python [manage.py](http://manage.py) makemigrations`
>         - model class를 기반으로 최종 설계도(migration)작성
>     - `python [manage.py](http://manage.py) migrate`
>         - 최종 설계도롤 DB에 전달하여 반영
> 
> - migrate 후 DB 내에 생성 된 테이블 확인
>     - Article 모델 클래스로 만들어진 articles_article 테이블
>         
>         ![Untitled](Django%20Model%20img/Untitled%208.png)
>         

---

### 추가 Migrations

> **추가 Migrations**
> 
> - 이미 생성된 테이블에 필드를 추가해야 한다면?
>     
>     ![Untitled](Django%20Model%20img/Untitled%209.png)
>     
> - 추가 모델 필드 작성
>     
>     ![Untitled](Django%20Model%20img/Untitled%2010.png)
>     
>     - 이미 기존 테이블이 존재하기 때문에 필드를 추가 할 때 필드의 기본 값 설정이 필요
>     - **1번은 현재 대화를 유지하면서 직접 기본 값을 입력하는 방법**
>     - 2번은 현재 대화에서 나간 후 models.py에 기본 값 관련 설정을 하는 방법
>         - `python [manage.py](http://manage.py) makemigrations`
>         
>         ![Untitled](Django%20Model%20img/Untitled%2011.png)
>         
>     - 추가하는 필드의 기본 값을 입력해야 하는 상황
>     - 날짜 데이터이기 때문에 직접 입력하기 보다 Django가 제안하는 기본 값을 사용하는 것을 권장
>     - 아무것도 입력하지 않고 enter를 누르면 Django가 제안하는 기본 값으로 설정 됨
>         
>         ![Untitled](Django%20Model%20img/Untitled%2012.png)
>         
>     - mirations 과정 종료 후 2번째 migration 파일이 생성됨을 확인
>     - 이처럼 Django는 설계도를 쌓아가면서 추후 문제가 생겼을 시 복구하거나 되돌릴 수 있도록 함 (마치 ‘git commit’)
>         
>         ![Untitled](Django%20Model%20img/Untitled%2013.png)
>         
>     
>     - migrate 후 테이블 필드 변화 확인
>         - `python [manage.py](http://manage.py) migrate`
>         
>         ![Untitled](Django%20Model%20img/Untitled%2014.png)
>         
> - **model class에 변경사항(1)**이 생겼다면,
> 반드시 **새로운 설계도를 생성(2)**하고,
> 이를 **DB에 반영(3)**해야 한다.
>     
>     **1.model class 변경 → 2.make migrations → 3.migrate**
>     

---

### 모델 필드

> **모델 필드**
> 
> - Model Field
>     - DB 테이블의 필드(열)을 정의하며,
>     해당 필드에 저장되는 데이터 타입과 제약 조건을 정의
> 
> - `CharField()`
>     - 길이의 제한이 있는 문자열을 넣을 때 사용
>     (필드의 최대 길이를 결정하는 `max_length` 는 필수 인자)
>     
> - `TextField()`
>     - 글자의 수가 많을 때 사용
> 
> - `DataTimeField()`
>     - 날짜와 시간을 넣을 때 사용
>     - `DataTimeField`의 선택 인자
>         - `auto_now`
>             - 데이터가 **저장될 때마다** 자동으로 현재 날짜 시간을 저장
>         - `auto_now_add`
>             - 데이터가 **처음 생성될 때만** 자동으로 현재 날짜 시간을 저장

---

## Admin site

> **Admin site**
> 
> - Automatic admin interface
>     - Django는 추가 설치 및 설정 없이 자동으로 관리자 인터페이스를 제공
>     - 데이터 확인 및 테스트 등을 진행하는데 매우 유용
> 
> - admin 계정 생성
>     - email은 선택사항이기 때문에 입력하지 않고 진행 가능
>     - 비밀번호 입력 시 보안 상 터미널에 출력 되지 않으니 무시하고 입력 이어가기
>     
>     `$ python [manage.py](http://manage.py) createsuperuser`
>     
> 
> - DB에 생성된 admin 계정 확인
>     
>     ![Untitled](Django%20Model%20img/Untitled%2015.png)
>     
> - admin에 모델 클래스 등록
>     - admin.py에 작성한 모델 클래스를 등록해야만 admin site에서 확인 가능
>     
>       ```python
>       from django.contrib import admin
>       from .models import Article
>       # Register your models here.
>       admin.site.register(Article)
>       ```
>     
> - admin site 로그인 후 등록된 모델 클래스 확인
>     
>     ![Untitled](Django%20Model%20img/Untitled%2017.png)
>     
> - 데이터 생성, 수정, 삭제 테스트
>     
>     ![Untitled](Django%20Model%20img/Untitled%2018.png)
>     
> - 테이블 확인
>     
>     ![Untitled](Django%20Model%20img/Untitled%2019.png)
>     

---

## 참고

> **참고**
> 
> - 데이터 베이스 초기화
>     1. Migration 파일 삭제
>     2. db.sqlite3 파일 삭제
>     - 아래 파일과 폴더를 지우지 않도록 주의
>         - `__init__.py`
>         - `migrations 폴더`
>     
>     ![Untitled](Django%20Model%20img/Untitled%2020.png)
>     
> 
> - Migrations 기타 명령어
>     - `$ python manage.py showmigrations`
>         - migrations 파일들이 migrate 됐는지 안됐는지 여부를 확인하는 명령어
>         - [X] 표시가 있으면 migrate가 완료되었음을 의미
>     - `$ python manage.py sqlmigrate articles 0001`
>         - 해당 migrations 파일이 SQL 언어(DB에서 사용하는 언어)로
>         어떻게 번역되어 DB에 전달되는지 확인하는 명령어
>         
> - 첫 migrate 시 출력 내용이 많은 이유는?
>     - Django 프로젝트가 동작하기 위해 미리 작성 되어있는 기
>     본 내장 app들에 대한 migration 파일들이 함께 migrate 되기 때문
>         
>         ![Untitled](Django%20Model%20img/Untitled%2021.png)
>         
> - SQLite
>     
>     ![Untitled](Django%20Model%20img/Untitled%2022.png)
>     
>     - 데이터베이스 관리 시스템 중 하나이며Django의 기본 데이터베이스로 사용됨
>     (파일로 존재하며 가볍고 호환성이 좋음)
>     
> - CRUD
>     - 소프트웨어가 가지는 기본적인 데이터 처리 기능
>     - Create (저장), Read (조회), Update (갱신), Delete (삭제)

---