# Topic 2. 오류 처리 (Exception Handling)
Python 코드를 작성하다 보면 많은 오류와 마주치게된다.  
오류는 상황에 따라서 의도하지 않은 동작이 발생하는 것을 방지할 수 있다.
하지만 어떠한 상황에서도 코드내에서 오류가 발생하게 되면 `Exit Code 1`이 발생하게 되며, 프로그램 실행이 강제 종료된다.  
프로그램이 강제 종료되면 해당 프로그램을 통해 원하는 결과값을 도출해 내기 어렵다.  
또한, 일반 스크립트 프로그램이 아닌 백그라운드에서 상시 동작하는 데몬과 같은 프로그램 또는 서비스 어플리케이션의 경우
오류로 인하여 프로그램이 종료되면 일시적 장애가 발생하게 된다.  
따라서, 코드 작성 시 여러 테스트 케이스를 만들고, 테스트를 통하여 발생할 가능성이 있는 오류를 미리 찾아내어 
오류를 미리 처리해주는 코드를 작성하는 것은 매우 중요하다.

> Jump to Python   
> P.189 - P.196
 
***
# Table of Contents
1. [Errors Overview](#1-errors-overview)
2. [Traceback](#2-traceback)
3. [try ... except](#3-try--except)
4. [finally](#4-finally)
5. [else](#5-else)

***

## 1. Errors Overview
아래 코드를 복사하여 실행해보자. 오류가 발생할 것이다.
```python
# SyntaxError
name = "Daniel'
print(name)
```
`SyntaxError`의 경우 기본적인 문법이 맞지 않을 때 발생한다.
```python
# IndexError
my_list = ["apple", "strawberry"]
print(my_list[2])
```
`IndexError`의 경우 `list`, `tuple`등의 자료형에서 참조하고자 하는 인덱스(Index)가 존재하지 않을 때 발생한다. 
```python
# ZeroDivisionError
print(1/0)
```
`ZeroDivisionError`의 경우 어떠한 수를 0으로 나누려고 할 때 발생한다. 
```python
# TypeError
num_1 = 10
num_2 = "20"
print(num_1 + num_2)
```
`TypeError`의 경우 자료형 규칙에 어긋난 코드가 실행되었을 때 발생하게 된다.   

## 2. Traceback
위의 예시와 같이 오류의 형태는 매우 다양하다.  
한가지 고마운 점은 Python은 오류가 발생하였을 때 `Traceback`을 통하여 오류가 발생한 위치와 오류의 원인을 알려준다.  
예를들어 `TypeError`가 발생하였다면 아래와 같은 문구가 출력될 것이다. 
>> Traceback (most recent call last):  
>>  File "/users/tutor/python_lectures/Topic_2/errors.py", line 1, in <module>  
>>    print(10 + "10")  
>> TypeError: unsupported operand type(s) for +: 'int' and 'str'   
> 
> 위 구문에서 두번째 라인부터 살펴보자.
>>  File "/users/tutor/python_lectures/Topic_2/errors.py", line 1, in <module>  
> 
> 위 구문은 어떤 파일에서 몇번째 구문에서 오류가 발생하였는지 알려준다. 
>>    print(10 + "10")  
>
> 위 구문은 오류가 발생한 코드의 내용을 알려준다. 
>> TypeError: unsupported operand type(s) for +: 'int' and 'str'   
>
> 그리고 마지막 라인은 어떤 형태의 오류가 발생하였는지 알려준다.  
> 오류의 내용은 `TypeError`가 발생하였고, 이유는 'int'와 'str' 사이에서 '+' 연산자는 사용될 수 없다는 내용이다.  
> 
위와 같이 오류가 발생하였을 때는 Traceback을 잘 읽어보면 오류에 대한 해답을 찾는데 도움을 받을 수 있다. 

## 3. Try ... Except
위와 같은 오류가 발생하였을 때, try ... except 문을 활용하여 오류를 유연하게 처리하는 방법을 살펴본다.  
`try`는 제일 먼저 이러한 코드를 '시도 하라' 라는 의미로 활용된다.  

- `try` 구문 내에는 실행하고자 하는 코드를 넣는다.

`except`는 `try`문 이후에 무조건 따라와야 하는 구문으로, '코드 실행 중 특정 오류 발생 시' 라는 의미로 활용된다.  

- `except` 구문은 `except <ErrorName>` 과 같은 형태로 작성한다.
- 해당 `<ErrorName>`이 발생했을 때 except 구문 내에 있는 코드를 실행한다는 의미이다. 

아래 예제코드를 살펴보자.  
```python
# TypeError
num_1 = 10
num_2 = "20"
print(num_1 + num_2)
```
`TypeError`를 발생시키는 위와 동일하 코드이다.  
위 코드에 `try ... except` 문을 추가해보자.  
```python
num_1 = 10
num_2 = "20"
try:
    added = num_1 + num_2
except TypeError:
    added = int(num_1) + int(num_2)
print(added)
```
위 코드를 실행시켜보면 30 이라는 결과가 오류없이 출력되는 것을 확인할 수 있다.  
원리는, `try`문 에서 `num_1`과 `num_2`를 더하는것을 <b>시도</b> 한다.  
하지만 우리의 예상과 같이 자료형이 다르기 때문에 `TypeError`가 발생한다.  
따라서, `except TypeError`문에서 `TypeError`가 발생할 경우 두 변수의 자료형을 int 타입으로 변환 및 통일시켜준 후 더한다.  

### 다양한 오류 처리 예제
1. 오류 건너뛰기   
    특정 오류가 발생하였을 때, 해당 오류를 발생시키지 않고, 그냥 넘어간다. 
```python
fruites = ['apple', 'banana', 'strawberry', 'mellon']
for i in range(5):
    try:
        print(fruites[i])
    except IndexError:
        pass  # when IndexError occurs, skip
```
2. 다중 오류 처리  
   다중 `except`구문을 활용하여 여러 오류를 처리한다. 
```python
my_num_list = [10, 100, 1000, 10_000]
number = "10"
for i in range(5):
    try:
        added = my_num_list[i] + number
    except TypeError:
        added = int(my_num_list[i] + int(number))  # when TypeError occurs, change the data type to integer
    except IndexError:
        pass  # when IndexError occurs, skip
    print(added)
```
3. 모든 오류 탐지  
   어떤 오류가 발생할 지 모르는 상황, 또는 모든 오류에 대해서 동일한 처리를 하고 싶을 때 사용할 수 있다.
```python
try:
    my_name = "Daniel"
    my_age = 20
    print("Hi, my name is " + my_name)
    print("I am " + my_age + " years old")
except BaseException:
    pass  # skip every error
```
아래 코드의 경우, 모든 종류의 오류가 발생하였을 시 `except`구 문이 실행되며,  
어떤 오류가 발생하였는지 `print`구문을 통하여 확인할 수 있다. 
```python
try:
    my_name = "Daniel"
    my_age = 20
    print("Hi, my name is " + my_name)
    print("I am " + my_age + " years old")
except BaseException as e:  # initialize a variable for BaseException
    print(e)
```

## 4. Finally
`finally` 구문은 `try ... except`구문 가장 마지막에서 항상 실행되는 코드이다.  
`finally` 구문의 경우 `try ... except` 구문이 끝날 때 <b>항상</b> 실행되게된다.  
즉, 특정 오류가 처리가 되었을 경우 또는 처리되지 못한 오류가 발생하였을 경우 등 모든 경우에서 실행되게 된다.  
이러한 특징으로 인하여 보통 데이터베이스와 연결을 close 할 때, 프로그램 내부에서 열려있는 파일을 닫을 때 등 많은 곳에서 활용될 수 있다.  
아래 예제 코드를 통하여 `finally`구문의 특징을 확인해보자.
```python
try:
    my_list = ["hello", "world"]
    print(my_list[0] + " " + my_list[2])
except TypeError:
    pass
print("Bye World")
```
위 예제코드의 경우 my_list에는 두개의 요소밖에 없기 때문에 `my_list[2]`에 의하여 `IndexError`가 발생할 것이다.  
`TypeError`는 오류 처리가 되어있지만, `IndexError`의 경우에는 오류 처리가 되어있지 않아서 `IndexError`가 발생하고, 프로그램이 종료되게 된다.  
따라서 제일 마지막의 `"Bye World"`는 출력되지 않을것이다.  
```python
try:
    my_list = ["hello", "world"]
    print(my_list[0] + " " + my_list[2])
except TypeError:
    pass
finally:
    print("Bye World")
```
위와 같이 `finally`구문을 추가하여 `print`구문을 `finally` 구문 안으로 이동하였다.  
위 코드를 다시 실행해보면 동일하게 `IndexError`가 발생하게 되지만, `"Bye World"`가 출력되는 것을 확인할 수 있다.  
이처럼 `finally`구문은 `try ... except`구문의 실행이 종료될 때 <b>항상</b> 실행되게 된다.  
`try ... except ... finally` 구문은 추후 공부할 함수와 함께 사용할때도 유용하게 사용될 수 있다.  

## 5. else
`else`구문은 `try ... except` 구문과도 함께 사용될 수 있다.  
`try ... except`와 함께 사용되는 `else`구문의 의미는 미리 정의한 오류가 발생되지 않았을 때 실행하라 라는 의미이다. 

