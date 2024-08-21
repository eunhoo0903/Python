## 04-2 사용자 입출력

프로그램은 사용자 입력에 따라 그에 맞는 출력을 내보낸다.

## 사용자 입력 활용하기

사용자가 입력한 값을 어떤 변수에 대입하고 싶을 때는 어떻게 해야 할까?

### input 사용하기

```python
>>> a = input()
Life is too short, you need python
>>> a
'Life is too short, you need python'
```

input은 사용자가 키보드로 입력한 모든 것을 문자열로 정한다.

### 프롬프트를 뜨워 사용자 입력받기

'숫자를 입력하세요' 등 안내 문구 또는 질문을 보여주고 싶을 때는 어떻게 할까?

```
input("안내_문구")
```

다음 예를 보자.

```python
>>> number = input("숫자를 입력하세요: ")
숫자를 입력하세요: 
```

괄호 안에 입력한 문구가 프롬프트로 나타난다.

'숫자를 입력하세요'라는 프롬프트 3을 입력하면 변수 number에 값 3이 대입된다.

```python
>>> number = input("숫자를 입력하세요: ")
숫자를 입력하세요: 3
>>> print(number)
3
```

input은 입력되는 모든것을 문자열로 취급하기 때문에 number는 숫자가 아닌 문자열이라는 것에 주의하자.

```python
>>> type(number)
<class 'str'>
```

## print 자세히 알기

데이터를 출력하는 print 문의 사용 예는 다음과 같다.

```python
>>> a = 123
>>> print(a)
123
>>> a = "Python"
>>> print(a)
Python
>>> a = [1, 2, 3]
>>> print(a)
[1, 2, 3]
```

### 큰따옴표로 둘러싸인 문자열은 + 연산과 동일하다

```python
>>> print("life" "is" "too short")  # 1번
lifeistoo short
>>> print("life"+"is"+"too short")  # 2번
lifeistoo short
```

### 문자열 띄어쓰기는 쉼표로 한다

```python
>>> print("life", "is", "too short")
life is too short
```

쉼표(,)를 사용하면 문자열을 띄어 쓸 수 있다.

### 한 줄에 결괏값 출력하기

03-3에서 for 문을 공부하면서 만든 구구단 프로그램에서 보았듯이 한 줄에 결괏값을 계속 이어서 출력하려면 매개변수 end를 사용하면 된다.

```python
>>> for i in range(10):
...     print(i, end=' ')
...
0 1 2 3 4 5 6 7 8 9 >>>
```

> end 매개변수의 초깃값은 줄바꿈(`\n`) 문자이다.