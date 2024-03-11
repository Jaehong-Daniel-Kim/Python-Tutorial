# Topic 1: Python Basic

Python의 기본적인 문법에 대해서 공부한다.  

# Python Code 맛보기
> Jump to Python P.18 - P.22

Python은 다른 프로그래밍 언어와 비교하였을 때 아주 간단한 문법을 갖고있다.  
일반적인 자연어와 비슷한 문법을 갖고있기 때문에 인간 친화적인 High Level Programming Language라고 한다.  
(High Level언어와 Low Level언어는 간단하게 설명하자면 사람이 얼마나 읽기 쉽고 편한지에 따라서 나뉘게된다. 사람에게 가깝다면 High Level언어라 하고, 사람보다 기계가 이해하기 더 쉽다면 Low Level언어로 볼 수 있다.)

```python
# writing "Hello World" to the console with Python

print("Hello World")
```

```c
// writing "Hello World" to the console with c

#include <stdio.h>

int main()
{
    printf("Hello World!");
    
    return 0;
}
```
간단히 "Hello world"를 출력하기 위해서 여러 줄을 작성해야 하는 C 언어와 다르게 Python은 한줄로 간단하게 수행할 수 있다.  

파이썬 코드의 몇가지 예제를 더 살펴본다.  

<b>변수 (Variables)</b>
```python
first_name = "Daniel"
last_name = "Kim"
print(first_name, last_name)

# > Daniel Kim
```

<b>조건문 (Conditional Statement)</b>
```python
today = "Friday"

if today == "Friday":
    print("Happy!")
else:
    print("Tired...")
```

<b>반복문 (Iteration, Loop)</b>
```python
favorite_fruits = ["apple", "banana", "kiwi"]

for fruit in favorite_fruits:
    print(fruit)

# > apple
# > banana
# > kiwi
```
```python
age = 15
year = 1

while age < 18:
    print(age)
    age = age + year
    print("a year later...")
print("I'm an adult now!")

# > 15
# > a year later...
# > 16
# > a year later...
# > 17
# > a year later...
# > I'm an adult now!
```

<b>함수 (Function)</b>
```python
def add(num1, num2):
    return num1 + num2
```
Python에 익숙하지 않은 사람도 위 코드를 보면 대략적으로라도 어렵지 않게 이해할 수 있을 것이다. 이렇게 사람에게 친숙한 문법을 갖고있는 것이 Python의 특징이다.  
만약 위 코드를 봐도 이해가 되지 않는다고 해도 걱정할 필요는 없다.  
과정이 진행되면서 하나씩 천천히 보다보면 금방 이해할 수 있을것이다.  

***

# 변수와 자료형

## 변수

변수는 값을 저장하는 "상자" 라고 생각할 수 있다.  
각 변수는 컴퓨터의 메모리 공간에 저장되어 메모리 공간을 차지하며 고유한 메모리 주소값을 할당 받게 된다. (Python에는 Garbage Collector 라는 프로세스가 자동으로 메모리 공간을 관리해주기 때문에 특별한 경우를 제외하고는 신경쓰지 않아도 된다.)  
변수는 전역 변수 (Global Variable)과 지역 변수 (Local Variable)로 나뉜다.  
각 종류에 대하여는 조금 더 나중에 공부할 예정이므로 아직까지는 모든 변수를 전역 변수라고 생각하면 된다. 
> 변수를 생성할때는 몇가지 약속된 주의사항이 있다.
> 1. l (소문자 "L"), O (대문자 "O"), I (대문자 "I")는 혼란을 주기 쉬운 문자이므로 단일 문지로 사용하지 않는다.
> 2. 변수명은 소문자로 작성하는것이 일반적이며, 짧고 간결하고 변수가 의미하는 값을 이해하기 쉽도록 작성한다. 변수명에 공백(띄어쓰기)이 필요하다면 "_"(Underscore)로 대체한다.  
> 3. Python에서 예약되어있는 함수명 (str, int 등)은 변수 명으로 사용하지 않는다.

> Python의 "Styling Guide"에 대해서 조금 더 자세하게 보고싶다면 아래 링크를 참조.  
> 1. PEP8 Style Guide for Python Code Official Document: https://peps.python.org/pep-0008/#introduction  
> 2. PEP8 한글 번역: https://zerosheepmoo.github.io/pep8-in-korean/doc/introduction.html

```python
# Example of use of variables

cookies = 10
candies = 5
chocolates = 2

total_snacks = cookies + candies + chocolates
print(total_snacks)
# > 17
```
## 자료형 
Python에서 가장 기본이 되는 자료형은 아래와 같다.  
각각의 자료형으로 문자, 숫자, 참과 거짓 등을 표현할 수 있다.   
각각의 자료형의 종류에 따라서 연산되는 방법도 다르기 때문에 자료형을 사용할 때 유의해야한다.  

> Jump to Python   
> 1. Integer (숫자형): P.36 - P.37  
> 2. Float (실수형): P.36 - P.37  
> 3. String (문자형): P.40 - P.43  
> 4. Boolean (참, 거짓형): P.85 - P.85    

> 꿀팁:   
> 간혹 숫자형을 사용할 때 높은 숫자를 코드에 그대로 적으면 가독성이 떨어지게 된다.   
> 예) 10000000 <- "천만" 을 작성하고자 하면 왼쪽과 같이 작성되어 가독성이 떨어진다.   
> 위와 같은 경우, 숫자에 Underscore 를 활용하여 가독성을 높일 수 있다.   
> 예) 10_000_000 <- "_"를 활용하여 숫자를 띄어쓸 수 있으며, 자료형에는 아무런 영향이 없다.

```python
# Examples of Basic Data Types
# ========================================================

# Interger and Float Type
my_age = 20 # Integer
pi = 3.14  # Float 
zero = 0  # Zero is an empty integer

# ========================================================

# String Type
my_name = "Daniel"  # String with double quotation marks
last_name = 'Kim'  # String with single quotation marks
number_string = "1234"  # This is also a string because the number is surrounded by quotation marks
empty = ""  # this represents an empty string 
not_empty = " "  # this is not an empty string because it contains an "empty space"

# ========================================================

# Boolean Type
is_student = True  # boolean type should always start with a capital letter.
is_raining = False

# ========================================================

# Operations
first_name = "Daniel"
last_name = "Kim"
my_name = first_name + " " + last_name  # adding three strings, the first_name, an empty space and the last_name
print(my_name)
# > Daniel Kim  

current_year = 2024
year_born = 1996
my_age = current_year - year_born
print(my_age)
# > 28
```

## Arithmetic Operators
Python에서는 다양한 연산자를 제공한다.  
연산자를 잘 사용하게 되면 길어질 수 있는 코드를 더 간결하고 깔끔하게 작성 할 수 있다.  
연산되는 자료형에 따라서 연산되는 방식또한 달라지며, 서로 다른 자료형을 연산하려고 하면 오류가 발생하니 주의해야한다.
> Jump to Python  
> 숫자형 연산: P.38 - P.39  
> 문자형 연산: P.44 - P.44
```python
# Ex) Operations on Integers
# ========================================================

# Addition, Subtraction
budget = 5000
cookie = 1000
coffee = 1500
total_cost = cookie + coffee  # Addition on Intergers
budget_left = budget - total_cost  # Subtraction on Integers
extra_erned = 1500.50
new_budget = budget_left + extra_erned  # Addition or Subtraction can be performed between interger and floats
print(new_budget)
# > 4000.5

# ========================================================

# Multiplication
multiplicand = 9
multiplier = 3
product = multiplicand * multiplier  # Multiplication on Integers
print(product)
# > 27

# ========================================================

# Exponential
base = 2
exponent = 4
result = 2 ** 4  # 2*2*2*2 / 2^4
print(result)
# > 16

# ========================================================

# Division
pieces_of_cake = 8
people = 4
pieces_per_person = pieces_of_cake / people  # Division on Integers
print(pieces_per_person)
# > 2.0  # mark that the result of division will always be a float type

# ========================================================

# Floor Division
lunch_total = 53_730
people_shared = 4
price_per_person = lunch_total / people_shared  # Simple Division
print(price_per_person)
# > 13432.5
price_per_person = lunch_total // people_shared  # Floor Division
print(price_per_person)
# > 13432  # drops any number after decimal point and only returns int type.

# ========================================================

# modulos
pizza_slices = 8
people = 3
left_slices = pizza_slices % people  # modulos returns the remainder value after division.
print(left_slices)
# > 2 
```

# 자료구조 (Data Structures)

## 자료 구조
기본 String, Int, Float 자료형 외에도 Python에는 list, tuple, dictionary와 같은 자료구조가 존재한다.  
List, Tuple, dictionary는 자료형 보다 조금 더 복잡한 자료구조로, 데이터를 다양한 방식으로 처리하기 위한 container 개념이다.  
> Jump to Python  
> 리스트 자료형: P.61 - P.66  
> 튜플 자료형: P.71 - P.73  
> 딕셔너리 자료형: P.74 - P.77  
> 집합: P.81 - P.82  

리스트 자료형은 변경할 수 있는 배열, 튜플 자료형은 변경할 수 없는 배열, 그리고 딕셔너리 자료형은 키(Key)로 값(Value)를 찾아내는 사전형 자료형이다.  
집합 자료형은 리스트 또는 튜플 자료형과 비슷하지만 중복을 허용하지 않으며, 순서가 없는것이 특징이다.

각각의 <b>자료구조</b>는 여러 <b>자료형</b>을 포함할 수 있다.

> 1. 리스트는 [ ] 괄호로 표기된다.
>    - 리스트 내 요소(Item)는 [ ]괄호에 인덱스 번호를 넣어 참조할 수 있다.  
> 2. 튜플은 ( ) 괄호로 표기된다.
>    - 튜플 내 요소(Item)는 [ ]괄호에 인덱스 번호를 넣어 참조할 수 있다.
> 3. 딕셔너리는 { } 괄호로 표기된다.
>    - 딕셔너리 내 값(Value)는 [ ]괄호에 키(Key)값을 넣어 참조할 수 있다.

```python
# Examples of Data Structures
# ========================================================

# Examples of List
todo_list = ["workout", "study", "grocery shopping"]
# Each item is indexed starting from 0: [0, 1, 2]
print(todo_list[0]) # > "workout"
print(todo_list[1]) # > "study"
print(todo_list[2]) # > "grocery shopping"
print(todo_list[3]) # this occurs an "IndexError" since there are three items with indicies starting from 0

todo_list[0] = "swimming"
print(todo_list)
# > ["swimming", "study", "grocery shopping"]  # you can change an item in a list by referencing the index of the item.

# ========================================================

# Examples of Tuple
members = ("Daniel", "Julia", "Owen")
# Each item is indexed starting from 0: (0, 1, 2)
print(members[0]) # > "Daniel"
print(members[1]) # > "Julia"
print(members[2]) # > "Owen"
print(members[3]) # > occurs an "IndexError"

members[0] = "John"  # > This occurs "TypeError" because tuple values cannot be changed or modified.

# ========================================================

# Examples of Dictionary
person = {
    "name": "Daniel",
    "birth_month": "August",
    "birth_day": 1,
    "favorit_fruits": ["apple", "banana", "tangerine"]
}
print(person["name"])  # Searching for the "name" value using the key, "name"
# > "Daniel"
print(person["sin_number"])  # This occurs "KeyError" because key does not exist

person["name"] = "John"
print(person["name"]) 
# > "John"  # you can also modify the value
```
# 조건문 (Conditional Statement)

## 조건문
> Jump to Python  
> If Statement: P.97 - P.108

조건문은 Conditional Statement라고하여 여러가지 경우의 수에 대응하는 코드를 작성할 수 있다.
조건문의 시작은 항상 `if`로 시작되며, 그 외 추가적인 조건은 `elif`로 작성한다.  
그리고 정의한 모든 조건에 부합되지 않는 경우는 `else` 구문으로 정의한다.  

조건문은 만약 특정 조건이 참일 경우 해당 조건문 안에 있는 코드를 실행하고,  
조건이 거짓일 경우에는 코드를 실행하지 않고 다음 조건 또는 다음 코드로 넘어가게 된다.  

> 자료형의 참과 거짓
> 자료형 (Int, Float, Str), 그리고 자료 구조 (list, tuple, dictionary, set)또한 참과 거짓으로 평가(evaluate)할 수 있다.  
>    - 모든 비어있는 자료형 또는 자료 구조는 <b>거짓</b>으로 평가된다.  
>    - 모든 비어있지 않은 자료형 또는 자료 구조는 <b>참</b>으로 평가된다. 

그리고 함수등과 같은 <b>코드 블록</b>을 작성할 때에는 들여쓰기(Indentation)가 매우 중요하기 때문에 항상 주의해야한다. 

> Indentation  
> 들여쓰기(Indentation)라는것은 말 그대로 코드의 첫 시작 부분에 특정 개수의 공백을 넣어 코드를 안쪽에서부터 작성을 하는 것이다.  
> 다양한 기호와 괄호를 사용하여 하나의 코드 블록을 작성하는 다른 언어들과 달리 파이썬은 코드 블록을 묶는 기호가 없는 대신 들여쓰기로 코드 블록을 나누게 된다.   
> 따라서 들여쓰기는 Python의 문법 중 하나로, 필수적으로 올바르게 작성해주어야 정상적으로 코드가 동작한다.  
> 아래 몇가지 주의 사항을 참고하자.  
>    1. 들여쓰기 간격은 최소 두칸 이상으로 띄워주면 되지만, 공식적 그리고 통상적으로 네칸을 띄우는게 일반적이다.  코드 협업시 암묵적으로 정해진 규칙이므로 네칸을 띄우는 것이 좋다.
>    2. 전체 코드에서 들여쓰기 간격은 항상 일정해야한다.  
>    3. 탭(\t)과 공백은 구분된다. 간혹 "vim"과 같은 텍스트 에디터에서는 탭과 공백을 별도의 문자로 작성하기 때문에 에디터를 변경해가며 코드를 작성할 시 유의해야한다.  

```python
# Example of Conditional Statement
# ========================================================

if True:  # this code block will always run since the statement is always True.
    print("Executing code...")  # Notice the 4-space-indentation.
print("Finished")
# > "Executing code..."
# > "Finished"

# ========================================================

if False:  # this code block will not run since the statement is always False.
    print("Executing code...")  # Notice the 4-space-indentation.
else:  # Instead, "else" code block will run.
    print("Statement is False!")  
print("Finished")
# > "Statement is False!"
# > "Finished"

# ========================================================

empty_string = ""   # this is an empty string
if empty_string is True:
    print("it is True!")
else:
    print("it is False!")
# > "it is False!"

empty_space = " "  # this is NOT an empty string since it contains a space
if empty_space:  # you can leave out "is True" for simplicity
    print("it is True!")
else:
    print("it is False!")
# > "it is True!"

empty_list = []  # this is an empty list
list_with_empty_string = [""]  # this is NOT an empty list because it contains an empty string
if empty_list:
    print("empty list is True!")
elif list_with_empty_string:
    print("list with empty string is True!")
else:
    print("Everything is False")
# > "list with empty string is True!"

# ========================================================
```
참과 거짓은 아래와 같이 값을 비교하는 상황에서도 평가될 수 있다.

> 값 비교하기  
> <b>==</b> : 해당 기호 기준 왼쪽과 오른쪽의 값의 일치 여부를 확인, 일치한다면 "True" 를 반환한다.   
> <b>!=</b> : 해당 기호 기준 왼쪽과 오른쪽의 값의 불일치 여부를 확인. 일치하지 않는다면 "True"를 반환한다.   
> <b>></b> : 해당 기호 기준 왼쪽의 값이 오른쪽의 값보다 클 경우 "True"를 반환한다.   
> <b><</b> : 해당 기호 기준 왼쪽의 값이 오른쪽의 값보다 작을 경우 "True"를 반환한다.   
> - <b>>=</b>, <b><=</b> 와 같이 "작거나 같다" 또는 "크거나 같다" 로도 사용할 수 있다.  
> 
> <b>not</b> : "True"와 "False"를 반대로 해석하여 평가한다.  
>    - not True: "True"가 아니라면 ("False"라면) "True"를 반환한다.   
>    - not False: "False"가 아니라면 ("True"라면) "True"를 반환한다.   
> 
> <b>in</b> : 특정 요소가 리스트, 튜플, 딕셔너리와 같은 자료 구조 내에 포함되어 있는지 확인. 포함되어있다면 "True"를 반환한다.
>    - list: in [list]
>    - tuple: in (tuple)
>    - dictionary: in {dictionary} -> 딕셔너리의 경우 키 값의 존재 유무를 확인한다.  

```python
# Examples 
# ========================================================

# ==
name = "Daniel"
if name == "Daniel":
    print("Hello,", name)
else:
    print("I don't know you")
# > "Hello, Daniel"

# ========================================================

# !=
entered_phone_number = "010-1234-5678"
my_phone_number = "010-2345-6789"
if entered_phone_number != my_phone_number:
    print("You've entered the wrong number")
else:
    print("You've reached me!")
# > "You've entered the wrong number"

# ========================================================

# > / < / >= / <=
my_age = 15
adult_age = 18
if my_age >= adult_age: 
    print("I'm an adult")
elif my_age >= 10 and my_age < adult_age:
    print("I'm a teenager")
else:
    print("I'm a kid")
# > "I'm a teenager"

# ========================================================

# not
expensive = True
if not expensive:
    print("I will buy it")
else:
    print("I will not buy it")
# > "I will not buy it" 

cheap = False
if not cheap:
    print("it is expensive")
else:
    print("it is cheap")
# > "it is expensive"

# ========================================================

# in
favorite_fruits = ["apple", "kiwi"]
if "banana" in favorite_fruits:
    pass  # pass statement does nothing and just break out of the conditional statement
elif "banana" not in favorite_fruits:
    print("I also like banana")
# > "I also like banana"

phone_book = {
    "Daniel": "010-1234-5678",
    "John": "010-1111-2222",
    "Peter": "010-9999-8888",
}
if "Daniel" in phone_book:
    print("I have Daniel's number")
elif "John" in phone_book:  # even if this statement is True, it will not be executed because the previous if statement was already True.
    print("I also have John's number")
else:
    print("I don't have either of your number")
# > "I have Daniel's number
```

# 반복문 (Loop) 

## Loop
> Jump to Python  
> while statement: P.109 - P.114  
> for statement: P.116 - P.120

반복문은 특정한 코드를 여러번 반복할 때 사용된다.   
반복문 내에서 조건문 (If Statement)를 활용하여 코드를 반복하면서 특정 조건에서 특정 코드가 실행되도록 작성할 수도 있고, 조건문 내에서 특정 조건이 성립 되었을 때 특정 코드블록을 반복시키는 등 사용 방법은 무궁무진하다.  

하지만 반복문은 말 그대로 특정 코드 블록을 반복하여 실행하는 구문으로, 잘못 사용한다면 코드가 무한 루프에 빠지거나 프로그램의 실행 속도가 현저하게 저하될 수 있는 문제점이 있기때문에 사용 시 유의하여야 한다.  

### while
`while` 문의 경우 특정 조건이 "True"상태인 동안은 계속해서 반복을 하게 된다.   
따라서 while문을 종료하기 위해서는 해당 조건의 상태를 "False"로 만들어 주어야 할 필요가 있다.  
그렇지 않으면 while문은 무한 루프가 되어 종료되지 않으며, 시스템에 부하를 발생시키게된다. 

### for
`for` 문의 경우 정해진 주기동안 반복문을 실행하게 된다.  
하지만 해당 주기를 무한으로 주게되면 for문 또한 무한 루프로 동작될 수 있으니 주의해야한다. 

`while`과 `for` 모두 반복적으로 실행되는 코드 블록이기 때문에 시스템에 부하를 일으킬 수 있는 리눅스 커맨드, Database Query커맨드 등은 반복문 안에 포함시키는 것을 지양하며, 사용을 해야할 경우에는 주의하여 사용한다. 

```python
# examples of loops
# ========================================================

# note that append() function adds an argument into a given list.
# without for loop
shoping_list = ["pen", "notebook", "calculator", "ruler"]
shoping_cart = []

shoping_cart.append("pen")
shoping_cart.append("notebook")
shoping_cart.append("calculator")
shoping_cart.append("ruler")

# with for loop
for item in shoping_list:
    shoping_cart.append(item)  # this iterate through shiping_list list and repeats the append() function for four times.
print(shoping_cart)
# > ["pen", "noteboko", "calculator", "ruler"]

# ========================================================

# while loop
current_hour = 13
off_hour = 17
while current_hour < off_hour:
    time_left = str(17 - 8)  # str() function transforms argument into a string type.
    print("I still need to work for another " + time_left + " hours")
    current_hour += 1
print("Let's go home!")  # this code block will not run until the while loop is finished
# > "I still need to work for another 4 hours"
# > "I still need to work for another 3 hours"
# > "I still need to work for another 2 hours"
# > "I still need to work for another 1 hours"
# > "Let's go home!"

# ========================================================

# Loop with conditions
cars = {
    "audi": {
        "price": 75_000_000,
        "design_rating": 3,
    },
    "porsche": {
        "price": 100_000_000,
        "design_rating": 5,
    },
    "used_bmw": {
        "price": 39_000_000,
        "design_rating": 3.2,
    },
    "hundai": {
        "price": 40_000_000,
        "design_rating": 3,
    },
    "kia": {
        "price": 38_000_000,
        "design_rating": 2.5,
    },
}

for car in cars:  # car is going to be each key of the cars_price dictionary
    if cars[car]["price"] >= 50_000_000:
        pass
    else:
        if cars[car]["design_rating"] > 2:
            print(car, ": I will consider")
# > used_bmw : I will consider
# > hundai : I will consider
# > kia : I will consider
```
