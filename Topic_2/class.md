# Python Class

# Topic 2. Class

클래스는 Python이라는 언어를 사용하는데에 필수적인 요소는 아니다. 하지만, 클래스의 개념을 알게되면 Python언어 자체를 이해하고 사용하는데에 큰 도움이 된다.  

그 이유는 우리가 지금까지 사용해왔던 String, List, Tuple, Dictionary 등의 모든 자료형이 Python내부에서 클래스로 정의도어 있기 때문이다.

<aside>
💡 우리가 사용하는 `str()`, `list()`, `tuple()` 등은 사실 **내장 함수** 가 아니라 **내장 클래스** 이다.
python interpreter에서 `help(str)`, `help(list)`, `help(tuple)` 를 입력해서 직접 증명해볼 수 있다.

</aside>

클래스는 기본적으로 하나의 `객체`를 생성하기 위해서 사용된다.

예를들면 하나의 빵틀(클래스)를 사용하여 여러개의 빵을 찍어내는 형식이다.  

여기에서 빵틀(클래스)를 활용하여 만들어진 각각의 빵을 `객체`라고 부르며, `객체`는 영어로 `Object`라고 한다.

간혹 `Instance(인스턴스)`라는 단어와 혼동될때가 있는데, `인스턴스`는 `객체`와 클래스 간의 관계를 얘기할 때 사용된다. 예를들면 아래와 같다.

**별모양의 빵틀**과 **네모 모양의 빵틀**이 있다고 가정하고,  별모양의 빵틀로 A, B, C **빵**을 그리고 네모 모양의 빵틀로 D 빵을 만들었다고 가정해보자.

1. A, B, C, D 빵은 `객체`이다.
2. A, B, C 빵은 **별모양의 빵틀**의 `인스턴스`이다
3. D 빵은 "별모양의 빵틀"의 `인스턴스`가 아니다
4. 빵은 "네모 모양의 빵틀"의 `인스턴스`이다.

<aside>
💡 Jump to Python 
P 156 - P 174

</aside>

## 1. Introduction

클래스를 사용하는 이유는 기본적으로 코드를 `객체화`  하여 재활용 할 수 있도록 만드는 것이다. 

이런식으로 클래스를 만들고, 객체 위주로 프로그램을 작성하는 방식을 `객체지향형 프로그래밍` 이라고 부르며, 영어로는 `Object Oriented Programming (OOP)` 라고 한다. 

아래 예시를 보자.

```python
first_list = [1, 2, 3, 4, 5]
second_list = ["a", "b", "c", "d", "e"]

first_list.append(6)
second_list.append("f")

print(first_list)  # [1, 2, 3, 4, 5, 6]
print(second_list). # ["a", "b", "c", "d", "e", "f"]
```

위 예시에서 우리는 벌써 클래스를 활용했다.  

Python의 list자료형이 클래스 이므로, 우리가 생성한 `first_list`와 `second_list`는 list 클래스의 `인스턴스`이며, `객체(object)`이다.

위 예제에서 사용된 `append` 메서드는 list 클래스 내부에 정의되어있는 함수로, 모든 `객체`에서 `객체.메서드()`와 같은 형태로 사용할 수 있다.  

<aside>
💡 `function(함수)`과 `methods(메서드)`는 동일하지만, 함수가 독립적으로 생성된 경우 `함수` 라고 부르며, 클래스 내부에서 생성된 경우  `매서드` 라고 부른다.
</aside>

우리는 위 예제에서 두개의 `객체` 를 생성하고 `append` 메서드를 활용하여 각 `list 객체`에 요소를 추가하였다. 그리고 print를 통하여 확인을 했을 때, 각 `객체`는 서로에게 영향을 주지 않으며, 독립적인 `요소`를 갖고 있는것을 확인할 수 있다.

## 2. Python Class

직접 클래스를 만들어 보면서 조금 더 클래스에 대한 개념을 알아보자.

### 2.1 Create Class

```python
class Human:

  def eat(self, food):
    print(f"I am eating {food}")
		
  def study(self, subject):
    print(f"I am studying {subject}"
			
```

`Human(사람)` 이라는 클래스를 생성했다. 

클래스를 생성하기 위해서는 앞에 `class`키워드를 붙여주기만 하면 된다. 

클래스의 이름의 가장 첫 문자를 `Human`과 같이 대문자로 적어준 것을 볼 수 있는데, 클래스의 이름을 작성할때는 관용적으로 `CamelCase 네이밍`방법을 사용한다.  `CamelCase 네이밍`이란 낙타의 혹 처럼 각 단어의 첫 문자를 대문자로 작성해주는 방법을 뜻한다.  

`Human` 클래스를 생성한 후 `eat`, `study`, 와 같은 함수를 구현하여 기능을 추가해 주었는데, 클래스 내부에서 정의된 함수를 `메서드`라고 한다.  정의된 메서드의 가장 첫 파라미터는 `self`로 시작한다.  `self` 에 대한 더 자세한 내용은 이후에 다시 알아본다.

이제 클래스를 사용하여 `객체`를 생성해보자.

```python
person_1 = Human()
person_2 = Human()
```

`객체`를 생성하는 방법은 일반 함수를 호출하는것과 동일하게 `클래스명()` 형태로 작성한다.

이제 생성된 `객체`를 통하여 `메서드`를 실행해본다.

```python
person_1.eat("chocolate")  # I am eating chocolate
person_2.study("Python")  # I am studying Python
```

`객체.메서드()` 형태로 해당 클래스 내부에 정의된 함수를 호출할 수 있다.  

우리가 일반적으로 `list객체.append()`, `dictionary객체.items()`와 같이 사용하던 `메서드`의 원리이다.

### 2.2 Class Attributes and Instance Attributes

이제 클래스의 활용도를 더 높여보자.

클래스에 `메서드(기능)`만을 추가 하는것이 아닌 `attribute(속성)` 을 저장하여 클래스로 생성된 각 `인스턴스` 에 고유 데이터를 저장할 수 있다. 

`클래스 속성 (Class Attribute)` 은 말그대로 클래스 자체의 속성으로 해당 클래스로 생성된 모든 객체에 영향을 주게 된다. 

`인스턴스 속성 (Instance Attribute)` 은 각 인스턴스, 즉 객체의 속성으로 다른 객체에 영향을 주지 않는다. 

```python
class Human:
  id = 0  # Class Attribute
  
  def __init__(self, name, age):
    self.name = name  # Instance Attribute
    self.age = age  # Instance Attribute
    
  def eat(self, food):
    print(f"I am eating {food}")
		
  def study(self, subject):
    print(f"I am studying {subject}"
```

위와같이 각 `class attribute` 와 `instance attribute` 를  생성했다.

<aside>
💡 `__init__()` 메서드는 클래스가 **호출** 되었을 때 자동으로 가장 먼저 실행되는 함수이다. 이와같이 메서드 이름의 전과 후에 두개의 underscore, “_” 가 붙은 함수를 `special method` 또는 `magic method` 또는 `dunder(double underscore) method` 라고 부른다.
클래스가 호출 되었다는 의미는 해당 클래스의 `인스턴스` 가 생성 되었다는 의미이다. 다르게 말하면 클래스가 호출되지 않았거나 `객체` 가 생성되지 않았다면 `__init__()` 메서드는 호출되지 않은 상태이다.

</aside>

이제 객체를 생성하여 속성을 확인해보자. 

```python
harry = Human("Harry", 15)
potter = Human("Potter", 20)

Human.id  # 0  (class attributes)
Human.name  # AttributeError: type object 'Human' has no attribute 'name'
Human.age  # AttributeError: type object 'Human' has no attribute 'age'

harry.id  # 0  (class attribute)
harry.name  # Harry  (instance attribute)
harry.age  # 15  (instance attribute)

potter.id  # 0  (class attribute)
potter.name  # Potter  (instance attribute)
potter.age  # 20  (instance attribute)
```

위 예시처럼 기본적으로 `속성` 을 호출할 때는 `()` 괄호를 생략하고 `객체.속성명` 과 같이 접근한다. 

클래스 속성인 `Human.id` 의 경우 클래스가 호출되지 않았고, 객체가 생성되지 않았음에도 클래스 자체에서 바로 접근이 가능하다. 

반면, `Human.name` 과 `Human.age` 는 `클래스` 자체에서 접근이 불가능 하다. 그 이유는 `Human.name` 과 `Human.age` 는 `__init__()` 메서드가 실행되면서 생성이 되며, `__init__()` 메서드는 클래스가 호출되거나 객체가 생성될 때 실행되는 메서드이기 떄문이다. 

따라서 클래스 자체에서 `Instance Attribute` 인 `name` 과 `age` 에 접근하려고 하면 그런 `attribute(속성)` 은 존재하지 않는다는 `AttributeError` 가 발생하게된다. 

이제 속성에 대한 값을 변경하여 `클래스 속성` 과 `인스턴스 속성` 의 차이점과 활용법을 알아보자. 

```python
Human.id = 1

harry.name = "Ron"
harry.age = 17

potter.name = "Weasley"
potter.age = 21

harry.id  # 1
harry.name  # Ron
harry.age  # 17

potter.id  # 1
potter.name  # Weasley
potter.age  # 17

```

클래스 속성인`Human.id` 의 값을 변경하였다. 변경된 값은 모든 `인스턴스` 에서 동일하게 적용되는것을 볼 수 있다. 

하지만, 각 `인스턴스` 에서 설정한 `name` 과 `age` 속성은 각각 별개로 설정되어 적용되는 것을 볼 수 있다. 

이는 Python의 `Namespace(네임 스페이스)` 와 연관이 있는데, 쉽게말하면 하나의 변수명은 하나의 네임스페이스에 독립적으로 할당된다는 의미이다. 

<details>
  <summary>More about Namespace</summary>
    
    ```python
    id = 0
    
    def get_id():
    	id = 10
    	return id
    
    print(f"{id}은 전역 네임스페이스의 id값 입니다.")
    print(f"{get_id()}은 get_id() 함수의 로컬 네임스페이스의 id값 입니다.")
    print(f"전역 네임스페이스의 id 값인 {id}은 변하지 않았습니다.")
    
    # > 0는 전역 네임스페이스의 id값 입니다.
    # > 10는 get_id 함수의 로컬 네임스페이스의 id값 입니다.
    # > 전역 네임스페이스의 id 값인 0은 변하지 않았습니다.
    ```
    
    위 예시는 네임스페이스에 대한 예시를 보여준다. 
    
    우리는 모두 하나의 변수명이 한개 이상의 값을 갖을 수 없는것을 알고 있다. 
    
    하지만 위와같은 경우에는 id라는 동일한 변수명이 서로다른 값을 갖고있는 것을 확인할 수 있다. 이와같이 하나의 변수명이 서로다른 값을 갖을 수 있는 이유는 각 변수가 서로다른 네임 스페이스에 존재하기 때문이다.
    
    이해가 잘 되지 않는다면 Python의 dictionary 자료형과 같이 떠올려 볼 수 있다.
    
    Python의 dictionary 자료형에서 key값은 중복될 수 없지만, 아래와 같이 각각의 “id”가 서로다른 공간에 존재한다면 가능하다. 
    
    ```python
    {
        "global": {
            "id": 0,
        },
        "get_id": {
            "id": 10
        },
    }
    ```
</details>

`Attributes` 를 그럼 언제 사용해야할까?

`Class Attribute` 는 여러 `인스턴스` 에서 공용으로 사용되어야 하는 속성을 위해서 사용할 수 있다. 

`Instance Attribute` 는 각각의 `인스턴스` 에서 독립적으로 사용되어야 하는 속성을 위해서 사용할 수 있다.

<aside>
💡 서로다른 속성값이 참조되는 순서도 중요하다. `인스턴스` 에서 `Attribute(속성)` 를 참조하게되면 항상 `Instance Attribute` 를 먼저 참조하며, 참조되는 속성값이 없을 때 `Class Attribute` 를 참조하게된다. **(Instance Namespace → Class Namespace)**
</aside>

<aside>
💡 만약 위 예시에서 `harry.id = 20` 과 같이 설정하고 각 `harry.id` 와`potter[.](http://potter.id)id` 를 확인해보면 harry와 potter 인스턴스에 서로다른 id 값이 저장된걸 확인할 수 있다. 하지만 이는 올바른 `class attribute` 의 사용법이 아니며, `class attribute` 를 제대로 사용한 것 또한 아니다. 
`harry.id = 20` 과 같이 설정하게되면 이는 기존의`class attribute`를 수정한것이 아닌 새로운 `instance attribute`를 생성하게 된것이다. 그러면 속성값이 참조되는 순서에 의해서 새로 생성된 instance namespace가 먼저 참조되게되며, class instance를 참조하기 위해서는 `harry.__class__.id` 와 같이 인스턴스가 아닌 클래스로 직접 접근해야한다.

</aside>

## 3. self

아래 예제를 다시 한번 보자. 

```python
class Human:
  id = 0  # Class Attribute
  
  def __init__(self, name, age):
    self.name = name  # Instance Attribute
    self.age = age  # Instance Attribute
    
  def eat(self, food):
    print(f"I am eating {food}")
		
  def study(self, subject):
    print(f"I am studying {subject}"
```

`Human` 내부에 정의된 모든 메서드는 `self` 라는 파라미터를 가장 처음으로 갖고있다. 

하지만 우리가 위 함수를 사용할때는 아래와 같이 `self` 인자값에 인수를 넣어주지 않았다. 

```python
harry = Human('Harry', 15)
harry.study("Python")  # study has two parameters, but only passing one argument.

# > I am studying Python
```

여기에서 `self` 가 의미하는것은 객체 자기 자신이다. 

즉, `harry.study(”Python”)` 메서드를 호출할 떄, self 인자에는 `harry` 객체가 들어가게된다. 

아래와 같이 직접 증명해볼수도 있다. 

```python
class MyClass:
    
    def print_self(self):
        print(self)

obj = MyClass()
obj.print_self()   # <__main__.MyClass object at 0x110774f40>

print(obj)  # <__main__.MyClass object at 0x110774f40>
```

직접 생성된 객체를 출력하거나, 또는 print_self 메서드에서 받아온 `self` 인자값을 출력하면 동일한 메모리 위치에 저장된 MyClass 객체를 보여주는 것을 확인할 수 있다. 

`self` 는 즉 객체 자신을 의미하는 것으로, 아래와 같이 사용될 수 있다. 

```python
class Human:
    
    def __init__(self, firstname, lastname):
        self.firstname = firstname
        self.lastname = lastname
        
    def get_fullname(self):
        return f"{self.firstname} {self.lastname}"

harry = Human("Harry", "Potter")
fullname = harry.get_fullname()
print(fullname)  # Harry Potter
```

`get_fullname(self)` 메서드를 보자. 

우리가 `instance attribute`에 접근하기 위해 `객체.속성명` 처럼 작성해준 것 처럼, `self.firstname` 은 동일한 역할을 한다 (`self` 가 객체 그 자체이기 떄문에).

이렇게 `self` 를 활용하여 클래스에서 객체 속성에 접근할 수 있게된다. 

## 4. 클래스의 상속 (Inheritance)

클래스는 하나의 클래스 자체로도 활용이 가능하지만 다른 클래스를 상속받아서 여러 자식클래스를 활용할 수도 있다. 클래스의 상속을 활용하여 프로그램을 작성할 때 기능, 속성, 용도에 따라서 유연하게 객체를 만들고 활용할 수 있다. 

<details>
<summary>Tip</summary>

    Python의 모든 클래스는 기본적으로 Python의 내장 클래스인`Object` 클래스를 상속하게 된다. 
    
    과거 Python2 버전의 경우 class를 생성할 때 `class MyClass(Object):` 와 같이 필수적으로 `Object` 클래스를 상속한다는 것을 명시해주어야했다. 
    
    하지만 Python3 버전 이상부터는 클래스를 생성할때 필수적으로 명시해주지 않아도 자동으로 `Object` 클래스를 상속받게된다. 

</details>

아래 예제를 살펴보자.

```python
class Human:

    def __init__(self, name, yob):
        self.name = name
        self.yob = yob
    
    def say_hello(self):
        print(f"[{self.name}]: 안녕하세요. 제 이름은 {self.name} 입니다.")
        
    def say_year_of_birth(self):
        print(f"[{self.name}]: 저는 {self.yob}에 태어났습니다.")

class Developer(Human):

    def __init__(self, name, yob, **kwargs):
        super().__init__(name, yob)
        self.language = kwargs.get("language", "")
        self.preffered_os = kwargs.get("preffered_os", "")
        
    def develope(self):
        print(f"[{self.name}]: 저는 주로 {self.language} 언어로 개발을 합니다.")
        
    def use_os(self):
        print(f"[{self.name}]: 저는 {self.preffered_os} 운영체제를 선호합니다.")
        
        
class Singer(Human):
    
    def __init__(self, name, yob, **kwargs):
        super().__init__(name, yob)
        self.genre = kwargs.get("genre", "")
        self.in_group = kwargs.get("in_group", False)
    
    def say_hello(self):
        stage_name = "Granger"
        print(f"[{self.name}]: 안녕하세요. 제 이름은 {self.name}이며 {stage_name}으로 활동하고 있습니다.")
    
    def sing(self):
        print(f"[{self.name}]: 저는 {self.genre} 장르를 부르는 가수입니다.")
        
    def is_single():
        if self.in_group:
            print(f"[{self.name}]: 저는 그룹으로 활동합니다.")
        else:
            print(f"[{self.name}]: 저는 솔로로 활동합니다.")
```

`Developer` 와 `Singer` 라는 두개의 직업 클래스가 하나의 `Human` 클래스를 상속했다. 즉, 개발자와 가수는 한명의 사람이라는 공통점이 존재하면서도 서로 다른 직업을 갖고있다고 볼 수 있다. 

따라서 한명의 사람으로써 공통적으로 이름과 태어난 날짜를 갖고있고, 그것을 소개할 수 있음과 동시에 한명의 개발자 또는 가수로서 그 직업에 맞는 특성과 그게 맞는 역할을 수행할 수 있다. 

<aside>
💡 자식 클래스, Developer와 Singer, 에서 사용된 `super` 키워드는 부모 클래스를 의미한다. 즉, `super().__init__(name, yob)` 는 자식 클래스의 `인스턴스`가 생성될 때 부모 클래스의 __init__ 메서드도 함께 실행하여 부모 클래스에 선언된 `instance attribute` 를 함께 생성해주는 것을 의미한다.

</aside>

```python
harry = Developer("Harry", 1995, language="Python", prefferd_os="Windows")
ron = Developer("Ron", 1993, language="Java", preffered_os="Linux")
hermione = Singer("Hermione", 1996, genre="city-pop", in_group=False)

# Say Hello
harry.say_hello()
ron.say_hello()
hermione.say_hello()
print()  # empty line

# Say Age
harry.say_year_of_birth()
ron.say_year_of_birth()
hermione.say_year_of_birth()
print()  # empty line

# Profession
harry.develope()
ron.use_os()
hermione.sing()

# [Harry]: 안녕하세요. 제 이름은 Harry 입니다.
# [Ron]: 안녕하세요. 제 이름은 Ron 입니다.
# [Hermione]: 안녕하세요. 제 이름은 Hermione이며 Granger으로 활동하고 있습니다.
#
# [Harry]: 저는 1995에 태어났습니다.
# [Ron]: 저는 1993에 태어났습니다.
# [Hermione]: 저는 1996에 태어났습니다.
#
# [Harry]: 저는 주로 Python 언어로 개발을 합니다.
# [Ron]: 저는 Linux 운영체제를 선호합니다.
# [Hermione]: 저는 city-pop 장르를 부르는 가수입니다.
```

상속된 자식 클래스에서 부모 클래스에서 생성된 `instance attribute` 및 메서드를 공통으로 사용할 수 있는 모습을 볼 수 있다.  

`Singer` 클래스에서는 이미 부모 클래스에서 선언된 `say_hello()`메서드를 다시 정의해주는 것을 볼 수 있다. 이와같이 부모 클래스에서 정의된 메서드를 자식 클래스에서 재정으 하는것을 `메서드 오버라이딩(method overriding)` 이라고 부른다. 즉, 부모 클래스에서 정의된 메서드의 기능을 해당 자식 클래스에서 덮어씌워 자식 클래스만의 기능을 재정의 해주는 것이다. 

## 5. Magic Methods / Special Methods

Python에는 클래스 기반으로 객체 지향형 프로그래밍을 할 때 유용하게 사용할 수 있는 `special methods` 가 존재하는데, 이는 `special methods`, `magic methods` 또는 `dunder methods` 와 같이 여러 이름으로 불린다. 

우리가 위에서 사용한 `__init__` 메서드도 `special methods` 중 하나이다. 

아래 몇개의 예시를 살펴보자. 

### `__init__`

Initialize의 약자로 클래스가 호출되어 객체가 생성될 때 가장 처음으로 그리고 자동으로 호출되는 메서드이다. 

주로 `instance attribute` 를 선언할 때 사용된다. 

### `__call__`

클래스의 `인스턴스` 는 호출할 수 없다. 

즉, 보통 `인스턴스.메서드()` 와 같은형태로 인스턴스 내부에 정의된 함수를 호출하며, 일반 함수를 호출하는것과 같이 `인스턴스()` 와 같은 형태로 사용할 수 없다. 

하지만, 클래스 내부에 `__call__` 메서드를 정의해주면 `인스턴스()` 와 같은 형태로 인스턴스 자체를 일반 함수처럼 호출해서 사용할 수 있다.

### `__str__`

객체의 문자열화 한다.

`print()` 함수가 실행될 때, 클래스 내부에 있는 이 `__str__` 를 호출하게 된다. 

`__str__` 의 목적은 데이터의 추가적인 가공 또는 다른 타입의 데이터와 호환될 수 있도록 universal 한 데이터를 출력해주는 것에 대한 목적이 있다. 

### `__repr__`

Representation의 약자로 객체의 문자열로 “표현” 한다. 

`__str__` 과 비슷하지만 사용목적이 다르다. `__str__` 은 객체의 universal interface를 제공해주는 반면, `__repr__` 은 사람이 이해하기 쉽도록 객체에 대한 정의를 내려주는, 표현 해주는, 메서드이다. 

`print()` 함수로 객체를 출력할 때, 해당 객체 내 `__str__` 메소드가 정의되어있지 않다면 `__repr__` 을 호출해주게된다. 

등.. 매우 많은 `special methods` 가 존재한다. 

모든 special methods와 그 사용 및 활용법을 알기에는 그만큼의 시간과 노력이 필요하다. 

추가적인 내용을 공부해보고 싶은 분들을 위하여 아래 링크를 첨부한다. 

<details>
<summary>추가 공부</summary> 

    1. **Python 공식문서**

    https://docs.python.org/ko/3/reference/datamodel.html#emulating-generic-types
    
    - 내용이 방대하므로 좌측 패널의 목차에서 필요한 내용만 골라보자.

    
    2. **Python Special Methods에 대한 블로그 정리 글**
    
    https://velog.io/@khs0415p/python-special-method#__str__
    
    - 주요 special methods에 대한 정리와 예제, 블로그 포스트


    3. `__str__` 과 `__repr__` 의 차이점에 대한 고찰, 블로그 정리 글

    https://shoark7.github.io/programming/python/difference-between-__repr__-vs-__str__

    - `__str__` 과 `__repr__` 두 special methods에 대한 공통점과 차이점에 대한 고찰, 블로그 포스트

</details>