## 04-4 프로그램의 입출력

명령 프롬프트를 사용해 본 사람이라면 다음과 같은 명령어를 사용해 봤을 것이다.

```
C:\> type a.txt
```

type은 바로 뒤에 적힌 파일 이름을 인수로 받아 해당 파일의 내용을 출력해 주는 명령어이다. 

```
명령어 [인수1, 인수2 ...]
```

이러한 기능을 파이썬 프로그램에도 적용할 수 있다.

## sys 모듈 사용하기

파이썬에서는 sys 모듈을 사용하여 프로그램에 인수를 전달할 수 있다.

```python
import sys

args = sys.argv[1:]
for i in args:
    print(i)
```

위는 프로그램 실행 시 전달받는 인수를 for 문을 사용해 차례대로 하나씩 출력하는 예이다. sys 모듈의 argv는 프로그램 실행 시 전달된 인수를 의미한다. argv[0]은 파일 이름 sys1.py가 되고 argv[1]부터는 뒤에 따라오는 인수가 차례대로 argv의 요소가 된다.

```
C:\python>python sys1.py aaa bbb ccc
aaa
bbb
ccc
```

위 예를 응용하여 간단한 프로그램을 만들어 보자.

```python
import sys
args = sys.argv[1:]
for i in args:
    print(i.upper(), end=' ')
```

문자열 관련 함수인 upper()를 사용하여 프로그램 실행 시 전달된 인수를 모두 대문자로 바꿔주는 간단한 프로그램이다.


```
C:\doit>python sys2.py life is too short, you need python
LIFE IS TOO SHORT, YOU NEED PYTHON
```
