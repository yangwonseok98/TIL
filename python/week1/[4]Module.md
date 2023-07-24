# Module

> INDEX
> 
> - 모듈
> - 모듈 활용
>     - 모듈 import
>     - 사용자 정의 모듈
> - 파이썬 표준 라이브러리

---

## 모듈

> 개요
> 
> - 과학자, 수학자가 모든 이론을 새로 만들거나 증명하지 않는 것처럼
>     
>     개발자 또한 프로그램 전체를 모두 혼자 힘으로 작성하는 것은 드문 일
>     
> - 이미 다른 프로그래머가 이미 작성해 놓은 수천, 수백만 줄의 코드를 사용하는 것은 생산성 에서 매우 중요한 일

> 모듈(Moudule)
> 
> - 한 파일로 묶인 변수와 함수의 모음
> - 특정한 기능을 하는 코드가 작성된 파이썬 파일(.py)

> 모듈 예시
> 
> - 파이썬의 math 모듈
> - 파이썬이 미리 작성해 둔 수학 관련 변수와 함수가 작성된 모듈
>     
>     ```python
>     import math
>     print(math.pi) # 3.141592653558979
>     print(math.sqrt(4)) # 2.0
>     ```
>     

---

## 모듈 활용

### 모듈 import

> 모듈 가져오기
> 
> - 모듈 내 변수와 함수에 접근하려면 **import** 문이 필요
>     
>     ```python
>     import math
>     ```
>     
> - 내장 함수 help를 사용해 모듈에 무엇이 들어있는지 확인 가능
>     
>     ```python
>     import math
>     help(math)
>     '''
>     NAME
>         math
>     
>     FUNCTIONS
>         acos(x)
>             acos(x)
>             
>             Return the arc cosine (measured in radians) of x.
>     				...
>     '''
>     ```
>     

> 모듈 사용하기
> 
> - ‘.(dot)’
>     - “점의 왼쪽 객체에서 점의 오른쪽 이름을 찾아라”라는 의미의 연산자
>         
>         ```python
>         import math
>         # 모듈명.변수명
>         print(math.pi)
>         # 모듈명.함수명
>         print(math.sqrt(4))
>         ```
>         

> 모듈을 import하는 다른 방법
> 
> - from 절을 활용해 특정 모듈을 미리 참조하고 어떤 요소를 import 할지 명시
>     
>     ```python
>     from math import pi, sqrt
>     print(pi)
>     print(sqrt(4))
>     ```
>     

> 모듈 주의사항
> 
> 
> ⇒ 만약 서로 다른 모듈이 같은 이름의 함수를 제공할 경우 문제 발생
> 
> - 마지막에 import된 이름으로 대체됨
>     
>     ```python
>     # 그래서 모듈 내 모든 요소를 한번에 import 하는 * 표기는 권장하지 않음
>     from math import *
>     
>     ```
>     

---

### 사용자 정의 모듈

> 직접 정의한 모듈 사용하기
> 
> 1. 모듈 my_math.py 작성
> 2. 두 수의 합을 구하는 add 함수 작성
> 3. my_math 모듈 import 후 add 함수 호출
>     
>     ```python
>     # my_math.py
>     def add(x, y):
>         return x + y
>     ```
>     
>     ```python
>     # main.py
>     import my_math
>     print(my_math.add(1, 2)) # 3
>     ```
>     

---

## 파이썬 표준 라이브러리

> 파이썬 표준 라이브러리 (Python Standard Library)
> 
> - 파이썬 언어와 함께 제공되는 다양한 모듈과 패키지의 모음
> - [https://docs.python.org/ko/3/library/index.html](https://docs.python.org/ko/3/library/index.html)

> 패키지 (Package)
> 
> - 관련된 모듈들을 하나의 디렉토리에 모아 놓은 것

> 패키지 사용하기
> 
> - 아래와 같은 디렉토리 구조로 작성
> - 패키지 3개 : my_package, math, statistics
> - 모듈 2개 : my_math.py  tools.py
> 
> ```
> sample.py (file)
> my_package (dir)
> 	> math (dir)
> 		> my_math.py (file)
> 	> statistics (dir)
> 		> tools.py (file)
> ```
> 
> ```python
> # my_math.py
> def add(x, y):
>     return x + y
> ```
> 
> ```python
> # tools.py
> def mod(x, y):
>     return x % y
> ```
> 
> ```python
> # sample.py
> from my_package.math import my_math
> from my_package.statistics import tools
> 
> print(my_math.add(1, 2)) # 3
> print(tools.mod(1, 2)) # 2
> ```
> 
> - 각 패키지의 모듈을 import 하여 사용하기
>     
>     ```python
>     from my_package.math import my_math
>     from my_package.statistics import tools
>     
>     print(my_math.add(1, 2)) # 3
>     print(tools.mod(1, 2)) # 2
>     ```
>     

> **PSL 내부 패키지**
> 
> - **설치 없이** 바로 import 하여 사용
> 
> **외부 패키지**
> 
> - **pip 를 사용하여 설치** 후 import 필요

> **pip (파이썬 패키지 관리자)**
> 
> - 외부 패키지들을 설치하도록 도와주는 파이썬의 패키지 관리 시스템
> - PyPI(Python Package Index)에 저장된 외부 패키지들을 설치
> - [https://pypi.org/](https://pypi.org/)

> **패키지 설치**
> 
> - 최신 버전/ 특정 버전/ 최소 버전을 명시하여 설치할 수 있음
>     
>     ```bash
>     $ pip install SomePackage
>     $ pip install SomePackage==1.0.5
>     $ pip install SomePackage>=1.0.4
>     ```
>     

> **requests 외부 패키지 설치 및 사용 예시**
> 
> 
> ```bash
> $ pip install requests
> ```
> 
> ```python
> import requests
> 
> url = 'https://random-data-api.com/api/v2/users'
> response = requests.get(url).json()
> print(response)
> ```
> 

> **패키지 사용 목적**
> 
> - 모듈들의 이름공간은 구분하여 충돌을 방지
> - 모듈들을 효율적으로 관리하고 재사용할 수 있도록 돕는 역할

---
