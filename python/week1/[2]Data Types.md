# Data Types

## INDEX

- Data Types
- Numeric Types
- Sequence Types
- Non-sequence Types
- Other Types
- Collection
- Type Conversion
- 연산자

---

## Data Types

> Data Types : 값의 종류와 그 값에 적용 가능한 연산과 동작을 결정하는 속성
> 

> 데이터 타입 분류
> 
> - Numeric Types
>     - int(정수), float(실수), complex(복소수)
> - Text Sequence Type
>     - str(문자열)
> - Sequence Types
>     - list, tuple, range
> - Non-sequence Types
>     - set, dict
> - 기타
>     - Boolean, None, Functions

> 데이터 타입이 필요한 이유
> 
> - 값들을 구분하고, 어떻게 다뤄야 하는지를 알 수 있음
> - 요리 재료마다 특정한 도구가 필요하듯이 각 데이터 타입 값들도 각자에게 적합한 도구를 가짐
> - 타입을 명시적으로 지정하면 코드를 읽는 사람이 변수의 의도를 더 쉽게 이해할 수 있고, 잘못된 데이터 타입으로 인한 오류를 미리 예방

---

## Numeric Types

> int - 정수 자료형 : 정수를 표현하는 자료형
> 
> 
> 
> 진수 표현
> 
> - 2진수(binary) : 0b
> - 8진수(octal) : 0o
> - 16진수(hexadecimal) : 0x
> 
> ```python
> print(0b10) # 2
> print(0o30) # 24
> print(0x10) # 16
> ```
> 

> float - 실수 자료형 : 실수를 표현하는 자료형
> 
> - 프로그래밍 언어에서는 float는 실수에 대한 근삿값
> 
> 유한 정밀도
> 
> - 컴퓨터 메모리 용량이 한정돼 있고 한 숫자에 대해 저장하는 용량이 제한됨.
> - 0.666666666666666666 과 1.666666666666666667 은 제한된 양의 메모리에 저장할 수 있는 2/3과 5/3에 가장 가까운 값
>     
>     ```python
>     print(2 / 3) # 0.6666666666666666
>     print(5 / 3) # 1.6666666666666667
>     ```
>     
> 
> 실수 연산 시 주의사항
> 
> - 컴퓨터는 2진수를 사용, 사람은 10진법을 사용
> - 이때 10진수 0.1은 2진수로 표현하면 0.0001100110011001100110… 같이 무한대로 반복
> - 무한대 숫자를 그대로 저장할 수 없어서 사람이 사용하는 10진법의 근사값만 표시
> - 0.1의 경우 3602879701896397 / 2 ** 55 이며 0.1에 가깝지만 정확히 동일하지는 않음
> - 이런 과정에서 예상치 못한 결과가 나타남
> - 이런 증상을 Floating point rounding error라고 함.
> 
> 실수 연산 시 해결책
> 
> - 두 수의 차이가 매우 작은 수보다 작은 지를 확인하거나 math 모듈 활용
>     
>     ```python
>     a = 3.2 - 3.1 #0.10000000000000009
>     b = 1.2 - 1.1 #0.09999999999999987
>     
>     # 1. 임의의 작은 수 활용
>     print(abs(a- b) <= 1e-10) #True
>     
>     # 2. math 모듈 활용
>     import math
>     print(math.isclose(a, b)) #True
>     ```
>     
> 
> 지수 표현 방식
> 
> - e 또는 E를 사용한 지수 표현
>     
>     ```python
>     # 314 * 0.01
>     number = 314e-2
>     
>     #float
>     print(type(number))
>     
>     #3.14
>     print(number)
>     ```
>     

---

## Sequence Types

> Sequence Types : 여러 개의 값들을 순서대로 나열하여 저장하는 자료형 (str, list, tuple, range)
> 
> 
> 
> Sequence Types 특징
> 
> 1. 순서(Sequence)
>     - 값들이 순서대로 저장 (정렬 X)
> 2. 인덱싱(Indexing)
>     - 각 값에 고유한 인덱스(번호)를 가지고 있으며, 인덱스를 사용하여 특정 위치의 값을 선택하거나 수정할 수 있음
> 3. 슬라이싱(Slicing)
>     - 인덱스 범위를 조절해 부분적인 값을 추출할 수 있음
> 4. 길이(Length)
>     - len() 함수를 사용하여 저장된 값의 개수(길이)를 구할 수 있음
> 5. 반복(Iteration)
>     - 반복문을 사용하여 저장된 값들을 반복적으로 처리할 수 있음

---

## str

> str -  문자열 : 문자들의 순서가 있는 변경 불가능한 시퀀스 자료형
> 
> 
> 
> 문자열 표현
> 
> - 문자열은 단일 문자나 여러 문자의 조합으로 이루어짐
> - 작은따옴표(’) 또는 큰따옴표(”) 감싸서 표현
>     
>     ```python
>     # Hello, World!
>     print("Hello, World!")
>     
>     # str
>     print(type('Hello, World!'))
>     ```
>     
> 
> 중첩 따옴표
> 
> - 따옴표 안에 따옴표를 표현할 경우
>     - 작은 따옴표가 들어 있는 경우는 큰 따옴표로 문자열 생성
>     - 큰 따옴표가 들어있는 경우는 작은 따옴표로 문자열 생성
> 
> Escape sequence
> 
> - 역 슬래시(backslash)뒤에 특정 문자가 와서 특수한 기능을 하는 문자 조합
> - 파이썬의 일반적인 문법 규칙을 잠시 탈출한다는 의미
>     
>     
>     | 예약문자 | 내용(의미) |
>     | --- | --- |
>     | \n | 줄 바꿈 |
>     | \t | 탭 |
>     | \ | 백슬래시 |
>     | \’ | 작은 따옴표 |
>     | \” | 큰 따옴표 |
>     
> 
> Escape sequence 예시
> 
> ```python
> # 철수야 '안녕'
> print('철수야 \'안녕\'')
> 
> '''
> 이 다음은 엔터 
> 입니다.
> '''
> print('이 다음은 엔터\n입니다.')
> ```
> 

---

## String Interpolation

- 문자열 내에 변수나 표현식을 삽입하는 방법

> f-string
> 
> - 문자열 f 또는 F 접두어를 붙이고 표션식을 {expression}로 작성하여 문자열에 파이썬 표현식의 값을 삽입할 수 있음
>     
>     ```python
>     bugs = 'roaches'
>     counts = 13
>     area = 'living room'
>     
>     # Debugging roaches 13 living room
>     print(f'Debugging {bugs} {counts} {area}')
>     ```
>     
> 
> 문자열 시퀀스 특징
> 
> ```python
> my_str = 'hello'
> # 인덱싱
> print(my_str[1]) # e
> # 슬라이싱
> print(my_str[2:4]) # ll
> # 길이
> print(len(my_str)) # 5
> ```
> 
> 인덱스(index) : 시퀀스 내의 값들에 대한 고유한 번호로, 각 값의 위치를 식별하는데 사용하는 숫자
> 
> index 예시
> 
> | ‘’ | h | e | l | l | o | “ |
> | --- | --- | --- | --- | --- | --- | --- |
> | index | 0 | 1 | 2 | 3 | 4 |  |
> | index | -5 | -4 | -3 | -2 | -1 |  |
> 
> 슬라이싱(slicing) : 시퀀스의 일부분을 선택하여 추출하는 작업
> 
> ⇒ 시작 인덱스와 끝 인덱스를 지정하여 해당 범위의 값을 포함하는 새로운 시퀀스를 생성
> 
> slicing 예시
> 
> | ‘’ | h | e | l | l | o | “ |
> | --- | --- | --- | --- | --- | --- | --- |
> | index | 0 | 1 | 2 | 3 | 4 |  |
> | index | -5 | -4 | -3 | -2 | -1 |  |
> 
> ```python
> print(my_str[2:4]) # ll
> print(my_str[:3]) # hel
> print(my_str[3:]) # lo
> ```
> 
> - step을 지정하여 추출
> 
> ```python
> print(my_str[0:5:2]) # hlo
> ```
> 
> - step이 음수일 경우
> 
> ```python
> print(my_str[::-1]) # olleh
> ```
> 
> 문자열은 불변 (변경 불가)
> 
> ```python
> my_str = 'hello'
> 
> # TypeError: 'str' object does not support item assignment
> my_str[1] = 'z'
> ```
> 

---

## list

> **list[리스트]** : 여러 개의 값을 순서대로 저장하는 **변경 가능한 시퀀스 자료형**
> 
> 
> 
> **리스트 표현**
> 
> - 0개 이상의 객체를 포함하며 데이터 목록을 저장
> - 대활호([])로 표기
> - 데이터는 어떤 자료형도 저장할 수 있음
>     
>     ```python
>     my_list_1 = []
>     my_list_2 = [1, 'a', 3, 'b', 5]
>     my_list_3 = [1, 2, 3, 'Python', ['hello', 'world', '!!!']]
>     ```
>     
> 
> **리스트의 시퀀스 특징**
> 
> ```python
> my_list = [1, 'a', 3, 'b', 5]
> 
> # 인덱싱
> print(my_list[1]) # a
> 
> # 슬라이싱
> print(my_list[2:4]) # [3, 'b']
> print(my_list[:3]) # [1, 'a', 3]
> print(my_list[3:]) # ['b', 5]
> print(my_list[0:5:2]) # [1, 3, 5]
> print(my_list[::-1]) # [5, 'b', 3, 'a', 1]
> 
> # 길이
> print(len(my_list)) # 5
> ```
> 
> **중첩된 리스트 접근**
> 
> - 출력 값 예상해보기
>     
>     ```python
>     my_list = [1, 2, 3, 'Python', ['hello', 'world', '!!!']]
>     print(len(my_list)) # 5
>     print(my_list[4][-1]) # !!!
>     print(my_list[-1][1][0]) #w
>     ```
>     
> 
> **리스트는 가변 (변경 가능)**
> 
> ```python
> my_list = [1, 2, 3]
> my_list[0] = 100
> print(my_list) # [100, 2, 3]
> ```
> 

---

## tuple

> tuple[튜플] : 여러 개의 값을 순서대로 저장하는 변경 불가능한 시퀀스 자료형
> 
> 
> 튜플 표현
> 
> - 0개 이상의 객체를 포함하며 데이터 목록을 저장
> - 소괄호(())로 표기
> - 데이터는 어떤 자료형도 저장할 수 있음
>     
>     ```python
>     my_tuple_1 = ()
>     my_tuple_2 = (1,)
>     my_tuple_3 = (1, 'a', 3, 'b', 5)
>     ```
>     
> 
> 튜플의 시퀀스 특징
> 
> ```python
> my_tuple = (1, 'a', 3, 'b', 5)
> 
> # 인덱싱
> print(my_tuple[1]) # a
> 
> # 슬라이싱
> print(my_tuple[2:4]) # (3, 'b')
> print(my_tuple[:3]) # (1, 'a', 3)
> print(my_tuple[3:]) # ('b', 5)
> print(my_tuple[0:5:]) # (1, 3, 5)
> print(my_tuple[::-1]) # (5, 'b', 3, 'a', 1)
> 
> # 길이
> print(len(my_tuple)) # 5
> ```
> 
> 튜플은 불변(변경 불가)
> 
> ```python
> my_tuple = (1, 'a', 3, 'b', 5)
> 
> # TypeError: 'tuple' object does not support item assignment
> my_tuple[1] = 'z'
> ```
> 
> 튜플은 어디에 쓰일까?
> 
> - 튜플의 불변 특성을 사용한 안전하게 여러 개의 값을 전달, 그룹화, 다중 할당 등 **개발자가 직접 사용하기 보다 ‘파이썬 내부 동작’에서 주로 사용됨
>     
>     ```python
>     x, y = (10, 20)
>     
>     print(x) # 10
>     print(y) # 20
>     
>     # 파이썬은 쉼표를 튜플 생성자로 사용하니 괄호는 생략 가능
>     x, y = 10, 20
>     ```
>     

---

## range

> range : 연속된 정수 시퀀스를 생성하는 변경 불가능한 자료형
> 

> range 표현
> 
> - range(n)
>     - 0 부터 n-1까지의 숫자의 시퀀스
> - range(n, m)
>     - n부터 m-1까지의 숫자 시퀀스
>     
>     ```python
>     my_range_1 = range(5)
>     my_range_2 = range(1, 10)
>     
>     print(my_range_1) # range(0, 5)
>     print(my_range_2) # range(1, 10)
>     ```
>     
> - 주로 반복문과 함께 사용 예정
>     
>     ```python
>     my_range_1 = range(5)
>     my_range_2 = range(1, 10)
>     
>     print(my_range_1) # range(0, 5)
>     print(my_range_2) # range(1, 10)
>     
>     # 리스트로 형 변환 시 데이터 확인 가능
>     
>     print(list(my_range_1)) # [0, 1, 2, 3, 4]
>     print(list(my_range_2)) # [1, 2, 3, 4, 5, 6, 7, 8, 9]
>     ```
>     

---

# Non-sequence Types

## dict

> dict[딕셔너리] : key - value 쌍으로 이루어진 순서와 중복이 없는 변경 가능한 자료형
> 

> 딕셔너리 표현
> 
> - key는 변경 불가능한 자료형만 사용 가능 (str, int, float, tuple, range…)
> - value는 모든 자료형 사용가능
> - 중괄호({})로 표기
>     
>     ```python
>     my_dict_1 = {}
>     my_dict_2 = {'key': 'value'}
>     my_dict_3 = {'apple': 12, 'list': [1, 2, 3]}
>     
>     print(my_dict_1) # {}
>     print(my_dict_2) # {'key': 'value'}
>     print(my_dict_3) # {'apple': 12, 'list': [1, 2, 3]}
>     ```
>     

> 딕셔너리 사용
> 
> - key를 통해 value에 접근
>     
>     ```python
>     my_dict_3 = {'apple': 12, 'list': [1, 2, 3]}
>     
>     print(my_dict['apple']) # 12
>     print(my_dict['list']) # [1, 2, 3]
>     
>     # 값 변경
>     my_dict['apple'] = 100
>     print(my_dict) # {'apple': 100, 'list': [1, 2, 3]}
>     ```
>     

---

## set

> set[세트] : 순서와 중복이 없는 변경 가능한 자료형
> 

> 세트 표현
> 
> - 수학에서의 집합과 동일한 연산 처리 가능
> - 중괄호({})로 표기
>     
>     ```python
>     my_set_1 = set()
>     my_set_2 = {1, 2, 3}
>     my_set_3 = {1, 1, 1}
>     
>     print(my_set_1) # set()
>     print(my_set_2) # {1, 2, 3}
>     print(my_set_3) # {1}
>     ```
>     

> 세트의 집합 연산
> 
> 
> ```python
> my_set_1 = {1, 2, 3}
> my_set_2 = {3, 6, 9}
> 
> # 합집합
> print(my_set_1 | my_set_2) # {1, 2, 3, 6, 9}
> 
> # 차집합
> print(my_set_1 - my_set_2) # {1, 2}
> 
> # 교집합
> print(my_set_1 & my_set_2) # {3}
> 
> ```
> 

---

# Other Types

## None

> None : 파이썬에서 ‘값이 없음’을 표현 하는 자료형
> 

> None 표현
> 
> 
> ```python
> variable = None
> print(variable) # None
> ```
> 

---

## Boolean

> Boolean : 참(True)과 거짓(False)을 표현하는 자료형
> 

> 불리언 표현
> 
> - 비교/ 논리 연산의 평가 결과로 사용됨
> - 주로 조건/ 반복문과 함께 사용
>     
>     ```python
>     bool_1 = True
>     bool_2 = False
>     
>     print(bool_1) # True
>     print(bool_2) # False
>     print(3 > 1) # True
>     print('3' != 3) # True
>     ```
>     

---

## Collection

> Collection : 여러 개의 항목 또는 요소를 담는 자료 구조
> 
> 
> → str, list, tuple, set, dict
> 

> 컬렉션 정리
> 
> 
> 
> | 컬렉션 | 변경 가능 여부 | 정렬 여부 |
> | --- | --- | --- |
> | str | X | O |
> | list | O | O |
> | tuple | X | O |
> | set | O | X |
> | dict | O | X |
> - 정렬 여부(O) ⇒ 시퀀스
> - 정렬 여부(X) ⇒ 비시퀀스

> 불변과 가변의 차이
> 
> 
> ```python
> my_str = 'hello'
> # TypeError: 'str' object does not support item assignment
> my_str[0] = 'z'
> 
> my_list = [1, 2, 3]
> my_list[0] = 100
> # [100, 2, 3]
> print(my_list)
> ```
> 

---

# Type Conversion

## Type conversion

### 암시적 형변환

> 암시적 형 변환 (Implicit Type Conversion)
> 
> 
> ⇒ 파이썬이 자동으로 형변환 하는 것
> 

> 암시적 형 변환 예시
> 
> - Boolean과 Numeric Type에서만 가능
>     
>     ```python
>     print(3 + 5.0) # 8.0
>     print(True + 3) # 4
>     print(True + False) # 1
>     ```
>     

---

### 명시적 형변환

> 명시적 형 변환(Explicit Type Conversion)
> 
> 
> ⇒ 개발자가 직접 형 변환을 하는 것
> 
> ⇒ 암시적 형 변환이 아닌 경우를 모두 포함
> 

> 명시적 형 변환 예시
> 
> - str → integer : 형식에 맞는 숫자만 가능
> - interger → str : 모두 가능
>     
>     ```python
>     print(int('1')) # 1
>     print(str(1) + '등') # 1등
>     print(float('3.5')) # 3.5
>     print(int(3.5)) # 3
>     
>     # ValueError: invalid literal for int() with base 10: '3.5'
>     print(int('3.5'))
>     ```
>     

> 컬렉션 간 형 변환 정리
> 
> 
> 
> |  | str | list | tuple | range | set | dict |
> | --- | --- | --- | --- | --- | --- | --- |
> | str |  | O | O | X | O | X |
> | list | O |  | O | X | O | X |
> | tuple | O | O |  | X | O | X |
> | range | O | O | O |  | O | X |
> | set | O | O | O | X |  | X |
> | dict | O | O(Key만) | O(Key만) | X | O(Key만) |  |

---

## Operator(연산자)

> 산술 연산자
> 
> 
> 
> | 기호 | 연산자 |
> | --- | --- |
> | - | 음수 부호 |
> | + | 덧셈 |
> | - | 뺄셈 |
> | * | 곱셈 |
> | / | 나눗셈 |
> | // | 정수 나눗셈 (몫) |
> | % | 나머지 |
> | ** | 지수 (거듭제곱) |

> 복합 연산자
> 
> - 연산과 할당이 함께 이뤄짐
>     
>     
>     | 기호 |  |  |
>     | --- | --- | --- |
>     | += | a += b | a = a + b |
>     | -= | a -= b | a = a - b |
>     | *= | a *= b | a = a * b |
>     | /= | a /= b | a = a / b |
>     | //= | a //= b | a = a // b |
>     | %= | a %= b | a = a % b |
>     | **= | a **= b | a = a ** b |

> 복합 연산자 예시
> 
> 
> ```python
> y = 10
> y -= 4
> print(y) # 6
> 
> z = 7
> z *= 2
> print(z) # 14
> 
> w = 15
> w /= 4
> print(w) # 3.75
> 
> q = 20
> q //= 3
> print(q) # 6
> ```
> 

> 비교 연산자
> 
> 
> 
> | 기호 | 내용 |
> | --- | --- |
> | < | 미만 |
> | <= | 이하 |
> | > | 초과 |
> | >= | 이상 |
> | == | 같음 |
> | != | 같지 않음 |
> | is | 같음 |
> | is not | 같지 않음 |

> is 비교 연산자
> 
> - 메모리 내에서 같은 객체를 참조하는지 확인
> - == 는 동등성(equality), is 는 식별성(identity)
> - 값을 비교하는 == 와 다름
>     
>     
>     | 기호 | 내용 |
>     | --- | --- |
>     | is | 같음 |
>     | is not | 같지 않음 |

> 비교 연산자 예시
> 
> 
> ```python
> print(3 > 6) # False
> print(2.0 == 2) # True
> print(2 != 2) # False
> print('HI' == 'hi') # False
> 
> # SyntaxWarning
> # ==은 값(데이터)을 비교하는 것이지만 is는 레퍼런스(주소)를 비교히가 때문
> # is 연산자는 되도록이면 None, True, False 등을 비교할 때 사용
> print(2.0 is 2) # False
> ```
> 

> 논리 연산자
> 
> 
> 
> | 기호 | 연산자 | 내용 |
> | --- | --- | --- |
> | and | 논리곱 | 두 피연산자 모두 True인 경우에만 전체 표현식을 True로 평가 |
> | or | 논리합 | 두 피연산자 중 하나라도 True인 경우 전체 표현식을 True로 평가 |
> | not | 논리부정 | 단일 피연산자를 부정 |

> 논리 연산자 예시
> 
> 
> ```python
> print(True and False) # False
> print(True or False) # True
> print(not True) # False
> print(not 0) # True
> ```
> 
> - 비교 연산자와 함께 사용 가능
>     
>     ```python
>     num = 15
>     result = (num > 10) and (num % 2 == 0)
>     print(result) # False
>     
>     name = 'Alice'
>     age = 25
>     result = (name == 'Alice') or (age == 30)
>     print(result) # True 
>     ```
>     

---

## 단축 평가

> **단축 평가**
> 
> - 논리 연산에서 두 번째 피 연산자를 평가하지 않고 결과를 결정하는 동작

> **단축 평가 예시 문제**
> 
> 
> ```python
> vowels = 'aeiou'
> 
> print(('a' and 'b') in vowels) # False
> print(('b' and 'a') in vowels) # True
> 
> print(3 and 5) # 5
> print(3 and 0) # 0
> print(0 and 3) # 0
> print(0 and 0) # 0
> 
> print(5 or 3) # 5
> print(3 or 0) # 3
> print(0 or 3) # 3
> print(0 or 0) # 0
> ```
> 

> 단축 평가 동작
> 
> 1. and
>     - 첫 번째 피 연산자가 False인 경우, 전체 표현식은 False로 결정.
>         
>         두 번째 피 연산자가 평가되지 않고 그 값이 무시
>         
>     - 첫 번째 피 연산자가 True인 경우, 전체 표현식의 결과는 두 번째 피 연산자에 의해 결정
>         
>         두 번째 피 연산자가 평가되고 그 결과가 전체 표현식의 결과로 반환
>         
> 2. or
>     - 첫 번째 피 연산자가 True인 경우, 전체 표현식은 True로 결정.
>         
>         두 번째 피 연산자가 평가되지 않고 그 값이 무시
>         
>     - 첫 번째 피 연산자가 False인 경우, 전체 표현식의 결과는 두 번째 피 연산자에 의해 결정
>         
>         두 번째 피 연산자가 평가되고 그 결과가 전체 표현식의 결과로 반환
>         

> **단축 평가 이유**
> 
> - 코드 실행을 최적화하고, 불필요한 연산을 피할 수 있도록 함

---

## 멤버십 연산자

> **멤버십 연산자**
> 
> - 특정 값이 시퀀스나 다른 컬렉션에 속하는지 여부를 확인
>     
>     
>     | 기호 | 내용 |
>     | --- | --- |
>     | in | 왼쪽 피 연산자가 오른쪽 피 연산자의 시퀀스에 속하는지를 확인 |
>     | not in | 왼쪽 피 연산자가 오른쪽 피 연산자의 시퀀스에 속하지 않는지를 확인 |

> **멤버십 연산자 예시**
> 
> 
> ```python
> word = 'hello'
> numbers = [1, 2, 3, 4, 5]
> 
> print('h' in word) # True
> print('z' in word) # False
> 
> print(4 not in numbers) # False
> print(6 not in numbers) # True
> ```
> 

---

## 시퀀스형 연산자

> **시퀀스형 연산자**
> 
> - + 와 * 는 시퀀스 간 연산에서 산술 연산자 일 때와 다른 역할을 가짐
>     
>     
>     | 연산자 | 내용 |
>     | --- | --- |
>     | + | 결합 연산자 |
>     | * | 반복 연산자 |

> **시퀀스형 연산자 예시**
> 
> 
> ```python
> # Gildong Hong
> print('Gildon' + 'Hong')
> 
> # hihihihihi
> print('hi' * 5)
> 
> # [1, 2, 'a', 'b']
> print([1, 2] + ['a', 'b'])
> 
> #[1, 2, 1, 2]
> print([1, 2] * 2)
> ```
> 

> **연산자 우선순위**
> 
> 
> 
> | 우선순위 | 연산자 | 내용 |
> | --- | --- | --- |
> | 높음 | () | 소 괄호 grouping |
> |  | [] | 인덱싱, 슬라이싱 |
> |  | ** | 거듭 제곱 |
> |  | +, - | 단항 연산자 양수/음수 |
> |  | *, /, //, % | 산술 연산자 |
> |  | +, - | 산술 연산자 |
> |  | <. ≤, > , ≥ , ==, ≠ | 비교 연산자 |
> |  | is, is not | 객체 비교 |
> |  | in, not in | 멤버십 연산자 |
> |  | not | 논리 부정 |
> |  | and | 논리 AND |
> | 낮음 | or | 논리 OR |
