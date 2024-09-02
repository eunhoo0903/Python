## 05-2 모듈

모듈이란 함수나 변수 또는 클래스를 모아 놓은 파이썬 파일이다. 모듈은 다른 파이썬 프로그램에서 불러와 사용할 수 있도록 만든 파이썬 파일이라고도 할 수 있다. 다른 사람들이 이미 만들어 놓은 모듈을 사용할 수도 있고 우리가 직접 만들어서 사용할 수도 있다.

## 모듈 만들기

```py
# mod1.py
def add(a, b):
    return a + b
def sub(a , b):
    return a - b
```

위와 같이 함수가 있는 파일을 만들자. 이 mod1.py가 바로 모듈이다.

## 모듈 불러오기

우리가 만든 mod1.py 파일, 즉 모듈을 파이썬에서 불러와 사용하려면 어떻게 해야 할까?

다음과 같이 따라해 보자.

```py
>>> import mod1
>>> print(mod1.add(3, 4))
7
>>> print(mod1.sub(4, 2))
```

mod1.py 모듈을 불러오기 위해 `import mod1`이라고 입력했다. import는 이미 만들어 놓은 파이썬 모듈을 사용할 수 있게 해 주는 명령어이다. mod1.py 파일에 있는 함수를 사용하려면 모듈 이름 뒤에 도트 연산자(.)를 붙이고 함수 이름을 쓰면 된다.

import의 사용 방법은 다음과 같다.

```
import 모듈_이름
```

여기에서 모듈 이름은 확장자를 제거한 mod1만 가리킨다.

때로는 모듈 이름 없이 함수 이름만 쓰고 싶은 경우도 있을 것이다.

```
from 모듈_이름 import 모듈_함수
```

위와 같이 함수를 직접 import하면 모듈 이름을 붙이지 않고 바로 해당 모듈의 함수를 쓸 수 있다.

```py
>>> from mod1 import add
>>> add(3, 4)
7
```

그런데 이렇게 하면 add 함수 하나만 사용할 수 있다. add와 sub 둘 다 모듈 이름을 붙이지 않고 사용하려면 어떻게 해야 할까?

2가지 방법이 있다.

```
from mod1 import add, sub
```

위와 같이 `from 모듈_이름 import 모듈_함수1, 모듈_함수2`처럼 사용하는 것이다.

```
from mod1 import *
```

`*`을 사용하는 방법도 있다. `*` 문자는 '모든 것'이라는 뜻인데, 파이썬에서도 같은 의미로 사용된다.

## if __name__ == "__main__":의 의미

mod1.py 파일을 다음과 같이 수정해 보자.

```py
def add(a, b):
    return a + b

def sub(a, b):
    return a - b

print(add(1, 4))
print(sub(4, 2))
```

`add(1, 4)`와 `sub(4, 2)`의 결과를 출력하는 문장을 추가했다.

```
C:\doit>python mod1.py
5
2
```

그런데 이 mod1.py 파일의 add와 sub 함수를 사용하기 위해 mod1 모듈을 import할 때는 조금 이상한 문제가 생긴다.

```
C:\doit> python
>>> import mod1
5
2
```

mod1.py 파일의 add와 sub 함수만 사용하려고 하면 어떻게 해야 할까?

```py
def add(a, b):
    return a + b

def sub(a, b):
    return a - b

if __name__ == "__main__":
    print(add(1, 4))
    print(sub(4, 2))
```

`if __name__ == "__main__"`을 사용하면 직접 이 파일을 실행했을 때 위 조건문이 참이 되어 if 문 다음 문장이 수행된다. 반대로 대화형 인터프리터나 다른 파일에서 이 모듈을 불러 사용할 때는 위 조건문이 거짓이 되어 if문 다음 문장이 수행되지 않는다.

```py
>>> import mod1
>>>
```

아무런 결괏값도 출력되지 않는다.
