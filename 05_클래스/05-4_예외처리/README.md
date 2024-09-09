## 05-4 예외 처리

파이썬에서 오류를 처리하는 방법은 뭐가 있을까?

## 오류는 언제 발생하는가?

어떤 상황에서 오류가 발생할까? 실제 프로그램에서 자주 발생하는 오류를 중심으로 살펴보자.

먼저 존재하지 않는 파일을 사용하려고 시도했을 때 발생하는 오류이다.

```py
>>> f = open("없는파일", 'r')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
FileNotFoundError: [Errno 2] No such file or directory: '없는파일'
```

0으로 다른 숫자를 나누는 경우 역시 자주 발생하는 오류이다.

```py
>>> 4 / 0
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero
```

다음 오류는 정말 빈번하게 일어난다.

```py
>>> a = [1, 2, 3]
>>> a[3]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```

a[3]은 a의 네 번째 요솟값을 가리키는데, a 리스트에는 값이 3개밖에 없으므로([1, 2, 3]) 값을 얻을 수 없다.

## 오류 예외 처리 기법

### try-except 문

다음은 오류를 처리하기 위한 try-except 문의 기본 구조이다.

```py
try:
    ...
except [발생오류 [as 오류변수]]:
    ...
```

try 블록 수행 중 오류가 발생하면 except 블록이 수행된다. 하지만 try 블록에서 오류가 발생하지 않는다면 except 블록은 수행되지 않는다.

```
except [발생오류 [as 오류변수]]:
```

위 구문을 보면 []를 사용하는데, 이 기호는 괄호 안의 내용을 생략할 수 있다는 관례적인 표기법이다. 즉, except 구문은 다음 3가지 방법으로 사용할 수 있다.

#### 1. try-except만 쓰는 방법

```py
try:
    ...
except:
    ...
```

이 경우에는 오류의 종류에 상관없이 오류가 발생하면 except 블록을 수행한다.

#### 2. 발생 오류만 포함한 except 문

```py
try:
    ...
except 발생오류:
    ...
```

이 경우는 오류가 발생했을 때 except 문에 미리 정해 놓은 오류와 동일한 오류일 경우에만 except 블록을 수행한다.

#### 3. 발생 오류와 오류 변수까지 포함한 except 문

```py
try:
    ...
except 발생오류 as 오류변수:
    ...
```

이 경우에는 두 번째 경우에서 오류의 내용까지 알고 싶을 때 사용하는 방법이다.

예를 들어 보면 다음과 같다.

```py
try:
    4 / 0
except ZeroDivisionError as e:
    print(e)
```

위처럼 4를 0으로 나누려고 하면 ZeroDivisionError가 발생하여 except 블록이 실행되고 변수 e에 담기는 오류 메시지를 출력할 수 있다.

```
division by zero
```

### try-finally 문

try 문에는 finally 절을 사용할 수 있다. finally 절은 try 문 수행 도중 예외 발생 여부에 상관없이 항상 수행된다.

```py
try:
    f = open('foo.txt', 'w')
    # 무언가를 수행한다.

    # (...생략...)
finally:
    f.close() # 중간에 오류가 발생하더라도 무조건 실행한다.
```

foo.txt 파일을 쓰기 모드로 연 후 예외 발생 여부에 상관없이 항상 파일을 닫아 주려면 try-finally 문을 사용하면 된다.

### 여러 개의 오류 처리하기

try 문 안에서 여러 개의 오류를 처리하려면 다음과 같이 사용해야 한다.

```py
try:
    ...
except 발생오류1:
    ...
except 발생오류2:
    ...
```

즉, 0으로 나누는 오류와 인덱싱 오류를 다음과 같이 처리할 수 있다.

```py
try:
    a = [1, 2]
    print(a[3])
    4/0
except ZeroDivisionError:
    print("0으로 나눌 수 없습니다.")
except IndexError:
    print("인덱싱 할 수 없습니다.")
```

### try-else 문

try 문에는 다음처럼 else 절을 사용할 수도 있다.

```py
try:
    ...
except [발생오류 [as 오류변수]]:
    ...
else: # 오류가 없을 경우에만 수행
    ...
```

try 문 수행중 오류가 발생하면 except 절, 오류가 발생하지 않으면 else 절이 수행된다.

다음은 try 문에 else 절을 사용한 간단한 예제이다.

```py
try:
    age = int(input('나이를 입력하세요:'))
except:
    print('입력이 정확하지 않습니다.')
else:
    if age <= 18:
        print('미성년자는 출입금지입니다.')
    else:
        print('환영합니다.')
```

만약 '나이를 입력하세요:'라는 질문에 숫자가 아닌 다른 값을 입력하면 오류가 발생하여 '입력이 정확하지 않습니다.'라는 문장을 출력한다. 오류가 없을 경우에만 else 절이 수행된다.

## 오류 회피하기

코드를 작성하다 보면 특정 오류가 발생할 경우 그냥 통과시켜야 할 때가 있다. 

```py
try:
    f = open('없는파일', 'r')
except FileNotFoundError:
    pass
```

## 오류 일부러 발생시키기

프로그래밍을 하다 보면 종종 오류를 일부러 발생시켜야 할 경우도 생긴다. 파이썬은 raise 명령어를 사용해 오류를 강제로 발생시킬 수 있다.

예를 들어 Bird 클래스를 상속받는 자식 클래스는 반드시 fly라는 함수를 구현하도록 만들고 싶은 경우가 있을 수 있다.

```py
class Bird:
    def fly(self):
        raise NotImplementedError
```

BIrd 클래스를 상속받는 자식 클래스는 반드시 fly 함수를 구현해야 한다는 의지를 보여 준다. 만약 자식 클래스가 fly 함수를 구현하지 않은 상태로 fly 함수를 호출한다면 어떻게 될까?

```py
class Eagle(Bird):
    pass

eagle = Eagle()
eagle.fly()
```

Eagle 클래스는 Bird 클래스를 상속받았다. 그런데 Eagle 클래스는 fly 메서드를 오버라이딩 하여 구현하지 않았다 따라서 eagle 객체의 fly 메서드를 수행하는 순간 Bird 클래스의 fly 메서드가 수행되어 NotImplementedError가 발생한다.

오류가 발생하지 않게 하려면 다음과 같이 Eagle 클래스에 fly 함수를 구현해야 한다.

```py
class Eagle(Bird):
    def fly(self):
        print("very fast")

eagle = Eagle()
eagle.fly()
```

위 예처럼 fly 함수를 구현한 후 프로그램을 실행하면 오류 없이 다음 문장이 출력된다.

```
very fast
```
