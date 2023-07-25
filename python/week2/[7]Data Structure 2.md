# Data Structure 2

## INDEX

> **INDEX**
> 
> - 비시퀀스 데이터 구조
> - 복사

---

## 비 시퀀스 데이터 구조

### 세트

> **set** : 고유한 항목들의 정렬되지 않은 컬렉션
> 

> **세트 메서드**
> 
> 
> 
> | 메서드 | 설명 |
> | --- | --- |
> | s.add(x) | 세트 s에 항목 x를 추가. 이미 x가 있다면 변화 없음 |
> | s.clear() | 세트 s의 모든 항목을 제거 |
> | s.remove(x) | 세트 s에서 항목 x를 제거. 항목 x가 없을 경우 Key error |
> | s.pop() | 세트 s에서 랜덤하게 항목을 반환하고, 해당 항목을 제거 |
> | s.discard(x) | 세트 s에서 항목 x를 제거 |
> | s.update(iterable) | 세트 s에 다른 iterable 요소를 추가 |

> **세트 관련 메서드**
> 
> - **.add(x) : 세트에 x를 추가**
>     
>     ```python
>     my_set = {1, 2, 3}
>     my_set.add(4)
>     print(my_set) #{1, 2, 3, 4}
>     
>     my_set.add(4)
>     print(my_set) # {1, 2, 3, 4}
>     ```
>     
> - **.clear() : 세트의 모든 항목을 제거**
>     
>     ```python
>     my_set = {1, 2, 3}
>     my_set.clear()
>     print(my_set) # set()
>     ```
>     
> - **.remove(x) : 세트에서 항목 x를 제거**
>     
>     ```python
>     my_set = {1, 2, 3}
>     my_set.remove(2)
>     print(my_set) # {1, 3}
>     
>     my_set.remove(10)
>     print(my_set) # KeyError: 10
>     ```
>     
> - **.discard() : 세트 s에서 항목 x를 제거. remove와 달리 에러 없음**
>     
>     ```python
>     my_set = {1, 2, 3}
>     my_set.discard(2)
>     print(my_set) # {1, 3}
>     
>     my_set.discard(10)
>     print(my_set) # {1, 3}
>     ```
>     
> - **.pop() : 세트에서 임의의 요소를 제거하고 반환**
>     
>     ```python
>     my_set = {1, 2, 3}
>     element = my_set.pop()
>     
>     print(element) # 3
>     print(my_set) # {1, 2}
>     ```
>     
> - **.update(iterable) : 세트에 다른 iterable 요소를 추가**
>     
>     ```python
>     my_set = {1, 2, 3}
>     my_set.update([4, 5, 1])
>     
>     print(my_set) # {1, 2, 3, 4, 5}
>     ```
>     

> **세트의 집합 메서드**
> 
> 
> 
> | 메서드 | 설명 | 연산자 |
> | --- | --- | --- |
> | set1.difference(set2) | set1에는 들어있지만 set2에는 없는 항목으로 세트를 생성 후 반환 | set1 - set2 |
> | set1.intersection(set2) | set1과 set2 모두 들어있는 항목으로 세트를 생성 후 반환 | set1 & set2 |
> | set1.issubset(set2) | set1의 항목이 모두 set2에 들어있으면 True를 반환 | set1 ≤ set2 |
> | set1.issuperset(set2) | set1이 set2의 모든 항목을 모두 포함하면 True를 반환 | set1 ≥ set2 |
> | set1.union(set2) | set1 또는 set2에(혹은 둘 다) 들어있는 항목으로 세트를 생성 후 반환 | set1 | set2 |
> 
> ```python
> set1 = {0, 1, 2, 3, 4}
> set2 = {1, 3, 5, 7, 9}
> 
> print(set1.difference(set2)) # {0, 2, 4}
> print(set1.intersection(set2)) # {1, 3}
> print(set1.issubset(set2)) # False
> print(set1.issuperset(set2)) # False
> print(set1.union(set2)) # {0, 1, 2, 3, 4, 5, 7, 9}
> ```
> 

---

### 딕셔너리

> **dictionary : 고유한 항목들의 정렬되지 않은 컬렉션**
> 

> **딕셔너리 메서드**
> 
> 
> 
> | 메서드 | 설명 |
> | --- | --- |
> | D.clear() | 딕셔너리 D의 모든 키/ 값 쌍을 제거 |
> | D.get(k) | 키 k에 연결된 값을 반환 (키가 없으면 None을 반환) |
> | D.get(k, v) | 키 k에 연결된 값을 반환하거나 키가 없으면 기본 값으로 v를 반환 |
> | D.keys() | 딕셔너리 D의 키를 모은 객체를 반환 |
> | D.values() | 딕셔너리 D의 값을 모은 객체를 반환 |
> | D.items() | 딕셔너리 D의 키/ 값 쌍을 모은 객체를 반환 |
> | D.pop(k) | 딕셔너리 D에서 키 k를 제거하고 연결됐던 값을 반환 (없으면 오류) |
> | D.pop(k, v) | 딕셔너리 D에서 키 k를 제거하고 연결됐던 값을 반환 (없으면 v를 반환) |
> | D.setdefault(k) | 딕셔너리 D에서 키 k와 연결된 값을 반환 |
> | D.setdefault(k, v) | 딕셔너리 D에서 키 k와 연결된 값을 반환. k가 D의 키가 아니면 값 v와 연결한 키 k를 D에 추가하고 v를 반환 |
> | D.update(other) | other 내 각 키에 대해 D에 있는 키면 D에 있는 그 키의 값을 other에 있는 값으로 대체, other에 있는 각 키에 대해 D에 없는 키면 키/ 값 쌍을 D에 추가 |

> **딕셔너리 관련 메서드**
> 
> - **.clear() : 딕셔너리 D의 모든 키/값 쌍을 제거**
>     
>     ```python
>     person = {'name': 'Alice', 'age': 25}
>     person.clear()
>     print(person) # {}
>     ```
>     
> - **.get(key[, default]) : 키에 연결된 값을 반환하거나 키가 없으면 None혹은 기본값을 반환**
>     
>     ```python
>     person = {'name': 'Alice', 'age': 25}
>     
>     print(person.get('name')) # Alice
>     print(person.get('country')) # None
>     print(person.get('country', 'Unknown')) # Unknown
>     ```
>     
> - **.keys() : 딕셔너리 키를 모은 객체를 반환**
>     
>     ```python
>     person = {'name': 'Alice', 'age': 25}
>     print(person.keys()) # dict_keys(['name', 'age'])
>     
>     for k in person.keys():
>         print(k)
>     '''
>     name
>     age
>     '''
>     ```
>     
> - **.values() : 딕셔너리 값을 모은 객체를 반환**
>     
>     ```python
>     person = {'name': 'Alice', 'age': 25}
>     print(person.keys()) # dict_keys(['name', 'age'])
>     
>     for v in person.values():
>         print(v)
>     '''
>     Alice
>     25
>     '''
>     ```
>     
> - **.items() : 딕셔너리 키/ 값 쌍을 모은 객체를 반환**
>     
>     ```python
>     person = {'name': 'Alice', 'age': 25}
>     print(person.items()) # dict_items([('name', 'Alice'), ('age', 25)])
>     
>     for k, v in person.items():
>         print(k, v)
>     '''
>     name Alice
>     age 25
>     '''
>     ```
>     
> - **.pop(key[,default]) : 키를 제거하고 연결됐던 값을 반환 (없으면 에러나 default를 반환)**
>     
>     ```python
>     person = {'name': 'Alice', 'age': 25}
>     
>     print(person.pop('age')) # 25
>     print(person) # {'name': 'alice'}
>     print(person.pop('country', None)) # None
>     print(person.pop('country')) # keyError
>     ```
>     
> - **.setdefault(key[,default]) : 키와 연결된 값을 반환**
>     
>     **키가 없다면 default와 연결한 키를 딕셔너리에 추가하고 default를 반환**
>     
>     ```python
>     person = {'name': 'Alice', 'age': 25}
>     
>     print(person.setdefault('country', 'KOREA')) # KOREA
>     print(person) # {'name': 'Alice', 'age': 25, 'country': 'Korea'}
>     ```
>     
> - **.update([other]) : other가 제공하는 키/ 값 쌍으로 딕셔너리를 갱신**
>     
>     **기존 키는 덮어씀**
>     
>     ```python
>     person = {'name': 'Alice', 'age': 25}
>     other_person = {'name': 'Jane', 'gender': 'Female'}
>     
>     person.update(other_person)
>     print(person) # {'name': 'Jane', 'age': 25, 'gender': 'Female'}
>     
>     person.update(age=50)
>     print(person) # {'name': 'Jane', 'age': 50, 'gender': 'Female'}
>     
>     person.update(country='KOREA')
>     print(person) # {'name': 'Jane', 'age': 50, 'gender': 'Female', 'country': 'KOREA'}
>     ```
>     

---

## 복사

### 개요

> **데이터 타입과 복사**
> 
> - 파이썬에서는 데이터 분류에 따라 복사가 달라짐
> - “변경 가능한 데이터 타입”과 “변경 불가능한 데이터 타입”을 다르게 다룸

> **변경 가능한 데이터 타입의 복사**
> 
> 
> ```python
> a = [1, 2, 3, 4]
> b = a
> b[0] = 100
> 
> print(a) # [100, 2, 3, 4]
> print(b) # [100, 2, 3, 4]
> ```
> 

> **변경 불가능한 데이터 타입의 복사**
> 
> 
> ```python
> a = 20
> b = a
> b = 10
> 
> print(a) # 20
> print(b) # 10
> ```
> 

---

### 복사 유형

> **복사 유형**
> 
> 1. 할당(Assignment)
> 2. 얕은 복사(Shallow copy)
> 3. 깊은 복사(Deep copy)

> **1 할당**
> 
> - 리스트 복사 예시
>     
>     ```python
>     original_list = [1, 2, 3]
>     copy_list = original_list
>     print(original_list, copy_list) # [1, 2, 3] [1, 2, 3]
>     
>     copy_list[0] = 'hi'
>     print(original_list, copy_list) # ['hi', 2, 3] ['hi', 2, 3]
>     ```
>     
>     - 할당 연산자(=)를 통한 복사는 해당 객체에 대한 객체 참조를 복사

> **2 얕은 복사**
> 
> - 리스트 얕은 복사 예시
>     
>     ```python
>     a = [1, 2, 3]
>     b = a[:]
>     print(a, b) # [1, 2, 3] [1, 2, 3]
>     
>     b[0] = 100
>     print(a, b) # [1, 2, 3] [100, 2, 3]
>     ```
>     
>     - 슬라이싱을 통해 생성된 객체는 원본 객체와 독립적으로 존재

> **2 얕은 복사의 한계**
> 
> - 2차원 리스트와 같이 변경가능한 객체 안에 변경 가능한 객체가 있는 경우
>     
>     ```python
>     a = [1, 2, [1, 2]]
>     b = a[:]
>     print(a, b) # [1, 2, [1, 2]] [1, 2, [1, 2]]
>     
>     b[2][0] = 100
>     print(a, b) # [1, 2, [100, 2]] [1, 2, [100, 2]]
>     ```
>     
>     - a 와 b의 주소는 다르지만 내부 객체의 주소는 같기 때문에 함께 변경됨

> **3 깊은 복사**
> 
> - 리스트 깊은 복사 예시
>     
>     ```python
>     import copy
>     
>     original_list = [1, 2, [1, 2]]
>     deep_copied_list = copy.deepcopy(original_list)
>     
>     deep_copied_list[2][0] = 100
>     
>     print(original_list) # [1, 2, [1, 2]]
>     print(deep_copied_list) # [1, 2, [100, 2]]
>     ```
>     
>     - 내부에 중첩된 모든 객체까지 새로운 객체 주소를 참조하도록 함

---
