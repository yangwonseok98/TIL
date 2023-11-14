# Vue with DRF 1

---

# INDEX

### 1. 프로젝트 개요

### 2. 메인 페이지 구현

### 3. CORS Policy

### 4. Article CR 구현

---

# 1. 프로젝트 개요

---

## DRF 프로젝트 안내

### 1. DRF 프로젝트 안내

- 스켈레톤 프로젝트 django-pjt 제공
- 외부 패키지 및 라이브러리는 requirements.txt에 작성되어 있음
- DRF 프로젝트는 주석을 해제하며 진행

### 2. Skeleton code 살펴보기

1. Model 클래스 확인

   ```python
    # articles/models.py

    from django.db import models
    from django.conf import settings


    class Article(models.Model):
        # user = models.ForeignKey(
        #     settings.AUTH_USER_MODEL, on_delete=models.CASCADE
        # )
        title = models.CharField(max_length=100)
        content = models.TextField()
        created_at = models.DateTimeField(auto_now_add=True)
        updated_at = models.DateTimeField(auto_now=True)
   ```

   ```python
   # accounts/models.py

   from django.db import models
   from django.contrib.auth.models import AbstractUser


   # Create your models here.
   class User(AbstractUser):
       pass

   ```

2. URL 확인

   ```python
   # my_api.urls.py

   from django.contrib import admin
   from django.urls import path, include


   urlpatterns = [
       path('admin/', admin.site.urls),
       path('api/v1/', include('articles.urls')),
       # path('accounts/', include('dj_rest_auth.urls')),
       # path('accounts/signup/', include('dj_rest_auth.registration.urls')),
   ]
   ```

   ```python
    # articles/url.py

    from django.urls import path
    from . import views


    urlpatterns = [
        path('articles/', views.article_list),
        path('articles/<int:article_pk>/', views.article_detail),
    ]
   ```

3. Serializers 확인

   ```python
   # articles/serializers.py

   from rest_framework import serializers
   from .models import Article


   class ArticleListSerializer(serializers.ModelSerializer):
       class Meta:
           model = Article
           fields = ('id', 'title', 'content')


   class ArticleSerializer(serializers.ModelSerializer):
       class Meta:
           model = Article
           fields = '__all__'
           # read_only_fields = ('user',)
   ```

4. views.py import 부분 확인

   ```python
   # articles/views.py

   from rest_framework.response import Response
   from rest_framework.decorators import api_view
   from rest_framework import status

   # permission Decorators
   # from rest_framework.decorators import permission_classes
   # from rest_framework.permissions import IsAuthenticated

   from django.shortcuts import get_object_or_404, get_list_or_404

   from .serializers import ArticleListSerializer, ArticleSerializer
   from .models import Article
   ```

5. view 함수 확인

   ```python
    # articles/views.py
    @api_view(['GET', 'POST'])
    # @permission_classes([IsAuthenticated])
    def article_list(request):
        if request.method == 'GET':
            articles = get_list_or_404(Article)
            serializer = ArticleListSerializer(articles, many=True)
            return Response(serializer.data)

        elif request.method == 'POST':
            serializer = ArticleSerializer(data=request.data)
            if serializer.is_valid(raise_exception=True):
                serializer.save()
                # serializer.save(user=request.user)
                return Response(serializer.data, status=status.HTTP_201_CREATED)


    @api_view(['GET'])
    def article_detail(request, article_pk):
        article = get_object_or_404(Article, pk=article_pk)

        if request.method == 'GET':
            serializer = ArticleSerializer(article)
            print(serializer.data)
            return Response(serializer.data)
   ```

6. settings.py 확인

   ```python
   INSTALLED_APPS = [
       'articles',
       'accounts',
       'rest_framework',
       # 'rest_framework.authtoken',
       # 'dj_rest_auth',
       # 'corsheaders',
       # 'django.contrib.sites',
       # 'allauth',
       # 'allauth.account',
       # 'allauth.socialaccount',
       # 'dj_rest_auth.registration',
       'django.contrib.admin',
       'django.contrib.auth',
       'django.contrib.contenttypes',
       'django.contrib.sessions',
       'django.contrib.messages',
       'django.contrib.staticfiles',
   ]

   # SITE_ID = 1

   # REST_FRAMEWORK = {
   #     # Authentication
   #     'DEFAULT_AUTHENTICATION_CLASSES': [
   #         'rest_framework.authentication.TokenAuthentication',
   #     ],
   #     # permission
   #     'DEFAULT_PERMISSION_CLASSES': [
   #         'rest_framework.permissions.AllowAny',
   #     ],
   # }

   MIDDLEWARE = [
       'django.middleware.security.SecurityMiddleware',
       'django.contrib.sessions.middleware.SessionMiddleware',
       # 'corsheaders.middleware.CorsMiddleware',
       'django.middleware.common.CommonMiddleware',
       'django.middleware.csrf.CsrfViewMiddleware',
       'django.contrib.auth.middleware.AuthenticationMiddleware',
       'django.contrib.messages.middleware.MessageMiddleware',
       'django.middleware.clickjacking.XFrameOptionsMiddleware',
   ]

   # CORS_ALLOWED_ORIGINS = [
   #     'http://127.0.0.1:5173',
   #     'http://localhost:5173',
   # ]
   ```

7. Fixtures 확인

   ```json
   // articles/fixtures/articles.json

   [
     {
       "model": "articles.article",
       "pk": 1,
       "fields": {
         "title": "title",
         "content": "content",
         "created_at": "2023-07-04T08:21:53.976Z",
         "updated_at": "2023-07-04T08:21:53.976Z"
       }
     },
     {
       "model": "articles.article",
       "pk": 2,
       "fields": {
         "title": "제목",
         "content": "내용",
         "created_at": "2023-07-04T12:59:07.671Z",
         "updated_at": "2023-07-04T12:59:07.671Z"
       }
     },
     {
       "model": "articles.article",
       "pk": 3,
       "fields": {
         "title": "제목",
         "content": "내용",
         "created_at": "2023-07-04T13:04:08.680Z",
         "updated_at": "2023-07-04T13:04:08.680Z"
       }
     }
   ]
   ```

8. 가상 환경 생성 및 활성화

   ```source
   $ python -m venv venv
   $ source venv/Scripts/activate
   ```

9. 패키지 설치

   ```source
   $ pip install -r requirements.txt
   ```

10. Migration 진행
    ```source
    $ python manage.py makemigrations
    $ python manage.py migrate
    ```
11. Fixtures 데이터 로드
    ```source
    $ python manage.py loaddata articles.json
    ```
12. Django 서버 실행 후, 전체 게시글 조회

- http://127.0.0.1:8000/api/v1/articles/

---

## Vue 프로젝트 안내

### 1. Vue 프로젝트 안내

- 스켈레톤 프로젝트 vue-pjt 제공
- Vite를 사용해 Pinia 및 Vue Router가 추가 되어있음
- pinia-plugin-persistedstate가 설치 및 등록 되어있음
- Vue 프로젝트는 직접 코드를 작성하며 진행

- 컴포넌트 구조
  - App
    - ArticleView
      - ArticleList
      - ArticleListItem
    - DetailView
    - CreateView
    - SignUpView
    - LoginView

### 2. Skeleton code 살펴보기

1. App 컴포넌트

   ```html
   <!-- App.vue -->

   <template>
     <header>
       <nav></nav>
     </header>
     <RouterView />
   </template>

   <script setup>
     import { RouterView } from "vue-router";
   </script>

   <style scoped></style>
   ```

2. route에 등록된 컴포넌트 (Article, Create, Detail, Login, SignUp)

   ```html
   <!-- views/ ....vue -->

   <template>
     <div></div>
   </template>

   <script setup></script>

   <style></style>
   ```

3. ArticleList 컴포넌트

   ```html
   <!-- components/ArticleList.vue -->

   <template>
     <div>
       <h3>Article List</h3>
       <ArticleListItem />
     </div>
   </template>

   <script setup>
     import ArticleListItem from "@/components/ArticleListItem.vue";
   </script>
   ```

4. ArticleListItem 컴포넌트

   ```html
   <!-- components/ArticleListItem.vue -->

   <template>
     <div></div>
   </template>

   <script setup></script>
   ```

5. routes 현황

   ```js
   // router/index.js

   import { createRouter, createWebHistory } from 'vue-router'
   // import ArticleView from '@/views/ArticleView.vue'
   // import DetailView from '@/views/DetailView.vue'
   // import CreateView from '@/views/CreateView.vue'
   // import SignUpView from '@/views/SignUpView.vue'
   // import LogInView from '@/views/LogInView.vue'

   const router = createRouter({
     history: createWebHistory(import.meta.env.BASE_URL),
     routes: [
       // {
       //   path: '/',
       //   name: 'ArticleView',
       //   component: ArticleView
       // },
       ...
     ]
   })
   ```

6. store 현황

   ```js
   // store/counter.js

   import { ref, computed } from "vue";
   import { defineStore } from "pinia";

   export const useCounterStore = defineStore(
     "counter",
     () => {
       return {};
     },
     { persist: true }
   );
   ```

7. main.js

   ```js
   // src/main.js

   import piniaPluginPersistedstate from "pinia-plugin-persistedstate";
   import { createApp } from "vue";
   import { createPinia } from "pinia";
   import App from "./App.vue";
   import router from "./router";

   const app = createApp(App);
   const pinia = createPinia();

   pinia.use(piniaPluginPersistedstate);
   // app.use(createPinia())
   app.use(pinia);
   app.use(router);

   app.mount("#app");
   ```

8. 패키지 설치
   ```
   $ npm install
   ```
9. 서버 실행
   ```
   $ npm run dev
   ```

---

# 2. 메인 페이지 구현

---

### 1. 시작하기 전에..

- 무결점의 프로젝트를 만드는 것이 아님
- front-end 프레임워크와 back-end 프레임워크 간의 요청과 응답, 그 과정에서 등장하는 새로운 개념과 문제를 해결하면서 하나의 웹 애플리케이션 서비스를 구현하는 과정에 집중할 것

---

## state 참조 및 출력

### 1. 개요

- ArticleView 컴포넌트에 ArticleList 컴포넌트와 ArticleListItem 컴포넌트 등록 및 출력하기
- ArticleList와 ArticleListItem은 각각 게시글 출력을 담당

### 2. state 참조 및 출력

1. ArticleView route 관련 주석 해제

   ```js
   // router/index.js

   import { createRouter, createWebHistory } from 'vue-router'
   import ArticleView from '@/views/ArticleView.vue'
   // import DetailView from '@/views/DetailView.vue'
   // import CreateView from '@/views/CreateView.vue'
   // import SignUpView from '@/views/SignUpView.vue'
   // import LogInView from '@/views/LogInView.vue'

   const router = createRouter({
    history: createWebHistory(import.meta.env.BASE_URL),
    routes: [
      {
         path: '/',
         name: 'ArticleView',
         component: ArticleView
      },
      ...
    ]
   })
   ```

2. App컴포넌트에 ArticleView 컴포넌트로 이동하는 RouterLink 작성

   ```html
   <!-- App.vue -->

   <template>
     <header>
       <nav>
         <router-link :to="{ name: 'ArticleView' }">Aritlcles</router-link>
       </nav>
     </header>
     <RouterView />
   </template>

   <script setup>
     import { RouterView, RouterLink } from "vue-router";
   </script>

   <style scoped></style>
   ```

3. ArticleView 컴포넌트에 ArticleList 컴포넌트 등록

   ```html
   <!-- view/ArticleView.vue -->
   <template>
     <div>
       <h1>Article Page</h1>
       <ArticleList />
     </div>
   </template>

   <script setup>
     import ArticleList from "@/components/ArticleList.vue";
   </script>

   <style></style>
   ```

4. store에 임시 데이터 articles 배열 작성하기

   ```js
   // store/counter.js

   import { ref, computed } from "vue";
   import { defineStore } from "pinia";

   export const useCounterStore = defineStore(
     "counter",
     () => {
       const articles = ref([
         { id: 1, title: "Article 1", content: "Content of article 1" },
         { id: 2, title: "Article 2", content: "Content of article 2" },
       ]);
       return { articles };
     },
     { persist: true }
   );
   ```

5. ArticleList 컴포넌트에서 게시글 목록 출력

   - store의 articles 데이터 참조
   - v-for를 활용하여 하위 컴포넌트에서 사용할 article 단일 객체 정보를 props로 전달

   ```html
   <!-- components/ArticleList.vue -->

   <template>
     <div>
       <h3>Article List</h3>
       <ArticleListItem
         v-for="article in store.articles"
         :key="article.id"
         :article="article"
       />
     </div>
   </template>

   <script setup>
     import ArticleListItem from "@/components/ArticleListItem.vue";
     import { useCounterStore } from "@/stores/counter";

     const store = useCounterStore();
   </script>
   ```

6. ArticleListItem 컴포넌트는 내려 받은 props를 정의 후 출력

   ```html
   <!-- components/ArticleListItem.vue -->

   <template>
     <div>
       <h5>{{ article.id }}</h5>
       <p>{{ article.title }}</p>
       <p>{{ article.content }}</p>
       <hr />
     </div>
   </template>

   <script setup>
     defineProps({
       article: Object,
     });
   </script>
   ```

7. 메인 페이지 게시글 목록 출력 확인

---

## state with DRF

### 1. 개요

- 이제는 임시 데이터가 아닌 DRF 서버에 직접 요청하여 데이터를 응답 받아 store에 저장 후 출력하기

### 2. state with DRF

1. DRF 서버로의 AJAX 요청을 위한 axios 설치 및 관련 코드 작성

   ```py
   # Vue 서버 종료 -> 설치 -> 서버 재실행
   $ npm install axios
   ```

   ```js
   // store/counter.js

   import { ref, computed } from "vue";
   import { defineStore } from "pinia";
   import axios from "axios";

   export const useCounterStore = defineStore(
     "counter",
     () => {
       const articles = ref([]);
       const API_URL = "http://127.0.0.1:8000";
       return { articles };
     },
     { persist: true }
   );
   ```

2. DRF 서버로 요청을 보내고 응답 데이터를 처리하는 getArticles 함수 작성

   ```js
   // store/counter.js

   import { ref, computed } from "vue";
   import { defineStore } from "pinia";
   import axios from "axios";

   export const useCounterStore = defineStore(
     "counter",
     () => {
       const articles = ref([]);
       const API_URL = "http://127.0.0.1:8000";

       const getArticles = function () {
         axios({
           method: "get",
           url: `${API_URL}/api/v1/articles/`,
         })
           .then((res) => {
             console.log(res);
             console.log(res.data);
           })
           .catch((error) => console.log(error));
       };
       return { articles, API_URL, getArticles };
     },
     { persist: true }
   );
   ```

3. ArticleView 컴포넌트가 마운트 될 때 getArticles 함수가 실행되도록 함

   - 해당 컴포넌트가 렌더링 될 때 항상 최신 게시글 목록을 불러오기 위함

   ```html
   <!-- view/ArticleView.vue -->

   <template>
     <div>
       <h1>Article Page</h1>
       <ArticleList />
     </div>
   </template>

   <script setup>
     import ArticleList from "@/components/ArticleList.vue";
     import { onMounted } from "vue";
     import { useCounterStore } from "@/stores/counter";

     const store = useCounterStore();

     onMounted(() => {
       store.getArticles();
     });
   </script>

   <style></style>
   ```

4. Vue와 DRF 서버를 모두 실행한 후 응답 데이터 확인
   - 에러 발생
5. 그런데 DRF 서버 측에서는 문제없이 응답했음 (200 OK)
   - 서버는 응답했으나 브라우저 측에서 거절한 것
6. 브라우저가 거절한 이유
   ### 'http://localhost:5173'에 'http://127.0.0.1:8000/api/v1/articles/'의 XMLHttpRequest에 대한 접근이 CORS policy에 의해 차단 되었다.

---

# 3. CORS Policy

---

## CORS

### 1. SOP (Same-origin policy)

- 동일 출처 정책
- 어떤 출처(Origin)에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호 작용하는 것을 제한하는 보안 방식
  - https://developer.mozila.org/en-US/docs/Web/Security/Same-origin_policy
- 웹 애플리케이션의 도메인이 다른 도메인의 리소스에 접근하는 것을 제어하여 사용자의 개인 정보와 데이터의 보안을 보호하고, 잠재적인 보안 위협을 방지
- 잠재적으로 해로울 수 있는 문서를 분리함으로써 공격받을 수 있는 경로를 줄임

### 2. Origin (출처)

- URL의 Protocol, Host. Port를 모두 포함하여 "출처"라고 부름
- Same Origin 예시
  - 위의 Protocol, Host. Port가 모두 일치하는 경우에만 동일 출처(Same-origin)로 인정

### 3. CORS policy의 등장

- 기본적으로 웹 브라우저는 같은 출처에서만 요청하는 것을 허용하며, 다른 출처로의 요청은 보안상의 이유로 차단됨
  - SOP에 의해 다른 출처의 리소스와 상호작용 하는 것이 기본적으로 제한되기 때문
- 하지만 현대 웹 애플리케이션은 다양한 출처로부터 리소스를 요청하는 경우가 많기 때문에 CORS 정책이 필요하게 되었음
  ### CORS는 웹 서버가 리소스에 대한 서로 다른 출처 간 접근을 허용 하도록 선택할 수 있는 기능을 제공

### 4. CORS(Cross-Origin Resource Sharing)

- 교차 출처 리소스 공유
- 특정 출처(Origin)에서 실행 중인 웹 애플리케이션이 다른 출처의 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제
  ### 만약 다른 출처의 리소스를 가져오기 위해서는 이를 제공하는 서버가 브라우저에게 다른 출처지만 접근해도 된다는 사실을 알려야 함

### 5. CORS policy (교차 출처 리소스 공유 정책)

- 다른 출처에서 온 리소스를 공유하는 것에 대한 정책
- 서버에서 설정되며, 브라우저가 해당 정책을 확인하여 요청이 허용되는지 여부를 결정
- 다른 출처의 리소스를 불러오려면 그 출처에서 올바른 "CORS header"를 포함한 응답을 반환해야 함
- https://developer.mozilla.org/ko/docs/Web/HTTP/CORS

---

## CORS Headers 설정

### 1. CORS Headers 설정하기

- Django에서는 django-cors-headers 라이브러리를 활용
- 손쉽게 응답 객체에 CORS header를 추가해주는 라이브러리
- https://github.com/adamchainz/django-cors-headers

### 2. django-cors-headers 사용하기

1. 설치 (requirements.txt로 인해 사전에 설치되어 있음)
   ```
   $ pip install django-cors-headers
   ```
2. 관련 코드 주석 해제

   ```py
   # settings.py

   INSTALLED_APPS = [
        ...
        'corsheaders',
        ...
   ]

    MIDDLEWARE = [
        ...
        'corsheaders.middleware.CorsMiddleware',
        'django.middleware.common.CommonMiddleware',
        ...
    ]
   ```

3. CORS를 허용할 Vue 프로젝트의 Domain 등록

   ```py
   # settings.py

   CORS_ALLOWED_ORIGINS = [
       'http://127.0.0.1:5173',
       'http://localhost:5173',
   ]
   ```

### 3. CORS 처리 결과

1. 메인 페이지에서 DRF 응답 데이터 재확인
   - 정상
2. 응답 객체에서 `Access-Control-Allow-Origin` Header 확인
   - Network -> Fetch/XHR -> 응답객체 -> Response Headers -> `Access-Control-Allow-Origin`

---

# 4. Article CR 구현

---

## 전체 게시글 조회

### 1. 전체 게시글 목록 저장 및 출력

1. 응답 받은 데이터에서 각 게시글의 구조 확인 (id, title, content)

2. store에 게시글 목록 데이터 저장

   ```js
   // store/counter.js

   import { ref, computed } from "vue";
   import { defineStore } from "pinia";
   import axios from "axios";

   export const useCounterStore = defineStore(
     "counter",
     () => {
       const articles = ref([]);
       const API_URL = "http://127.0.0.1:8000";

       const getArticles = function () {
         axios({
           method: "get",
           url: `${API_URL}/api/v1/articles/`,
         })
           .then((res) => {
             articles.value = res.data;
           })
           .catch((error) => console.log(error));
       };
       return { articles, API_URL, getArticles };
     },
     { persist: true }
   );
   ```

3. store에 저장된 게시글 목록 출력 확인
   - pinia-plugin-persistedstate에 의해 브라우저의 Local Storage에 저장됨

---

## 단일 게시글 조회

### 1. 단일 게시글 데이터 출력

1. DetailVue 관련 route 주석 해제

   ```js
   // router/index.js

   import { createRouter, createWebHistory } from "vue-router";
   import ArticleView from "@/views/ArticleView.vue";
   import DetailView from "@/views/DetailView.vue";
   // import CreateView from '@/views/CreateView.vue'
   // import SignUpView from '@/views/SignUpView.vue'
   // import LogInView from '@/views/LogInView.vue'

   const router = createRouter({
     history: createWebHistory(import.meta.env.BASE_URL),
     routes: [
       {
         path: "/",
         name: "ArticleView",
         component: ArticleView,
       },
       {
         path: "/articles/:id",
         name: "DetailView",
         component: DetailView,
       },
     ],
   });
   ```

2. ArticleListItem에 DetailView 컴포넌트로 가기 위한 RouterLink 작성

   ```html
   <!-- components/ArticleListItem.vue -->

   <template>
     <div>
       <h5>{{ article.id }}</h5>
       <p>{{ article.title }}</p>
       <p>{{ article.content }}</p>
       <router-link :to="{ name: 'DetailView', params: { id: article.id } }"
         >[DETAIL]</router-link
       >
       <hr />
     </div>
   </template>

   <script setup>
     import { RouterLink } from "vue-router";
     defineProps({
       article: Object,
     });
   </script>
   ```

3. DetailView가 마운트 될 때 특정 게시글을 조회하는 AJAX 요청 진행

   ```html
   <!-- views/DetailView.vue -->

   <template>
     <div></div>
   </template>

   <script setup>
     import axios from "axios";
     import { onMounted } from "vue";
     import { useRoute } from "vue-router";
     import { useCounterStore } from "@/stores/counter";

     const store = useCounterStore();
     const route = useRoute();

     onMounted(() => {
       axios({
         method: "get",
         url: `${store.API_URL}/api/v1/articles/${route.params.id}/`,
       })
         .then((res) => {
           console.log(res.data);
         })
         .catch((err) => console.log(err));
     });
   </script>

   <style></style>
   ```

4. 응답 데이터 확인

   - 정상

5. 응답 데이터 저장 후 출력

   ```html
   <!-- views/DetailView.vue -->

   <template>
     <div>
       <h1>Detail</h1>
       <div v-if="article">
         <p>글 번호: {{ article.id }}</p>
         <p>제목 : {{ article.title }}</p>
         <p>내용 : {{ article.content }}</p>
         <p>작성시간 : {{ article.created_at }}</p>
         <p>수정시간 : {{ article.updated_at }}</p>
       </div>
     </div>
   </template>

   <script setup>
     import axios from "axios";
     import { onMounted, ref } from "vue";
     import { useRoute } from "vue-router";
     import { useCounterStore } from "@/stores/counter";

     const store = useCounterStore();
     const route = useRoute();
     const article = ref(null);

     onMounted(() => {
       axios({
         method: "get",
         url: `${store.API_URL}/api/v1/articles/${route.params.id}/`,
       })
         .then((res) => {
           article.value = res.data;
         })
         .catch((err) => console.log(err));
     });
   </script>

   <style></style>
   ```

6. 결과 확인
   - 정상

---

## 게시글 작성

### 1. 게시글 작성

1. CreateView 관련 route 주석 해제

   ```js
   // router/index.js

   import { createRouter, createWebHistory } from "vue-router";
   import ArticleView from "@/views/ArticleView.vue";
   import DetailView from "@/views/DetailView.vue";
   import CreateView from "@/views/CreateView.vue";
   // import SignUpView from '@/views/SignUpView.vue'
   // import LogInView from '@/views/LogInView.vue'

   const router = createRouter({
     history: createWebHistory(import.meta.env.BASE_URL),
     routes: [
       {
         path: "/",
         name: "ArticleView",
         component: ArticleView,
       },
       {
         path: "/articles/:id",
         name: "DetailView",
         component: DetailView,
       },
       {
         path: "/create",
         name: "CreateView",
         component: CreateView,
       },
     ],
   });
   ```

2. ArticleView에 CreateView 컴포넌트로 가기 위한 RouterLink 작성

   ```html
   <!-- view/ArticleView.vue -->

   <template>
     <div>
       <h1>Article Page</h1>
       <RouterLink :to="{ name: 'CreateView' }">[CREATE]</RouterLink>
       <ArticleList />
     </div>
   </template>

   <script setup>
     import ArticleList from "@/components/ArticleList.vue";
     import { onMounted } from "vue";
     import { useCounterStore } from "@/stores/counter";
     import { RouterLink } from "vue-router";
     const store = useCounterStore();

     onMounted(() => {
       store.getArticles();
     });
   </script>

   <style></style>
   ```

3. v-model을 사용해 사용자 입력 데이터를 양방향 바인딩

   - v-model의 trim 수식어를 사용해 사용자 입력 데이터의 공백을 제거

   ```html
   <!-- views/CreateView.vue -->

   <template>
     <div>
       <h1>게시글 작성</h1>
       <form>
         <label for="title">제목 : </label>
         <input type="text" id="title" v-model.trim="title" /><br />
         <label for="content"></label>
         <textarea id="content" v-model.trim="content"></textarea><br />
         <input type="submit" />
       </form>
     </div>
   </template>

   <script setup>
     import { ref } from "vue";
     const title = ref(null);
     const content = ref(null);
   </script>

   <style></style>
   ```

4. 양방향 바인딩 데이터 확인

   - 제목과 내용을 입력하면서 vue.extension을 통해 값이 입력되는 것을 확인

5. 게시글 생성 요청을 담당하는 createArticle 함수 작성

   - 게시글 생성이 성공한다면 ArticleView 컴포넌트로 이동

   ```html
   <!-- views/CreateView.vue -->

   <template>
     <div>
       <h1>게시글 작성</h1>
       <form>
         <label for="title">제목 : </label>
         <input type="text" id="title" v-model.trim="title" /><br />
         <label for="content">내용 : </label>
         <textarea id="content" v-model.trim="content"></textarea><br />
         <input type="submit" />
       </form>
     </div>
   </template>

   <script setup>
     import { ref } from "vue";
     import axios from "axios";
     import { useRouter } from "vue-router";
     import { useCounterStore } from "@/stores/counter";

     const title = ref(null);
     const content = ref(null);

     const router = useRouter();
     const store = useCounterStore();
     const createArticle = function () {
       axios({
         method: "POST",
         url: `${store.API_URL}/api/v1/articles/`,
         data: {
           title: title.value,
           content: content.value,
         },
       })
         .then(() => {
           router.push({ name: "ArticleView" });
         })
         .catch((err) => {
           console.log(err);
         });
     };
   </script>

   <style></style>
   ```

6. submit 이벤트가 발생하면 createArticle 함수를 호출

   - v-on의 prevent 수식어를 사용해 submit 이벤트의 기본 동작(새로고침) 취소

   ```html
   <!-- views/CreateView.vue -->

   <template>
     <div>
       <h1>게시글 작성</h1>
       <form @submit.prevent="createArticle">
         <label for="title">제목 : </label>
         <input type="text" id="title" v-model.trim="title" /><br />
         <label for="content">내용 : </label>
         <textarea id="content" v-model.trim="content"></textarea><br />
         <input type="submit" />
       </form>
     </div>
   </template>
   ```

7. 게시글 생성 결과 확인

   - 정상

8. 서버 측 DB 확인
   - django-project -> db.sqlite3 -> articles_article 확인
   - 정상

---
