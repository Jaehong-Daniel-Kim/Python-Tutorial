# Topic 2. 함수 Functions
과거 수학을 공부할 때 우리는 함수를 배웠다.  
예를 들어 `f(x) = x + 2` 와 같은 함수 공식이 있을 때, `x`를 `2`라고 가정하다면 `y`의 값은 4가 되는것이다.  
그리고 `x`를 `3`이라고 한다면 `y`의 값은 `5`가 된다.  
이와 같이 입력값`x`에 따라서 동일한 작업`x+2`가 실행되며, 그에 해당하는 결과값 `y`가 도출된다.  

특정한 작업이 반복될 때 함수를 생성하고 해당 함수를 호출하는것 만으로 반복적인 코드가 줄어들게된다.  
또한 코드의 길이도 줄어들고, 하나의 기능을 하나의 함수로 한정하여 코드를 작성하게 되므로 추후 유지보수 및 코드 관리도 편해지게된다.  

> Jump to Python   
> P.125 - 139

***
# Table of Contents
1. [Functions Overview](#1-functions-overview)
2. [Defining Functions](#2-defining-functions)
3. [return](#3-return)
4. [parameters and arguments](#4-parameters--arguments)  
   4.1. [Functions without parameters](#4-1-parameters---매개변수가-없는-함수)  
   4.2. [Default Parameters](#4-2-parameters---default-값-설정)  
   4.3. [**args](#4-3-parameters---args)  
   4.4. [**kwargs](#4-4-parameters---kwargs)
***

## 1. Functions Overview
아래와 같이 여러 사람에게 인사를 해주는 코드가 있디고 가정한다.  
사람의 이름만 다를 뿐 반복적인 `print()` 함수와 `"Hello"` 라는 문자열이 반복되고있다.
```python
print("Hello Daniel.")
print("Hello Jefferson.")
print("Hello Ralph.")
print("Hello Gus.")
```
만약 위 코드에서 `"Hello"` 문자열을 `"Bye"` 라고 수정해야할 경우 총 네번을 수정해야 한다.  
이제 위 코드를 함수형태로 변경한다. 
```python
def say_hello(name):
    print(f"Hello {name}")  # this is called f-string

say_hello("Daniel")
say_hello("Jefferson")
say_hello("Ralph")
say_hello("Gus")
```
위와 같이 함수를 작성하게 되면, 우리는 `say_hello()`함수를 여러번 호출하여 동일한 처음 코드와 동일한 결과값을 얻을 수 있다.  
또한 `"Hello"` 문자열을 `"Bye"`라고 수정을 하고 싶다면 `say_hello()`함수 안에서 한번만 수정하게 되면 깔끔하게 해결된다.  

> 우리가 자주 사용하는 `print()` 또한 Python에 기본적으로 내장되어있는 하나의 함수 이다.  
> 이처럼 Python에서는 기본적으로 다양한 작업을 간편하게 할 수 있도록 다양한 기능의 함수를 제공한다.

## 2. Defining Functions
이제 함수를 직접 작성하는 방법을 본다.  
```python
def name_of_function(parameter1, parameter2, parameter3,):
    # Code Block

name_of_function(argument1, argument2, argument3)
```
위 코드를 살펴본다.   
- `def`: 키워드는 함수를 생성하기 위한 키워드이며, `define`의 약자이다. 함수를 생성하려면 무조건 가장 처음에 사용되어야 한다.
- `name_of_function`: 함수의 이름이다. 변수명과 같이 의미있는 이름으로 만든다.  
- `parameter`: 한국어로 `매개변수` 또는 `인자` 라고 부른다. 함수의 입력값으로 한 개 부터 무한대의 입력값을 입력받을 수 있다.
- `Code Block`: 함수가 호출되었을 때 실행될 코드이다.   
- `name_of_function()`: 함수를 실행한다는 의미로, 함수 이름뒤에 `()`를 붙여준다. `()`안에는 매개변수에 대한 `인수` 값이 들어간다.
- `argument`: 한국어로 `인수` 라고 부른다. 함수를 실행(호출)할 때 입력값으로 넣는 값을 뜻한다. `인수`의 개수는 호출하고자 하는 함수의 `인자`의 개수와 무조건 동일해야만 한다. 

위 예시를 통하여 직접 함수를 작성해본다. 
```python
def add_numbers(number1, number2):
    print(number1 + number2)

add_numbers(1, 2)  # 3
add_numbers(5, 10)  # 15
add_numbers(20, 100)  # 120
add_numbers(50, 50)  # 100
```
> `인자`와 `인수`는 순서가 있다. 즉, 첫번 째 `인수`는 첫번 째 `인자`로 입력되며, 두번째 `인수`는 두번 째`인자`로 입력된다.
> 따라며 `add_numbers(1, 2)`와 같이 작성한다면 `number1`은 `1`이되며, `number2`는 `2`가 된다.   
 
아래 예시를 참고하여 `인자`와 `인수`가 어떻게 설정되는지 확인해보자.   
항상 왼쪽부터 순서대로 대입된다.
```python
def subtract_numbers(number2, number1):
    print(number1 - number2)

subtract_numbers(10, 3)  # -7
subtract_numbers(5, 55)  # 50
subtract_numbers(10, 9)  # -1
```

## 3. return
함수에는 크게 두가지 종류가 있다.  
하나는 반환하는 값이 있는 함수이며, 다른 하나는 반환하는 값이 없는 함수이다.

위에서 살펴본 함수는 함수 내에서 `print()`함수만 실행시켜줄 뿐 반환값이 없다.  
반환값이 없다는 뜻은 `None` 값을 반화한다는 의미이다.  
이게 어떤 의미인지 아래 코드를 통하여 확인해본다. 

```python
def add_numbers(number1, number2):
    print(number1 + number2)

added = add_numbers(10, 5)  # 15
print(added)  # None
```
`add_numbers()`함수를 호출하여 그 결과값을 `added`라는 변수에 저장을 하였다.  
그리고 `print()`함수 문으로 해당 변수에 저장된 값을 확인하였을 때 `None`이 출력되는 것을 볼 수 있다.  
즉, 반환값이 없는 함수는 항상 `None`을 반환하게된다.  
`return` 키워드는 함수 안에서 사용되는 키워드로, 특정 값을 함수 밖으로 `반환` 해줄 때 사용한다.

```python
def add_numbers(number1, number2):
    return number1 + number2

added = add_numbers(10, 5) 
print(added)  # 15
```
위 코드를 실행해보면 `add_numbers()`함수를 실행했을 때는 아무련 결과값이 출력되지 않지만 `print()`문으로 `added`변수의 값을 출력하면 15가 출력되는 것을 확인할 수 있다.  
즉, 함수에서 결과값을 반환한 것이고, `added`라는 변수에 반환된 값을 저장한 것이다. 

> `return` 키워드는 반환값을 돌려주면서, 함수의 실행을 종료한다.  
> ***
> 아래와 같은 상황에서 결과값을 예측해보자. 
> ```python
> def get_greater_than_five(number_list):
>     for number in number_list:
>         if number > 5:
>             return number
>         print(number)
>         
> numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
> number_returned = get_greater_than_five(numbers)
> print("The number greater than five is " + str(number_returned))
> ```
> 위 `get_greater_than_five()` 함수는 숫자가 리스트를 인자 갚으로 받고, 해당 리스트에서 `5` 보다 큰 숫자가 나오면 `return`구문으로 반환하며, 
> 그렇지 않은 경우에는 `print()` 함수를 실행하여 리스트 내 각 요소를 출력하게 된다.  
> 위 코드를 그대로 실행해보면 알 수 있는 것은 `print()` 구문은 `5` 까지 출력을 하고, 그 이후에는 멈추게 된다.   
> 즉, `for` loop이 실행되다가 return 구문을 만나게되면 그 즉시 실행을 멈추고, 값을 반환하게 된다. 

## 4. Parameters & Arguments

이번에는 함수의 `매개변수(parameter)`와 `인수(argument)`에 대해서 조금 더 자세히 살펴본다.  
`매개변수`는 `인자` 또는 영어식 발음으로 `파라미터` 라고 불리며, <b>함수가 받는 데이터를 저장하는 변수</b>를 뜻한다.  
`인수`는 영어식 발음으로 `아규먼트` 라고 불리며, <b>함수에게 전달하는 데이터</b>를 뜻한다.  

`매개변수`와 `인수` 모두 모든 자료형을 허용하며, 그 개수에는 제한이 없고, 각 `매개변수`와 `인수`는 `,(쉼표)`로 구분된다.  
또한, 순서가 있기 때문에 모든 `매개변수`와 `인수`는 왼쪽으로 오른쪽으로 설정 및 할당 된다.

`인수`를 통하여 데이터를 전달하는 방법으로는 대표적으로 `positional argument`와 `keyword argument`가 있다.
- `Positional Argument`: 왼쪽부터 오른쪽으로 순서대로 매개변수 데이터를 전달하는 방법
- `keyword Argument`: 매개변수 이름을 직접 명시하에 데이터를 전달하는 방법.

```python
# Positional Argument
def my_function(param_1, param_2, param_3):
    print(param_1, param_2, param_3)

my_function("first", "second", "third")   # first second third
my_function("thrid", "first", "second")  # thrid first second
```

```python
# Keyword Argument
def my_function(param_1, param_2, param_3):
    print(param_1, param_2, param_3)

my_function(param_1="first", param_2="second", param_3="third")  # first second third
my_function(param_3="first", param_1="second", param_2="third")  # second third first
```
### 4-1. Parameters - 매개변수가 없는 함수
함수를 생성할 때 `매개변수`는 필수가 아니다. `매개변수`가 없는 함수를 만들기 위해서는 아무것도 넣어쥐 않으면 된다.
```python
def say_hello():
    print("Hello world")

say_hello()  # Hello World
```
`매개 변수`가 없는 함수에서도 값을 `반환`받을 수 있다.
```python
def get_hello():
    return "Hello World"

hello = get_hello()
print(hello)  # Hello World
```
### 4-2. Parameters - default 값 설정
위 `my_function`과 같이 함수를 생성할 경우, 세개의 `매개변수`가 존재하므로 무조건 세개의 `인수`가 전달 되어야먄 한다.  
만약 그렇지 않을 경우에는 오류가 발생한다.  
하지만 떄로는 `매개변수`에 고정적인 default 값을 설정하고, 특별한 경우에만 `인수`로 데이터를 받아 처리를 원하는 경우가 생길 수 있다.  
아래 직원들의 출근 시간을 출력해주는 함수가 있다.
```python
def come_to_work(name, arrived_hour):
    print(f"{name} has come to work at {arrived_hour}")  # f-string

come_to_work("Potter", "8")  # Potter has come to work at 8
come_to_work("Weasley", "8")  # Weasley has come to work at 8
come_to_work("Granger", "8")  # Granger has come to work at 8
come_to_work("Hagrid", "8")  # Hagrid has come to work at 8
come_to_work("Malfoy", "12")  # Malfoy has come to work at 12
```
특별한 경우를 제외하고는 출근 시간은 일반적으로 8시로 통일되어있다. 이 경우 아래와 같이 `arrvied_hour` 매개변수 default값을 설정해주어 조금 더 사용하기 편한 함수를 만들 수 있다.   
```python
def come_to_work(name, arrived_hour="8"):
    print(f"{name} has come to work at {arrived_hour}")  # f-string

come_to_work("Potter")  # Potter has come to work at 8
come_to_work("Weasley")  # Weasley has come to work at 8
come_to_work("Granger")  # Granger has come to work at 8
come_to_work("Hagrid")  # Hagrid has come to work at 8
come_to_work("Malfoy", "12")  # Malfoy has come to work at 12
```
위와 같이 `default` 값을 넣어주면, `arrived_hour` 매개변수는 별도로 `인수` 값을 넣어주지 않는다면, `8`로 고정된다. 

### 4-3. Parameters - *args
위 예제들과 같이 `매개변수`를 특정하면 항상 정해진 매개변수의 개수만큼 `인수`를 전달해주어야 한다.  
그렇지 않을 경우에는 오류가 발생한다.  
하지만, 몇개의 데이터를 받아올지 예측을 할 수 없는 상황이 발생할 때도 있다.  
이 경우에는 `*<매개변수>` 를 사용할 수 있다.  
톡상적으로 `*args`와 같은 형태로 사용되며, 함수로 전달된 각 인수는 `Positional Arguments` 형태로, 왼쪽으로 오른쪽으로 순서대로 `tuple` 자료형으로 변환되어 전달된다.
> 매개변수 명 앞에 `* (asterisk)`를 붙여 사용하는 형태이다.    
> 통상적인 경우 `arguments`를 줄여 `*args`와 같은 형태로 사용하지만, 꼭 `args`라는 이름을 사용할 필요는 없다.  
```python
def add_numbers(*args):  # The name does not have to be "args"
    print(f"Arguments Recieved: {args}, Type: {type(args)}")  # f-string
    added = 0
    for arg in args:
        added += arg
    return added

result_1 = add_numbers(1, 2, 3, 4, 5)
print(result_1)
print()
result_2 = add_numbers(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
print(result_2)
# Arguments Recieved: (1, 2, 3, 4, 5), Type: <class 'tuple'>
# 15
#
# Arguments Recieved: (1, 2, 3, 4, 5, 6, 7, 8, 9, 10), type: <class 'tuple'>
# 55
```
위 예제에서 볼 수 있듯, `*args`의 형태로 `매개변수`를 생성해주면, 입력되는 모든 `인수`는 하나의 튜플 형태로 전달된다.   
`*args`는 단독으로 사용할 수 있으며, 일반 `매개변수`와도 함께 사용 가능하다.  
다만, 일반 `매개변수`와 사용할 때에는 일반 `매개변수`가 항상 먼저와야하며, `*args`를 항상 맨 뒤에 작성되어야만 한다.  
아래는 한 반(class)의 평균 점수를 구하는 함수이다. 
```python
def average_grade(class_name, *grades):
    total_grade = 0
    for grade in grades:
        total_grade += grade
    average_grade = total_grade / len(grades)
    print(f"The average grade of class, {class_name}, is {average_grade}")
    print()

average_grade("c-1", 80, 90, 95, 55, 70)
average_grade("c-2", 70, 50, 60, 95, 80)
average_grade("c-3", 80, 95, 95, 65, 70)
# The average grade of class, c-1, is 78.0
#
# The average grade of class, c-2, is 71.0
#
# The average grade of class, c-3, is 81.0
#
```

### 4-4. Parameters - **kwargs
`*args`가 `Positional Arguments`의 형태로 `인수`를 전달하는 형태였다고 하면, `**kwargs`는 `Keyword Argument` 형태로 `인수`값을 전달한다.  
`**kwargs`또한 통상적으로 사용하는 명칭일 뿐, `**<매개변수>` 형태로 아무 이름이나 사용할 수 있다.  
`**kwargs`로 전달받은 `인수`는 `dictionary`자료형으로 전달된다.
> kwargs는 `Keyword Argument`의 줄임말이다.   
> `**kwargs`를 사용할 경우, `인수`를 전달할 때에는 항상 `매개변수`이름을 명시해주어야 하며, 해당 `매개변수`명은 `dictionary`의 `key`값으로 활용된다.

```python
def say_hello(**kwargs):
    print(kwargs)
    name = kwargs["name"]
    print(f"Hello {name}")
    print()

say_hello(name="Potter")
say_hello(name="Weasley")
say_hello(name="Granger")
# {'name': 'Potter'}
# Hello Potter
#
# {'name': 'Weasley'}
# Hello Weasley
#
# {'name': 'Granger'}
# Hello Granger
#
```
`**kwargs`또한 일반 `매개변수`와 함께 활용이 가능하다.   
`**kwargs`를 사용할 경우에도 `매개변수`가 항상 먼저 와야하며, `**kwargs`는 가장 마지막에 작성되어야만 한다.  
아래는 한 반(class)의 과목별 평균 점수를 구하는 함수이다.   
```python
def average_by_subject(class_name, **subject_grades):
    average_grades = {}
    for subject, grades in subject_grades.items():
        average_grades[subject] = sum(grades) / len(grades)
        
    print(f"[Math Average of {class_name}]: {average_grades['math']}")
    print(f"[Science Average of {class_name}]: {average_grades['science']}")
    print(f"[History Average of {class_name}]: {average_grades['history']}")
    print()

average_by_subject("c-1", math=[50, 70, 55, 60], science=[80, 85, 55, 90], history=[90, 80, 85, 75])
average_by_subject("c-2", math=[65, 75, 50, 80], science=[85, 80, 45, 95], history=[70, 50, 75, 65])
average_by_subject("c-3", math=[80, 60, 50, 65], science=[90, 95, 95, 90], history=[50, 55, 55, 80])

# [Math Average of c-1]: 58.75
# [Science Average of c-1]: 77.5
# [History Average of c-1]: 82.5
# 
# [Math Average of c-2]: 67.5
# [Science Average of c-2]: 76.25
# [History Average of c-2]: 65.0
# 
# [Math Average of c-3]: 63.75
# [Science Average of c-3]: 92.5
# [History Average of c-3]: 60.0
#
```