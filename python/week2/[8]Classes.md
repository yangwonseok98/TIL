# Classes

## INDEX

> **INDEX**
> 
> - 객체 지향 프로그래밍
> - 객체
> - 클래스
> - 메서드

## 객체 지향 프로그래밍

### 개요

> **절차 지향 프로그래밍 (Procedural Programming)**
> 
> - 프로그램을 **‘데이터’**와 **‘절차’**로 구성하는 방식의 프로그래밍 패러다임

> **절차 지향 프로그래밍 특징**
> 
> - “데이터”와 해당 데이터를 처리하는 “함수(절차)” 가 분리되어 있으며, 함수 호출의 흐름이 중요
> - 코드의 순차적인 흐름과 함수 호출에 의해 프로그램이 진행
> 
> ⇒ 실제로 실행되는 내용이 무엇이 무엇인가가 중요
> 
> ⇒ 데이터를 다시 재사용하거나 하기보다는 처음부터 끝까지 실행되는 결과물이 중요한 방식
> 

> **소프트웨어 위기(Software Crisis)**
> 
> - 하드웨어의 발전으로 컴퓨터 계산용량과 문제의 복잡성이 급격히 증가함에 따라 소프트웨어에 발생한 충격

> **객체 지향 프로그래밍(Object Oriented Programming)**
> 
> - 데이터와 해당 데이터를 조작하는 메서드를 하나의 객체로 묶어 관리하는 방식의 프로그래밍 패러다임

> **절차 지향 VS 객체 지향**
> 
> - 절차 지향
>     - 데이터와 해당 데이터를 처리하는 함수(절차)가 분리
>     - 함수 호출의 흐름이 중요
> - 객체 지향
>     - 데이터와 해당 데이터를 처리하는 메서드(메시지)를 하나의 객체(클래스)로 묶음
>     - 객체 간 상호작용과 메시지 전달이 중요

---

## 객체

### 개요

> **클래스(Class) : 파이썬에서 타입을 표현하는 방법**
> 
> - 객체를 생성하기 위한 설계도
> - 데이터와 기능을 함께 묶는 방법을 제공

> **객체(Object)**
> 
> - 클래스에서 정의한 것을 토대로 메모리에 할당된 것
> - ‘속성’과 ‘행동’으로 구성된 모든 것

> **객체 예시**
> 
> - 가수
>     - 속성(변수)
>         - 직업 - 가수
>         - 생년월일 - 1993년 5월 16일
>         - 국적 - 대한민국
>     - 행동(메서드)
>         - 랩()
>         - 댄스()
>         - 소몰이()

> **클래스와 객체**
> 
> - **클래스** : 가수
> - **객체** : 아이유, BTS, ….
> - 클래스로 만든 객체를 인스턴스라고도 함
>     - 가수(클래스)
>         
>         → 아이유는 객체다(O)
>         
>         → 아이유는 인스턴스다(X)
>         
>         → 아이유는 가수의 인스턴스다(O)
>         
> - 클래스(가수)와 객체(아이유)
> - 클래스(가수) → 타입(list)
>     - 클래스를 만든다 == 타입을 만든다.
> 
> - 변수 name의 타입은 str 클래스다.
>     
>     ⇒ 변수 name은 str 클래스와 인스턴스이다.
>     
>     ⇒ 우리가 사용해왔던 데이터 타입은 사실 모두 클래스였다.
>     
>     ```python
>     name = 'Alice'
>     print(type(name)) # <class 'str'>
>     ```
>     
> 
> - 결국 문자열 타입의 변수는 str 클래스로 만든 인스턴스다.
>     
>     ```python
>     print(help(str))
>     '''
>     class str(object)
>      |  str(object='') -> str
>      |  str(bytes_or_buffer[, encoding[, errors]]) -> str
>      |  
>      |  Create a new string object from the given object. If encoding or
>      |  errors is specified, then the object must expose a data buffer
>      |  that will be decoded using the given encoding and error handler.
>      |  Otherwise, returns the result of object.__str__() (if defined)
>     ...
>     '''
>     ```
>     
> - ‘ ‘ , ‘hello’, ‘파이썬’ ⇒ 문자열 타입(클래스)의 객체(인스턴스)
> - [1, 2, 3], [1], [], [’hi’] ⇒ 리스트 타입(클래스)의 객체(인스턴스)

> **인스턴스와 메서드**
> 
> - “hello”.upper()
>     - 문자열.대문자로()
>     - 객체.행동()
>     - 인스턴스.메서드()
> - [1, 2, 3].sort()
>     - 리스트.정렬()
>     - 객체.행동()
>     - 인스턴스.메서드()
> - 하나의 객체(object)는 특정 타입의 인스턴스(instance)이다.
>     - 123, 900, 5는 모두 int의 인스턴스
>     - ‘hello’, ‘bye’는 모두 string의 인스턴스
>     - [232, 89, 1], []은 모두 list의 인스턴스

> **객체(object)의 특징**
> 
> - 타입(type) : 어떤 연산자(operator)와 조작(method)이 가능한가?
> - 속성(attribute) : 어떤 상태(데이터)를 가지는가?
> - 조작법(method) : 어떤 행위(함수)를 할 수 있는가?
> - Python의 객체와 클래스(Object and Class in Python)
>     - 객체(Object) = 속성(Attribute) + 기능(Method)

---

## 클래스

### 개요

> **클래스(Class) : 파이썬에서 타입을 표현하는 방법**
> 
> - 객체를 생성하기 위한 설계도
> - 데이터와 기능을 함께 묶는 방법을 제공

> **클래스 구조**
> 
> 
> ```python
> # 클래스 정의
> class Person:
>     pass
> 
> # 인스턴스 생성
> iu = Person()
> 
> # 메서드 호출
> iu.메서드()
> 
> # 속성(변수) 접근
> iu.attribute
> ```
> 

> **클래스 기본 활용**
> 
> 
> ```python
> # 클래스 정의
> class Person:
>     blood_color = 'red'
> 
>     def __init__(self, name):
>         self.name = name
> 
>     def singing(self):
>         return f'{self.name}가 노래합니다.'
> 
> # 인스턴스 생성
> singer1 = Person('iu')
> 
> # 메서드 호출
> print(singer1.singing()) # iu가 노래합니다.
> 
> # 속성(변수) 접근
> print(singer1.blood_color) # red
> ```
> 
> - 생성자 함수 ex) `def __init__(self, name)`
>     - 객체를 생성할 때 자동으로 호출되는 특별한 메서드
>     - `__init__`이라는 이름의 메서드로 정의되며, 객체의 초기화를 담당
>     - 생성자 함수를 통해 인스턴스를 생성하고 필요한 초기값을 설정
> 
> - 인스턴스 변수 ex) `self.name = name`
>     - 인스턴스(객체)마다 별도로 유지되는 변수
>     - 인스턴스마다 독립적인 값을 가지며, 인스턴스가 생성될 때 마다 초기화 됨
>     
> - 클래스 변수 ex) `blood_color = 'red'`
>     - 클래스 내부에 선언된 변수
>     - 클래스로 생성된 모든 인스턴스들이 공유하는 변수
> 
> - 인스턴스 메서드 ex) `def singing(self)`
>     - 각각의 인스턴스에서 호출할 수 있는 메서드
>     - 인스턴스 변수에 접근하고 수정하는 등의 작업을 수행

> **인스턴스와 클래스 간의 이름 공간(name space)**
> 
> - 클래스를 정의하면, 클래스와 해당하는 이름 공간 생성
> - 인스턴스를 만들면, 인스턴스 객체가 생성되고 독립적인 이름 공간 생성
> - 인스턴스에서 특정 속성에 접근하면, 인스턴스 → 클래스 순으로 탐색
>     
>     ```python
>     # 클래스 정의
>     class Person:
>         name = 'unknown'
>     
>         def talk(self):
>             print(self.name)
>     
>     p1 = Person()
>     p1.talk() # unknown
>     
>     p2 = Person()
>     p2.talk() # unknown
>     p2.name = 'Kim'
>     p2.talk() # Kim
>     
>     print(Person.name) # unknown
>     print(p1.name) # unknown
>     print(p2.name) # Kim
>     ```
>     
>     - p1은 인스턴스 변수가 정의되어 있지 않아 클래스 변수(unkown)가 출력됨
>     - p2는 인스턴스 변수가 정의되어 인스턴스 변수(Kim)가 출력됨
>     - Person 클래스 값이 Kim으로 변경된 것이 아닌, p2 인스턴스의 이름 공간에 name이 Kim으로 저장됨

> **독립적인 이름공간을 가지는 이점**
> 
> - 각 인스턴스는 독립적인 메모리 공간을 가지며, 클래스와 다른 인스턴스 간에는 서로의 데이터나 상태에 직접적인 접근이 불가능
> - 객체 지향 프로그래밍의 중요한 특성 중 하나로, 클래스와 인스턴스를 모듈화하고 각각의 객체가 독립적으로 동작하도록 보장
> - 이를 통해 클래스와 인스턴스는 다른 객체들과의 상호작용에서 서로 충돌이나 영향을 주지 않으면서 독립적으로 동작할 수 있음
> - 코드의 가독성, 유지보수성, 재사용성을 높이는데 도움을 줌

---

### 인스턴스 변수와 클래스 변수

> **클래스 변수 활용**
> 
> - 가수가 몇 명인지 확인하고 싶다면?
>     - 인스턴스가 생성될 때 마다 클래스 변수가 늘어나도록 설정할 수 있음
>         
>         ```python
>         class Person:
>             count = 0
>         
>             def __init__(self, name):
>                 self.name = name
>                 Person.count += 1
>         
>         person1 = Person('iu')
>         person2 = Person('BTS')
>         
>         print(Person.count) # 2
>         ```
>         

> **클래스 변수와 인스턴스 변수**
> 
> - 클래스 변수를 변경할 때는 항상 클래스.클래스변수 형식으로 변경
>     
>     ```python
>     class Circle:
>         pi = 3.14
>     
>         def __init__(self, r):
>             self.r = r
>     
>     c1 = Circle(5) 
>     c2 = Circle(10)
>     
>     print(Circle.pi) # 3.14
>     print(c1.pi) # 3.14
>     print(c2.pi) # 3.14
>     
>     Circle.pi = 5 # 클래스 변수 변경
>     print(Circle.pi) # 5
>     print(c1.pi) # 5
>     print(c2.pi) # 5
>     
>     Circle.pi = 3.14 # 클래스 변수 초기화
>     c2.pi = 5 # 인스턴스 변수 변경
>     print(Circle.pi) # 3.14 (클래스 변수)
>     print(c1.pi) # 3.14 (클래스 변수)
>     print(c2.pi) # 5 (새로운 인스턴스 변수가 생성됨)
>     ```
>     

---

## 메서드

### 개요

> **메서드 종류**
> 
> - 인스턴스 메서드
> - 클래스 메서드
> - 정적 메서드

---

### 인스턴스 메서드

> **인스턴스 메서드 (instance method)**
> 
> - 클래스로부터 생성된 각 인스턴스에서 호출할 수 있는 메서드
>     
>     ⇒ 인스턴스의 상태를 조작하거나 동작을 수행
>     

> **인스턴스 메서드 구조**
> 
> - 클래스 내부에 정의되는 메서드의 기본
> - 반드시 첫 번째 매개변수로 인스턴스 자신(self)를 전달받음
>     
>     ```python
>     class MyClass:
>         def instance_method(self, arg1,..):
>             pass
>     ```
>     

> **self 동작 원리**
> 
> - upper 메서드를 사용해 문자열 ‘hello’를 대문자로 변경하기
>     
>     `‘hello’.upper()`
>     
> - 하지만 실제 파이썬 내부의 동작은 다음과 같이 이루어 진다.
>     
>     `str.upper(’hello’)`
>     
> - str 클래스가 upper 메서드를 호출했고, 그 첫번째 인자로 문자열 인스턴스가 들어간 것이다.
> 
> **⇒ 인스턴스 메서드의 첫번째 매개변수가 반드시 인스턴스 자기 자신인 이유**
> 
> - `‘hello’.upper()` 은 `str.upper(’hello’)`를 객체 지향 방식의 메서드로 호출하는 표현이다. (단축형 호출)
> - `‘hello’` 라는 문자열 객체가 단순히 어딘가의 함수로 들어가는 인자가 아닌 객체 스스로 메서드를 호출하여 코드를 동작하는 객체 지향적 표현이다.

> **생성자 메서드(constructor method)**
> 
> - 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드
>     
>     ⇒ 인스턴스 변수들의 초기값을 설정
>     

> **생성자 메서드 구조**
> 
> 
> ```python
> class Person:
>     def __init__(self):
>         print('인스턴스가 생성되었습니다.')
>     
> 
> person1 = Person() # 인스턴스가 생성되었습니다.
> ```
> 
> ```python
> class Person:
>     def __init__(self, name):
>         print(f'인스턴스가 생성되었습니다. {name}')
> 
> person1 = Person('지민') # 인스턴스가 생성되었습니다. 지민
> ```
> 

---

### 클래스 메서드

> **클래스 메서드 (class method) : 클래스가 호출하는 메서드**
> 
> 
> ⇒ 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행
> 

> **클래스 메서드 구조**
> 
> - `@classmethod` 데코레이터를 사용하여 정의
> - 호출 시, 첫 번째 인자로 호출하는 클래스(cls)가 전달됨
>     
>     ```python
>     class MyClass:
>         
>         @classmethod
>         def class_method(cls, arg1):
>             pass
>     ```
>     

> **클래스 메서드 예시**
> 
> 
> ```python
> class Person:
>     count = 0
> 
>     def __init__(self, name):
>         self.name = name
>         Person.count += 1
> 
>     @classmethod
>     def number_of_population(cls):
>         print(f'인구수는 {cls.count}입니다.')
> 
> person1 = Person('IU')
> person2 = Person('BTS')
> 
> Person.number_of_population() # 인구수는 2입니다.
> ```
> 

---

### 스태틱 메서드

> **스태틱(정적) 메서드 (static method)**
> 
> - 클래스와 인스턴스와 상관없이 독립적으로 동작하는 메서드
>     
>     ⇒ 주로 클래스와 관련이있지만 인스턴스와 상호작용이 필요하지 않은 경우에 사용
>     

> **스태틱 메서드 구조**
> 
> - `@staticmethod` 데코레이터를 사용하여 정의
> - 호출 시 필수적으로 작성해야 할 매개변수가 없음
> - 즉, 객체 상태나 클래스 상태를 수정할 수 없으며 단지 기능(행동)만을 위한 메서드로 사용
>     
>     ```python
>     class MyClass:
>         @staticmethod
>         def static_method(arg1, ...):
>             pass
>     ```
>     

> **스태틱 메서드 예시**
> 
> 
> ```python
> class StringUtils:
>     @staticmethod
>     def reverse_string(string: str):
>         return string[::-1]
> 
>     @staticmethod
>     def capitalized_string(string: str):
>         return string.capitalize()
> 
> text = 'hello, world'
> 
> reversed_text = StringUtils.reverse_string(text)
> print(reversed_text) # dlrow ,olleh
> 
> capitalized_text = StringUtils.capitalized_string(text)
> print(capitalized_text) # Hello, world
> ```
> 

---

### 메서드 정리

> **메서드 정리**
> 
> - 인스턴스 메서드
>     - 인스턴스의 상태를 변경하거나, 해당 인스턴스의 특정 동작을 수행
> - 클래스 메서드
>     - 인스턴스의 상태에 의존하지 않는 기능을 정의
>     - 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행
> - 스태틱 메서드
>     - 클래스 및 인스턴스와 관련이 없는 일반적인 기능을 수행

> **각자의 역할**
> 
> - 클래스가 사용해야 할 것
>     - 클래스 메서드
>     - 스태틱 메서드
> - 인스턴스가 사용해야 할 것
>     - 인스턴스 메서드

> **메서드 정리 예시**
> 
> 
> ```python
> class MyClass:
> 
>     def instance_method(self):
>         return 'instance method', self
> 
>     @classmethod
>     def class_method(cls):
>         return 'class method', cls
> 
>     @staticmethod
>     def static_method():
>         return 'static method'
> ```
> 

> **클래스가 할 수 있는 것**
> 
> - 클래스는 모든 메서드를 호출 할 수 있음
>     
>     ⇒ 하지만 클래스는 클래스 메서드와 스태틱 메서드만 사용하도록 한다
>     
>     ```python
>     class MyClass:
>     
>         def instance_method(self):
>             return 'instance method', self
>     
>         @classmethod
>         def class_method(cls):
>             return 'class method', cls
>     
>         @staticmethod
>         def static_method():
>             return 'static method'
>     
>     instance = MyClass()
>     
>     print(MyClass.instance_method(instance)) # ('instance method', <__main__.MyClass object at 0x000001e16dc786b0>)
>     print(MyClass.class_method()) # ('class method', <class '__main__.MyClass'>)
>     print(MyClass.static_method()) # static method
>     ```
>     

> **인스턴스가 할 수 있는 것**
> 
> - 인스턴스는 모든 메서드를 호출 할 수 있음
>     
>     ⇒ 하지만 인스턴스는 인스턴스 메서드만 사용하도록 한다.
>     
>     ```python
>     class MyClass:
>     
>         def instance_method(self):
>             return 'instance method', self
>     
>         @classmethod
>         def class_method(cls):
>             return 'class method', cls
>     
>         @staticmethod
>         def static_method():
>             return 'static method'
>     
>     instance = MyClass()
>     
>     print(instance.instance_method()) # ('instance method', <__main__.MyClass object at 0x000001ee8bd586e8>)
>     print(instance.class_method()) # ('class method', <class '__main__.MyClass'>)
>     print(instance.static_method()) # static method
>     ```
>     

> **할 수 있다 ≠ 써도된다**
> 
> - 각자의 메서드는 OOP 패러다임에 따라
>     
>     명확한 목적에 따라 설계된 것이기 때문에
>     
>     클래스와 인스턴스 각각 올바른 메서드만 사용하도록 해야 한다.
>     

---

## 참고

> **매직 메서드**
> 
> - 특별한 인스턴스 메서드
> - 특정 상황에 자동으로 호출되는 메서드
> - Double underscore(__)가 있는 메서드는 특수한 동작을 위해 만들어진 메서드
>     - 스페셜 메서드 혹은 매직 메서드라고 불림
> - 예시
>     
>     ```python
>     __str__(self), __len__(self), __lt__(self, other), 
>     __le__(self, other), __eq__(self, other), __gt__(self, other), 
>     __ge__(self, other), __ne__(self, other),
>     ```
>     

> **매직 매서드 예시**
> 
> 
> ```python
> class Circle:
>     def __init__(self, r):
>         self.r = r
> 
>     def area(self):
>         return 3.14 * self.r * self.r
> 
>     def __str__(self):
>         return f'[원] radius: {self.r}'
> 
> c1 = Circle(10)
> c2 = Circle(1)
> 
> print(c1) # [원] radius: 10
> print(c2) # [원] radius: 1
> ```
> 

> **데코레이터 (Decortator)**
> 
> - 다른 함수의 코드를 유지한 채로 수정하거나 확장하기 위해 사용되는 함수
>     
>     ```python
>     # 데코레이터 정의
>     def my_decorator(func):
>         def wrapper():
>             # 함수 실행 전에 수행할 작업
>             print('함수 실행 전')
>             # 원본 함수 호출
>             result = func()
>             # 함수 실행 후에 수행할 작업
>             print('함수 실행 후')
>             return result
>         return wrapper
>     
>     # 데코레이터 적용
>     @my_decorator
>     def my_function1():
>         print('원본 함수 실행1')
>     
>         
>     my_function()
>     '''
>     함수 실행 전
>     원본 함수 실행
>     함수 실행 후
>     '''
>     ```
>     

> **절차 지향과 객체 지향은 대조되는 개념이 아니다**
> 
> 
> 객체 지향은 기존 절차 지향을 기반으로 두고 보완하기 위해
> 
> 객체라는 개념을 도입해 상속, 코드 재사용성, 유지보수성 등의 이점을 가지는 패러다임
>
