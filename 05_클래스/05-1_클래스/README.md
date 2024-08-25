## 05-1 클래스

클래스가 무엇인지, 클래스가 왜 필요한지 매우 기초적인 것부터 차근차근 함께 알아보자.

## 클래스는 왜 필요한가?

가장 많이 사용하는 언어 중 하나인 C 언어에는 클래스가 없다. 이 말은 굳이 클래스가 없어도 프로그램을 충분히 만들 수 있다는 뜻이다. 클래스는 지금까지 공부한 함수나 자료형처럼 프로그램 작성을 위해 꼭 필요한 요소는 아니다.

하지만 프로그램을 작성할 때 클래스를 사용하면 얻을 수 있는 이익은 많다.

### 계산기 프로그램을 만들며 클래스 알아보기

계산기에 숫자 3을 입력하고 +를 입력한 후 4를 입력하면 결괏값으로 7을 보여준다. 다시 한번 +를 입력한 후 3을 입력하면 기존 결괏값에 3을 더해 10을 보여준다. 즉, 계산기는 이전에 계산한 결괏값을 항상 메모리 어딘가에 저장하고 있다.

이러한 내용을 함수를 이용해 구현해 보자.

```py
result = 0

def add(num):
    global result
    result += num
    return result

print(add(3))
print(add(4))
```

입력값을 이전에 계산한 결괏값에서 더한 후 리턴하는 add 함수를 위와 같이 작성했다. 프로그램을 실행하면 예상한 대로 다음과 같은 결괏값이 출력된다.

```
3
7
```

만일 한 프로그램에서 2대의 계산기가 필요한 상황이 발생하면 어떻게 해야 할까? 각 계산기는 각각의 값을 유지해야 하므로 위와 같이 add 함수 하나만으로는 값을 따로 유지할 수 없다.

이런 상황을 해결하려면 함수를 각각 따로 만들어야 한다.

하지만 계산기가 3개, 5개, 10개로 점점 더 많이 필요해진다면 어떻게 해야 할까? 계산기마다 빼기나 곱하기와 같은 기능을 추가해야 한다면 상황은 더 어려워질 것이다.

위와 같은 경우 클래스를 사용하면 다음과 같이 간단하게 해결할 수 있다.

```py
class Calculator:
    def __init__(self):
        self.result = 0
    
    def add(self, num):
        self.result += num
        return self.result

cal1 = Calculator()
cal2 = Calculator()

print(cal1.add(3))
print(cal1.add(4))
print(cal2.add(3))
print(cal2.add(7))
```

프로그램을 실행하면 함수 2개를 사용했을 때와 동일한 결과가 출력된다.

```
3
7
3
10
```

클래스로 만든 별개의 계산기 cal1, cal2(객체)가 각각의 역할을 수행한다. 이렇게 클래스를 사용하면 계산기가 대수가 늘어나도 객체를 생성하면 되므로 함수만 사용할 때보다 간단하게 프로그램을 작성할 수 있다.

## 클래스와 객체

클래스를 가장 잘 설명해주는 과자를 만드는 과자 틀과 이를 사용해 만든 과자로 알아보자.

- 과자 틀 = 클래스
- 과자 틀로 찍어 낸 과자 = 객체

클래스는 과자 틀과 비슷하다. 클래스(class)란 똑같은 무언가를 계속 만들어 낼 수 있는 설계 도면 (과자 틀), 객체(object)란 클래스로 만든 피조물(과자 틀로 찍어 낸 과자)를 뜻한다.

클래스로 만든 객체는 중요한 특징이 있다. 객체마다 고유한 성격을 가진다는 것이다. 과자에 구멍을 뚫거나 조금 베어 먹더라도 다른 과자에는 아무 영향이 없듯이, 클래스로 만든 객체들은 서로 전혀 영향을 주지 않는다.

파이썬 클래스의 가장 간단한 예이다.

```py
>>> class Cookie:
...     pass
...
>>>
```

위에서 작성한 Cookie 클래스는 아무런 기능도 가지고 있지 않은 껍질뿐인 클래스이다. 하지만 껍질뿐인 클래스도 객체를 생성하는 기능이 있다.

객체는 클래스로 만들고 1개의 클래스는 무수히 많은 객체를 만들어 낼 수 있다.

```py
>>> a = Cookie()
>>> b = Cookie()
```

Cookie()의 결괏값을 리턴받은 a와 b가 바로 객체이다.

## 사칙 연산 클래스 만들기

클래스를 직접 만들며 배워 보자.

### 클래스를 어떻게 만들지 먼저 구상하기

클래스로 만든 객체를 중심으로 어떤 식으로 동작하게 할지 미리 구상한 후 하나씩 만들면서 완성해 나가는 것이 좋다.

사칙 연산 기능을 가진 FourCal 클래스가 다음처럼 동작한다고 가정해 보자.

먼저 a = FourCal()를 입력해서 a라는 객체를 만든다.

```py
>>> a = FourCal()
```

다음 `a.setdata(4, 2)`처럼 입력해서 숫자 4와 2를 지정해 준다.

```py
>>> a.setdata(4, 2)
```

a.add()를 수행하면 두 수를 합한 결과(`4 + 2`)를 리턴한다.

```py
>>> a.add()
6
```

a.mul()를 수행하면 두 수를 곱한 결과(`4 * 2`)를 리턴한다.

```py
>>> a.mul()
8
```

a.sub()를 수행하면 두 수를 뺀 결과(`4 - 2`)를 리턴한다.

```py
>>> a.sub()
2
```

a.div()를 수행하면 두 수를 나눈 결과(`4 / 2`)를 리턴한다.

```py
>>> a.div()
2
```

### 클래스 구조 만들기

앞에서 구상한 것처럼 동작하는 클래스를 만들어 보자. 제일 먼저 할 일은 객체를 만들 수 있게 하는 것이다.

```py
>>> class FourCal:
...     pass
```

pass라는 문장만을 포함한 FourCal 클래스를 만든다.

> pass는 아무것도 수행하지 않는 문법으로, 임시로 코드를 작성할 때 주로 사용

### 객체에 연산할 숫자 지정하기

생성된 객체는 아직 아무런 기능도 하지 못한다. 이제 사칙 연산 기능을 하는 객체를 만들어야 한다. 이러한 기능을 갖춘 객체를 만들려면 먼저 사칙 연산을 할 때 사용할 2개의 숫자를 a 객체에게 알려 주어야 한다.

```py
>>> a.setdata(4, 2)
```

위 문장이 동작하려면 다음과 같이 FourCal 클래스를 다시 정의해야 한다.

```py
>>> class FourCal:
...     def setdata(self, first, second):
...     self.first = first
...     self.second = second
```

FourCal 클래스에서 setdata 함수를 정의했다. 클래스 안에 구현된 함수는 다른 말로 메서드(method)라고 부른다.

#### setdata 메서드의 매개변수

setdata 메서드를 좀 더 자세히 살펴보자. setdata 메서드는 매개변수로 self, first, second 3개의 입력값을 받는다. 메서드의 첫 번째 매개변수 self는 특별한 의미를 가진다.

a 객체를 만들고 a 객체를 통해 setdata 메서드를 호출해 보자.

```py
>>> a = FourCal()
>>> a.setdata(4, 2)
```

`a.setdata(4, 2)`처럼 호출하면 setdata 메서드의 첫 번째 매개변수 self에는 setdata 메서드를 호출한 객체 a가 자동으로 전달된다.

#### setdata 메서드의 수행문

```py
def setdata(self, first, second):   # 메서드의 매개변수
    self.first = first              # 메서드의 수행문
    self.second = second            # 메서드의 수행문
```

`a.setdata(4, 2)`처럼 호출하면 setdata 메서드의 매개변수 first, second에는 각각 값 4와 2가 전달되어 setdata 메서드의 수행문이 다음과 같이 해석된다.

```py
self.first = 4
self.second = 2
```

`a.first = 4`라는 문장이 수행되면 a 객체에 객체변수 first가 생성되고 4라는 값이 저장된다. `a.second`도 마찬가지이다.

### 더하기 기능 만들기

숫자를 더하는 기능을 방금 만들 클래스에 추가해 보자.

```py
>>> a = FourCal()
>>> a.setdata(4, 2)
>>> a.add()
6
```

이 연산이 가능하도록 FourCal 클래스를 다시 작성해 보자.

```py
>>> class FourCal:
...     def setdata(self, first, second):
...         self.first = first
...         self.second = second
...     def add(self):
...         result = self.first + self.second
...         return result
```

이제 클래스를 사용해 보자

```py
>>> a = FourCal()
>>> a.setdata(4, 2)
>>> a.add()
6
```

앞에서 살펴보았듯이 a 객체의 first, second 객체 변수에는 각각 값 4와 2가 저장된다.

### 곱하기, 빼기, 나누기 기능 만들기

```py
>>> class FourCal:
...     def setdata(self, first, second):
...         self.first = first
...         self.second = second
...     def add(self):
...         result = self.first + self.second
...         return result
...     def mul(self):
...         result = self.first * self.second
...         return result
...     def sub(self):
...         result = self.first - self.second
...         return result
...     def div(self):
...         result = self.first / self.second
...         return result
```

모든 것이 제대로 동작하는지 확인해 보자.

```py
>>> a = FourCal()
>>> b = FourCal()
>>> a.setdata(4, 2)
>>> b.setdata(3, 8)
>>> a.add()
6
>>> a.mul()
8
>>> a.sub()
2
>>> a.div()
2
>>> b.add()
11
>>> b.mul()
24
>>> b.sub()
-5
>>> b.div()
0.375
```

우리가 목표로 한 사칙 연산 기능을 가진 클래스를 만들어 보았다.
