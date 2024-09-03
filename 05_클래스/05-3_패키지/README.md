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