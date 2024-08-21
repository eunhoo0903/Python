## 04-3 파일 읽고 쓰기

파일을 통한 입출력 방법에 대해 알아보자.

## 파일 생성하기

```python
f = open("새파일.txt", 'w')
f.close()
```

프로그램을 실행한 디렉터리에 새로운 파일이 하나 생성된 것을 확인할 수 있다. 파이썬 내장 함수 open을 사용했다. open 함수는 다음과 같이 '파일 이름'과 '파일 열기 모드'를 입력값으로 받고 결괏값으로 파일 객체를 리턴한다.

```
파일_객체 = open(파일_이름, 파일_열기_모드)
```

|파일열기모드|설명|
|---|---|
|r|읽기 모드: 파일을 읽기만 할 때 사용한다.|
|w|쓰기 모드: 파일에 내용을 쓸 때 사용한다.|
|a|추가 모드: 파일의 마지막에 새로운 내용을 추가할 때 사용한다.|

파일을 쓰기 모드로 열면 해당 파일이 이미 존재할 경우 원래 있던 내용이 모두 사라지고 해당 파일이 존재하지 않으면 새로운 파일이 생성된다.

만약 '새파일.txt' 파일을 `C:doit` 디렉터리에 생성하고 싶다면 다음과 같이 작성해야 한다. 

```python
f = open("C:/doit/새파일.txt", 'w')
f.close()
```

위 예에서 f.close()는 열려 있는 파일 객체를 닫아 주는 역할은 한다.

## 파일을 쓰기 모드로 열어 내용 쓰기

파일을 쓰기 모드로 열기만 했을 뿐, 정작 아무것도 쓰지는 않았다.

```python
f = open("C:/doit/새파일.txt", 'w')
for i in range(1, 11):
    data = f"{i}번째 줄입니다.\n"
    f.write(data)
f.close()
```

위 프로그램을 다음과 비교해 보자.

```python
for i in range(1, 11):
    data = f"{i}번째 줄입니다.\n"
    f.write(data)
```

두 프로그램의 다른 점은 data를 출력하는 방법이다. 첫 번째는 모니터 화면 대신 파일에 데이터를 적는 방법, 두 번째는 우리가 계속 사용해 왔던 모니터 화면에 데이터를 출력하는 방법이다.

## 파일을 읽는 여러 가지 방법

### readline 함수 이용하기

```python
f = open("C:/doit/새파일.txt", 'r')
line = f.readline()
print(line)
f.close()
```

위는 '새파일.txt' 파일을 읽기 모드로 연 후 readline()을 사용해서 파일의 첫번 째 줄을 읽어 출력하는 예제이다.

```
1번째 줄입니다.
```

모든 줄을 읽어 화면에 출력하고 싶다면 다음과 같이 작성하면 된다.

```python
f = open("C:/doit/새파일.txt", 'r')
while True:
    line = f.readline()
    if not line: break
    print(line)
f.close()
```

`while True:` 무한 루프 안에서 `f.readline()`을 사용해 파일을 계속 한 줄씩 읽어 들인다.

### readlines 함수 사용하기

```python
f = open("C:/doit/새파일.txt", 'r')
lines = f.readlines()
for line in lines:
    print(line)
f.close()
```

readlines 함수는 파일의 모든 줄을 읽어서 각각의 줄을 요소로 가지는 리스트를 리턴한다.

### read 함수 사용하기

```python
f = open("C:/doit/새파일.txt", 'r')
data = f.read()
print(data)
f.close()
```

`f.read()`는 파일의 내용 전체를 문자열로 리턴한다.

### 파일 객체를 for 문과 함께 사용하기

```python
f = open("C:/doit/새파일.txt", 'r')
for line in f:
    print(line)
f.close()
```

파일 객체(f)는 기본적으로 위와 같이 for 문과 함께 사용하여 파일을 줄 단위로 읽을 수 있다.

## 파일에 새로운 내용 추가하기

쓰기 모드('w')로 파일을 열 때 이미 존재하는 파일을 열면 그 파일의 내용이 모두 사라지게 된다. 하지만 원래 있던 값을 유지하면서 단지 새로운 값만 추가해야 할 경우도 있다.

```python
f = open("C:/doit/새파일.txt",'a')
for i in range(11, 20):
    data = "%d번째 줄입니다.\n" % i
    f.write(data)
f.close()
```

새파일.txt 파일을 추가 모드('a')로 열고 write를 사용해서 결괏값을 기존 파일에 추가해 적는 예이다.

## with 문과 함께 사용하기

파일을 열면(open) 항상 닫아(close) 주어야 한다. 이렇게 파일을 열고 닫는 것을 자동으로 처리할 수 있다면 편리하지 않을까?

```python
with open("foo.txt", "w") as f:
    f.write("Life is too short, you need python")
```

위와 같이 with 문을 사용하면 with 블록을 벗어나는 순간, 열린 파일 객체 f가 자동으로 닫힌다.