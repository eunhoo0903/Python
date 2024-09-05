## 05-3 패키지

파이썬에서 패키지(packages)란 관련 있는 모듈의 집합을 말한다. 패키지는 파이썬 모듈을 계층적(디렉터리 구조)으로 관리할 수 있게 해 준다.

파이썬 패키지는 디렉터리와 파이썬 모듈로 이루어진다.

*가상의 game 패키지 예*

```
game/
    __init__.py
    sound/
        __init__.py
        echo.py
        wav.py
    graphic/
        __init__.py
        screen.py
        render.py
    play/
        __init__.py
        run.py
        test.py
```

game, sound, graphic, play는 디렉터리, 확장자가 .py인 파일은 파이썬 모듈이다. game 디렉터리가 이 패키지의 루트 디렉터리, sound, graphic, play는 서브 디렉터리이다.

간단한 파이썬 프로그램이 아니라면 이렇게 패키지 구조로 파이썬 프로그램을 만드는 것이 공동 작업이나 유지 보수 등 여러 면에서 유리하다.

## 패키지 만들기

이제 위 예와 비슷한 game 패키지를 직접 만들어 보자

1. `C:/doit` 디렉터리 밑에 game 패키지를 직접 만들어 보면서 패키지에 대해서 알아보자.

```
C:/doit/game/__init__.py
C:/doit/game/sound/__init__.py
C:/doit/game/sound/echo.py
C:/doit/game/graphic/__init__.py
C:/doit/game/graphic/render.py
```

2. 각 디렉터리에 `__init__.py` 파일을 만들어 놓기만 하고 일단 비워둔다.

3. echo.py 파일의 내용은 다음과 같이 작성한다.

```py
# echo.py
def echo_test():
    print("echo")
```

4. render.py 파일의 내용은 다음과 같이 작성한다.

```py
# render.py
def render_test():
    print("render")
```

5. 다음 예제를 수행하기 전에 우리가 만든 game 패키지를 참조할 수 있도록 명령 프롬프트 창에서 set 명령어로 PYTHONPATH 환경 변수에 `C:/doit` 디렉터리를 추가한다.

```
C:\> set PYTHONPATH=C:/doit
C:\> python
>>> 
```

## 패키지 안의 함수 실행하기

패키지를 사용하여 echo.py 파일의 echo_test 함수를 실행해 보자. 패키지 안의 함수를 실행하는 방법에는 3가지가 있다.

첫 번째는 echo 모듈을 import하여 실행하는 방법으로, 다음과 같이 실행한다.

> echo 모듈은 echo.py 파일이다.

```py
>>> import game.sound.echo
>>> game.sound.echo.ehco_test()
echo
```

두 번째는 echo 모듈이 있는 디렉터리까지를 `from ... import`하여 실행하는 방법이다.

```py
>>> exit()
C:\> python
>>> from game.sound import echo
>>> echo.echo_test()
echo
```

세 번째는 echo 모듈의 echo_test 함수를 직접 import하여 실행하는 방법이다.

```py
>>> from game.sound.echo import echo_test
>>> echo_test()
echo
```

하지만 다음과 같이 echo_test 함수를 사용하는 것은 불가능하다.

```
>>> import game
>>> game.sound.echo.echo_test()
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'sound'
```

import game을 수행하면 game 디렉터리의 `__init__.py`에 정의한 것만 참조할 수 있다.

또 다음처럼 echo_test 함수를 사용하는 것도 불가능하다.

```
>>> import game.sound.echo.echo_test
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'game.sound.echo.echo_test'; 'game.sound.echo' is not a package
```

도트 연산자(.)를 사용해서 `import a.b.c`처럼 import할 때 가장 마지막 항목인 c는 반드시 모듈 또는 패키지여야만 한다.

## __init__.py의 용도

`__init__.py` 파일은 해당 디렉터리가 패키지의 일부임을 알려주는 역할을 한다. 만약 game, sound, graphic 등 패키지에 포함된 디렉터리에 `__init__.py` 파일이 없다면 패키지로 인식되지 않는다.

또한, `__init__.py` 파일은 패키지와 관련된 설정이나 초기화 코드를 포함할 수 있다.

### 패키지 변수 및 함수 정의

패키지 수준에서 변수와 함수를 정의할 수 있다. 예를 들어, game 패키지의 `__init__.py` 파일에 공통 변수나 함수를 정의할 수 있다.

```py
# C:/doit/game/__init__.py
VERSION = 3.5

def print_version_info():
    print(f"The version of this game is {VERSION}.")
```

이렇게 패키지의 `__init__.py` 파일에 정의된 변수와 함수는 다음과 같이 사용할 수 있다.

```py
>>> import game
>>> print(game.VERSION)
3.5
>>> game.print_version_info()
The version of this game is 3.5.
```

### 패키지 내 모듈을 미리 import

`__init__.py` 파일에 패키지 내의 다른 모듈은 미리 import하여 패키지를 사용하는 코드에서 간편하게 접근할 수 있다.

```py
# C:/doit/game/__init__.py
from .graphic.render import render_test

VERSION = 3.5

def print_version_info():
    print(f"The version of this game is {VERSION}.")
```

> `from .graphic.render import render_test` 문장에서 `.graphic.render`에 사용한 맨 앞의 `.`은 현재 디렉터리를 의미한다.

이제 패키지를 사용하는 코드에서는 다음과 같이 간편하게 game 패키지를 통해 render_test 함수를 사용할 수 있다.

```py
>>> import game
>>> game.render_test()
render
```

### 패키지 초기화

`__init__.py` 파일에 패키지를 처음 불러올 때 실행되어야 하는 코드를 작성할 수 있다. (예. 데이터베이스 연결, 설정 파일 로드)

```py
# C:/doit/game/__init__.py
from .graphic.render import render_test

VERSION = 3.5

def print_version_info():
    print(f"The version of this game is {VERSION}.")

# 여기에 패키지 초기화 코드를 작성한다.
print("Initializing game ..")
```

이렇게 하면 패키지를 처음 import할 때 초기화 코드가 실행된다.

```py
>>> import game
Initializing game ...
```

game 패키지의 초기화 코드는 game 패키지의 하위 모듈의 함수를 import할 경우에도 실행된다.

```py
>>> from game.graphic.render import render_test
Initializing game ...
```

단, 초기화 코드는 한 번 실행된 후에는 다시 import를 수행하더라도 실행되지 않는다. 다음과 같이 game 패키지를 import한 후에 하위 모듈을 다시 import 하더라도 초기화 코드는 처음 한 번만 실행된다.

```py
>>> import game
Initializing game ...
>>> from game.graphic.render import render_test
```

### __all__

```py
>>> from game.sound import *
Initializing game ...
>>> echo.echo_test()
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
NameError: name 'echo' is not defined
```

game.sound 패키지에서 모든 것(`*`)을 import 했으므로 echo 모듈을 사용할 수 있어야 할 것 같은데, echo라는 이름이 정의되지 않았다는 오류가 발생했다.

특정 디렉터리의 모듈을 `*`를 사용하여 import할 때느느 다음과 같이 해당 디렉터리의 `__init__.py` 파일에 `__all__` 변수를 설정하고 import할 수 있는 모듈을 정의해 주어야 한다.

```py
# C:/doit/game/sound/__init__.py
__all__ = ['echo']
```

여기에서 `__all_`이 의미하는 것은 sound 디렉터리에서 `*`를 사용하여 import할 경우, 이곳에 정의된 echo 모듈만 import된다는 의미이다.

### relative 패키지

만약 graphic 디렉터리의 render.py 모듈에서 sound 디렉터리의 echo.py 모듈을 사용하고 싶다면 어떻게 해야 할까?

```py
# render.py
from game.sound.echo import echo_test
def render_test():
    print("render")
    echo_test()
```

`from game.sound.echo import echo_test` 문장을 추가하여 echo_test 함수를 사용할 수 있도록 수정했다.
