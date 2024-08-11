## 02-5 딕셔너리 자료형

사람은 누구든지 "이름" = "홍길동", "생일" = "몇 월 며칠" 등과 같은 방식으로 그 사람이 가진 정보를 나타낼 수 있다. 파이썬은 이러한 대응 관계를 나타낼 수 있는 딕셔너리(dictionary) 자료형을 가지고 있다.

## 딕셔너리란?

딕셔너리는 단어 그대로 '사전'이라는 뜻이다. 딕셔너리는 Key와 Value를 한 쌍으로 가지는 자료형이다. 예컨대 Key가 "baseball" 이라면 Value는 "야구"가 될 것이다.

딕셔너리는 리스트나 튜플처럼 순차적으로 해당 요솟값을 구하지 않고 Key를 통해 Value를 얻는다. baseball이라는 단어의 뜻을 찾기 위해 baseball이라는 단어가 있는 곳만 펼쳐 보는 것이다.

## 딕셔너리는 어떻게 만들까?

다음은 딕셔너리의 기본 모습이다.

```
{Key1: Value1, Key2: Value2, Key3: Value3, ...}
```

Key와 Value의 쌍 여러 개가 {}로 둘러싸여 있다. 각각의 요소는 Key: Value 형태로 이루어져 있고 심표(,)로 구분되어 있다.

```python
>>> dic = {'name': 'pay', 'phone': '010-1234-5678', 'birth': '1118'}
```

위에서 Key는 각각 'name', 'phone', 'birth', 각각의 Key에 해당하는 Value는 'pey', '010-1234-5678', '1118'이 된다.

또한 다음 예 처럼 Key로 정숫값 1, Value로 문자열 'hi'를 사용하거나 Value에 리스트도 넣을 수 있다.

```python
>>> a = {1: 'hi'}
>>> b = {'a': [1, 2, 3]}
```

## 딕셔너리 쌍 추가, 삭제하기

딕셔너리 쌍을 추가 또는 삭제하는 방법을 알아보자.

### 딕셔너리 쌍 추가하기

```python
>>> a = {1: 'a'}
>>> a[2] = 'b'
>>> a
{1: 'a', 2: 'b'}
```

a[2] = 'b'와 같이 입력하면 딕셔너리 a에 Key와 Value가 각각 2와 'b'인 {2: 'b'} 딕셔너리 쌍이 추가된다.

```python
>>> a['name'] = 'pey'
>>> a
{1: 'a', 2: 'b', 'name': 'pey'}
```

딕셔너리 a에 {'name': 'pey'} 쌍이 추가되었다.

### 딕셔너리 요소 삭제하기

```python
>>> del a[1]
>>> a
{2: 'b', 'name': 'pey'}
```

del 함수를 사용해서 `del a [key]`를 입력하면 지정한 Key에 해당하는 {Key: Value} 쌍이 삭제된다.

## 딕셔너리를 사용하는 방법

딕셔너리는 주로 어떤 것을 표현하는 데 사용할까? 예를 들어 4명의 사람이 각자의 특기를 표현할 수 있는 좋은 방법에 대해서 생각해보자. 딕셔너리를 사용하면 이 상황을 표현하기가 정말 쉽다.

### 딕셔너리에 Key를 사용해 Value 얻기

```python
>>> grade = {'pay': 10, 'julliet': 99}
>>> grade['pey']
10
>>> grade['jullet']
99
```

딕셔너리는 Key를 사용해서 Value를 구하는 방법이 있다. 위 예에서 'pey'라는 Key의 Value를 얻기 위해 `grade['pey']`를 사용한 것처럼 어떤 key의 Value를 얻기 위해서는 '딕셔너리_변수_이름[key]'를 사용해야 한다.

### 딕셔너리를 만들 때 주의할 사항

딕셔너리에서 Key는 고유한 값이므로 중복되는 Key 값을 설정해 놓으면 하나를 제외한 나머지 것들이 모두 무시된다.

```python
>>> a = {1: 'a', 1: 'b'}
>>> a
{1: 'b'}
```

이렇게 Key가 중복되었을 때 1개를 제외한 나머지 Key:Value 값이 모두 무시되는 이유는 Key를 통해 Value를 얻는 딕셔너리의 특징 때문이다.

## 딕셔너리 관련 함수

### Key 리스트 만들기 - Keys

```python
>>> a = {'name': 'pey', 'phone': '010-1234-5678', 'birth': '1118'}
>>> a.keys()
dict_keys(['name', 'phone', 'birth'])
```

a.keys()는 딕셔너리 a의 Key만을 모아 dict_keys 객체를 리턴한다.

### Value 리스트 만들기 - values

```python
>>> a.values()
dict_values(['pey', '010-1234-5678', '1118'])
```

Value만 얻고 싶다면 values 함수를 사용하면 된다.

### Key, Value 쌍 얻기 - items

```python
>>> a.items()
dict_items([('name', 'pey'), ('phone', '010-1234-1234'), ('birth', '1118')])
```

items 함수는 Key와 Value의 쌍을 튜플로 묶은 값을 dict_items 객체로 리턴한다.

### Key: Value 쌍 모두 지우기 - clear

```python
>>> a.clear()
>>> a
{}
```

clear 함수는 딕셔너리 안의 모든 요소를 삭제한다.

### Key로 Value 얻기 - get

```python
>>> a = {'name': 'pey', 'phone': '010-1234-5678', 'birth': '1118'}
>>> a.get('name')
'pey'
>>> a.get('phone')
'010-9999-1234'
```

get(x) 함수는 x라는 Key에 대응되는 Value를 리턴한다.

### 해당 Key가 딕셔너리 안에 있는지 조사하기 - in

```python
>>> a = {'name':'pey', 'phone':'010-1234-5678', 'birth': '1118'}
>>> 'name' in a
True
>>> 'email' in a
False
```

'name' in a를 호출하면 참(True)을 리턴한다. 이와 반대로 'email'은 a 딕셔너리 안에 존재하지 않는 Key이므로 거짓(False)을 리턴한다.
