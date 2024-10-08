## 02-2 문자열 자료형

문자열(string)이란 연속된 문자들의 나열을 말한다.

```python
"Life is too short, You need Python"
"a"
"123"
```

모든 예문이 (")로 둘러싸여 있다. 따옴표로 둘러싸여 있으면 모두 문자열이라고 보면 된다.

### 문자열은 어떻게 만들고 사용할까?

앞에서는 문자열을 만들 때 큰따옴표만을 사용했지만, 이 밖에도 문자열을 만드는 방법은 3가지가 더 있다.

#### 1. 큰따옴표로 양쪽 둘러싸기

```python
"Hello World"
```

#### 2. 작은따옴표로 양쪽 둘러싸기

```python
'Python is fun'
```

#### 3. 큰따옴표 3개를 연속으로 써서 양쪽 둘러싸기

```python
"""Life is too short, You need python"""
```

#### 4. 작은따옴표 3개를 연속으로 써서 양쪽 둘러싸기

```python
'''Life is too short, You need python'''
```

### 문자열 안에 작은따옴표나 큰따옴표를 포함시키고 싶을 때

문자열을 만들어주는 주인공은 작은따옴표(')와 큰따옴표(")이다. 그런데 문자열 안에도 작은따옴표와 큰따옴표가 들어 있어야 할 경우가 있다. 이때는 좀 더 특별한 기술이 필요하다.

#### 1. 문자열에 작은따옴표 포함하기

```
Python's favorite food is perl
```

위와 같은 문자열을 food 변수에 저장하고 싶다고 가정해 보자. 문자열 중 Python's에 작은따옴표(')가 포함되어 있다.

이 경우에는 문자열은 큰따옴표로 둘러싸야 한다. 큰따옴표 안에 들어 있는 작은따옴표는 문자열을 나타내기 위한 기호로 인식되지 않는다.

```python
>>> food = "Python's favorite food is perl"
>>> food
"Python's favorite food is perl"
```

다음과 같이 문자열을 큰따옴표가 아닌 작은따옴표로 둘러싼다면 'Python'이 문자열로 인식되어 구문 오류(SyntaxError)가 발생한다.

```python
>>> food = 'Python's favorite food is perl'
  File "<stdin>", line 1
    food = 'Python's favorite food is perl'
                   ^
SyntaxError: invalid syntax
```

#### 2. 문자열에 큰따옴표 포함하기

```
"Python is very easy." he says.
```

위와 같이 큼따옴표가 포함된 문자열이라면, 작은따옴표로 둘러싸면 된다.

```python
>>> say = '"Python is very easy." he says.'
```

이렇게 작은따옴표 안에 사용되는 큰따옴표는 문자열을 만드는 기호로 인식되지 않는다.

### 여러 줄인 문자열을 변수에 대입하고 싶을 때

문자열이 항상 한 줄짜리만 있는 것은 아니다. 다음과 같은 여러 줄의 문자열을 변수에 대입하려면 어떻게 해야 할까?

```
Life is too short
You need python
```

#### 1. 줄을 바꾸기 위한 이스케이프 코드 `\n` 삽입하기

```python
>>> multiline = "Life is too short\nYou need python"
```

위 예처럼 줄바꿈 문자인 `\n`을 삽입하는 방법이 있지만, 읽기 불편하고 줄이 길어지는 단점이 있다.

#### 2. 연속된 작은따옴표 3개 또는 큰따옴표 3개 사용하기

1번 방법의 단점을 극복하기 위해 파이썬에서는 다음과 같이 작은따옴표 3개(''') 또는 큰따옴표 3개(""")를 사용한다.

```python
>>> multiline='''
    Life is too short
    You need python
    '''
```

작은따옴표 3개를 사용한 경우

```python
>>> multiline="""
    Life is too short
    You need python
    """
```

큰따옴표 3개를 사용한 경우

‘print(multiline)’을 입력하면 잘 출력되는것을 볼 수 있다.

```python
>>> print(multiline)
Life is too short
You need python
```

두 경우 모두 결과는 동일하다. 문자열이 여러 줄일 경우, 이스케이프 코드를 쓰는 것보다 따옴표 3개를 사용하는 것이 훨씬 깔끔하다.

### 문자열 연산하기

파이썬에서는 문자열을 더하거나 곱할 수 있다. 이는 다른 언어에서는 쉽게 찾아볼 수 없는 재미있는 기능이다. 문자열을 더하거나 곱하는 방법에 대해 알아보자.

#### 문자열 더해서 연결하기

```python
>>> head = "Python"
>>> tail = " is fun!"
>>> head + tail
'Python is fun!'
```

"Python"이라는 head 변수와 " is fun!"이라는 변수를 더한것이다. 결과는 `Python is fun!'이다. 즉, head와 tail 변수가 +에 의해 합쳐진 것이다.

#### 문자열 곱하기

```python
>>> a = "python"
>>> a * 2
'pythonpython'
```

위 소스 코드에서 `*`의 의미는 우리가 일반적으로 사용하는 숫자 곱하기의 의미와는 다르다. 위 소스 코드에서 `a * 2`라는 문장은 a를 2번 반복하라는 뜻이다. 즉, `*`는 문자열의 반복을 뜻하는 의미로 사용되었다.

### 문자열 길이 구하기

문자열의 길이는 다음과 같이 len 함수를 사용하면 구할 수 있다. len 함수는 print 함수처럼 파이썬 기본 내장 함수로, 별다른 설정 없이 바로 사용할 수 있다.

> 문자열의 길이에는 공백 문자도 포함.
```python
>>> a = "Life is too short"
>>> len(a)
17
```

### 문자열 인덱싱과 슬라이싱

인덱싱(indexing)이란 무엇인가를 '가리킨다', 슬라이싱(slicing)은 무엇인가를 '잘라 낸다'라는 의미이다.

#### 문자열 인덱싱

```python
>>> a = "Life is too short, You need Python"
```

위 코드에서 변수 a에 저장한 문자열의 각 문자마다 번호를 매겨 보면 다음과 같다.

![indexing](./02_2_indexing.png?raw=true)

"Life is too short, You need Python" 문자열에서 L은 첫 번째 자리를 뜻하는 숫자 0, i는 1 이런식으로 계속 번호를 붙인 것이다.

다음 예를 실행하면

```python
>>> a = "Life is too short, You need Python"
>>> a[3]
'e'
```

a[3]이 뜻하는 것은 a라는 문자열의 네 번째 문자 e를 말한다. a[3]에서 숫자 3이 왜 네 번째 문자를 뜻할까? 

**"파이썬은 0부터 숫자를 센다."**

따라서 파이썬은 위 문자열을 다음과 같이 바라보고 있다.

```python
a[0]: 'L', a[1]: 'i', a[2]: 'f', a[3]: 'e', a[4]: ' ', ...
```

위 예에서 볼 수 있듯이 a[번호]는 문자열 안의 특정한 값을 뽑아 내는 역할을 한다. 이러한 작업을 '인덱싱'이라고 한다.

#### 문자열 인덱싱 활용하기

```python
>>> a = "Life is too short, You need Python"
>>> a[0]
'L'
>>> a[12]
's'
>>> a[-1]
'n'
```

마지막의 a[-1]이 뜻하는 것은 뭘까? 문자열을 뒤에서부터 읽기 위해 -(빼기) 기호를 붙인 것이다. 즉, a[-1]은 뒤에서부터 세어 첫 번째가 되는 문자를 말한다.

```python
>>> a[-0]
'L'
>>> a[-2]
'o'
>>> a[-5]
'y'
```

0과 0은 똑같은 것이기 때문에 a[-0]은 a[0]과 똑같은 값을 보여준다. 두 번째 예는 뒤에서부터 두 번째 문자, 세 번째 예는 뒤에서부터 다섯 번째 문자를 가리키는 것이다.

#### 문자열 슬라이싱

그렇다면 "Life is too short, You need Python" 문자열에서 단순히 한 문자만 뽑아 내는 것이 아니라 'Life' 또는 'You'와 같은 단어를 뽑아 내는 방법은 없을까?

바로 슬라이싱(slicing) 기법을 사용하면 된다.

> 인덱싱 기법과 슬라이싱 기법은 뒤에서 배울 자료형인 리스트나 튜플에서도 사용 가능
```python
>>> a = "Life is too short, You need Python"
>>> a[0:4]
'Life'
```

a[0:4]는 a 문자열, 즉 "Life is too short, You need Python" 문자열에서 자리 번호 0부터 4까지의 문자를 뽑아 낸다는 뜻이다.

슬라이싱 기법을 사용할 때 주의해야 할 점은 a[시작_번호:끝_번호]를 지정할 때 끝 번호에 해당하는 문자는 포함하지 않는다. 즉, a[0:3]을 수식으로 나타내면 다음과 같다.

```python
0 <= a < 3
```

이 수식을 만족하는 것은 a[0], a[1], a[2]이다. 따라서 a[0:3]은 'Lif', a[0:4]는 'Life'가 되는 것이다.

#### 문자열 슬라이싱 활용하기

슬라이싱할 때 항상 시작 번호가 0일 필요는 없다.

```python
>>> a[0:2]
'Li'
>>> a[5:7]
'is'
>>> a[12:17]
'short'
```

a[시작_번호:끝_번호]에서 끝 번호 부분을 생략하면 시작 번호부터 그 문자열 끝까지 뽑아 낸다.

```python
>>> a[19:]
'You need Python'
```

a[시작_번호:끝_번호]에서 시작 번호를 생략하면 문자열의 처음부터 문자열의 처음부터 끝 번호까지 뽑아 낸다.

```python
>>> a[:17]
'Life is too short'
```

a[시작_번호:끝_번호]에서 시작 번호와 끝 번호를 생략하면 문자열의 처음부터 끝까지 뽑아낸다.

```python
>>> a[:]
'Life is too short, You need Python'
```

슬라이싱에서도 인덱싱과 마찬가지로 -(빼기) 기호를 사용할 수 있다.

```python
>>> a[19:-7]
'You need'
```

a[19:-7]은 a[19]에서 a[-8]까지를 의미한다. 이때에도 a[-7]은 포함하지 않는다.

#### 슬라이싱으로 문자열 나누기

다음은 자주 사용하는 슬라이싱 기법 중 하나이다.

```python
>>> a = "20230331Rainy"
>>> date = a[:8]
>>> weather = a[8:]
>>> date
'20230331'
>>> weather
'Rainy'
```

위 예는 문자열 a를 두 부분으로 나누는 기법이다. 숫자 8을 기준으로 문자열 a를 양쪽으로 한 번씩 슬라이싱했다. 위 예에서는 "20230331Rainy" 문자열을 날짜를 나타내는 부분인 '20230331'과 날씨를 나타내는 부분인 'Rainy'로 나누는 방법이다.

인덱싱과 슬라이싱은 프로그래밍할 때 자주 사용하는 기법이다.

### 문자열 포매팅이란?

문자열 안의 특정한 값을 바꿔야 할 경우가 있을 때 이것을 가능하게 해 주는 것이 바로 '문자열 포매팅(string formatting)'이다.

#### f 문자열 포매팅

다음과 같이 문자열 앞에 f 접두사를 붙이면 f 문자열 포매팅 기능을 사용할 수 있다.

```python
>>> name = "홍길동"
>>> age = 30
>>> f'나의 이름은 {name}입니다. 나이는 {age}입니다.'
'나의 이름은 홍길동입니다. 나이는 30입니다.'
```

f 문자열 포매팅은 위와 같이 name, age와 같은 변숫값을 생성한 후에 그 값을 참조할 수 있다. 또한 문자열 포매팅은 표현식을 지원하기 때문에 다음과 같은 것도 가능하다.

> 표현식이란 중괄호 안의 변수를 계산식과 함께 사용하는 것을 말한다.

```python
>>> age = 30
>>> f'나는 내년이면 {age + 1}살이 된다.'
'나는 내년이면 31살이 된다.'
```

딕셔너리는 f 문자열 포매팅에서 다음과 같이 사용할 수 있다.

```python
>>> d = {'name': '홍길동', 'age': 30}
>>> f'나의 이름은 {d["name"]}입니다. 나이는 {d["age"]}입니다.'
'나의 이름은 홍길동입니다. 나이는 30입니다.'
```

> 딕셔너리는 key와 Value라는 것을 한 쌍으로 가지는 자료형이다. (02-5)

소수점은 다음과 같이 표현할 수 있다.

```python
>>> y = 3.42134234
>>> f'{y:0.4f}' # 소수점 4자리까지만 표현
'3.4213'
>>> f'{y:10.4f}' # 소수점 4자리까지 표현하고 총 자리수를 10으로 맞춤
'    3.4213'
```

f 문자열에서 `{}`를 문자 그대로 표시하려면 다음과 같이 2개를 동시에 사용해야 한다.

```python
>>> f'{{ and }}'
'{ and }'
```

지금까지는 문자열을 가지고 할 수 있는 기본적인 것에 대해 공부했다. 이제부터는 문자열을 좀 더 자유자재로 다루기 위해 알아야 할 것을 알아보자.

### 문자열 관련 함수들

문자열 자료형은 자체적으로 함수를 가지고 있다. 이들 함수를 다른 말로 '문자열 내장 함수'라고 한다. 이 내장 함수를 사용하려면 문자열 변수 이름 뒤에 '.'를 붙인 후 함수 이름을 써 주면 된다.

#### 문자 개수 세기 - count

```python
>>> a = "hobby"
>>> a.count('b')
2
```

count 함수로 문자열 중 문자 b의 개수를 리턴했다.

#### 위치 알려 주기 1 - find

```python
>>> a = "Python is the best choice"
>>> a.find('b')
14
>>> a.find('k')
-1
```

find 함수로 문자열 중 문자 b가 처음으로 나온 위치를 반환했다. 만약 찾는 문자나 문자열이 존재하지 않는다면 -1을 반환한다.

> 파이썬은 숫자를 0부터 세기 때문에 b의 위치는 15가 아닌 14가 된다.

#### 위치 알려 주기 2 - index

```python
>>> a = "Life is too short"
>>> a.index('t')
8
>>> a.index('k')
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ValueError: substring not found
```

index 함수로 문자열 중 문자 t가 맨 처음으로 나온 위치를 반환했다. 만약 찾는 문자나 문자열이 존재하지 않는다면 오류가 발생한다.

#### 문자열 삽입 - join

```python
>>> ",".join(['a', 'b', 'c', 'd'])
'a, b, c, d'
```

join 함수로 abcd 문자열의 각각의 문자 사이에 ','를 삽입했다.

#### 소문자를 대문자로 바꾸기 - upper

```python
>>> a = "hi"
>>> a.upper()
'HI'
```

upper 함수는 소문자를 대문자로 바꾸어 준다.

#### 대문자를 소문자로 바꾸기 - lower

```python
>>> a = "HI"
>>> a.lower()
'hi'
```

#### 왼쪽 공백 지우기 - lstrip

```python
>>> a = " hi "
>>> a.lstrip()
'hi '
```

lstrip 함수는 문자열 중 가장 왼쪽에 있는 한 칸 이상의 연속된 공백들을 모두 지운다.

#### 오른쪽 공백 지우기 - rstrip

```python
>>> a = " hi "
>>> a.rstrip()
' hi'
```

rstrip 함수는 문자열 중 가장 오른쪽에 있는 한 칸 이상의 연속된 공백을 모두 지운다.

#### 양쪽 공백 지우기 - strip

```python
>>> a = " hi "
>>> a.strip()
'hi'
```

strip 함수는 문자열 양쪽에 있는 한 칸 이상의 연속되 공백을 모두 지운다.

#### 문자열 바꾸기 - replace

```python
>>> a = "Life is too short"
>>> a.replace("Life", "Your leg")
'Your leg is too short'
```

replace 함수는 replace(바뀔_문자열, 바꿀_문자열)처럼 사용해서 문자열 안의 특정한 값을 다른 값으로 치환해 준다.

#### 문자열 나누기 - split

```python
>>> a = "Life is too short"
>>> a.split()
['Life', 'is', 'too', 'short']
>>> b = "a:b:c:d"
>>> b.split(':')
['a', 'b', 'c', 'd']
```

split 함수는 a.split()처럼 괄호 안에 아무 값도 넣어 주지 않으면 공백을 기준으로 문자열을 나눈다. 만약 b.split(':')처럼 괄호 안에 특정 값이 있을 경우에는 괄호 안의 값을 구분자로 해서 문자열을 나누어 준다.

앞에서 정리한 문자열 관련 함수는 문자열 처리에서 사용 빈도가 매우 높고 유용하다.



