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