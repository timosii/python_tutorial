# Замыкание. Карринг. Декораторы.

### Внутренние функции

* Мы можем определить функцию внутри другой функции

```python
def outer(a, b):
    def inner(c, d):
        return c + d
    return inner(a, b)
outer(4, 7)
# 11
```

* Внутренние функции могут быть полезны при выполнении некоторых сложных задач более одного раза внутри другой функции. Это позволит избежать дублирования кода
* Рассмотрим пример работы со строкой, когда внутренняя функция добавляет текст в свой аргумент:

```python
def hello(saying):
    def inner(name):
        return f"Hello, {name}!"
    return inner(saying)

hello("Igor")
# 'Hello, Igor!'
```

_**Практика:**_

* Напишите функцию, которая принимает аргумент — число. В теле функции определите внутреннюю функцию, которая принимает строку и число. Значение строки по умолчанию — `"Python"`. Число — это количество, сколько раз должна быть продублирована строка. Верните результат работы внутренней функции во внешней функции. Протестируйте программу.

### Замыкания

* Внутренняя функция может действовать как _замыкание, если возвращает функцию_
* _**Замыкание**_ — это функция, которая находится внутри другой функции и ссылается на переменные, объявленные в теле внешней функции

```python
def talk(n, name):
    def hello():
        return f'Привет {name}.'
    def goodbye():
        return f'Пока {name}.'
    if n > 0:
        return hello
    else:
        return goodbye

talk(1, 'Андрей')()
# 'Привет Андрей.'
```

{% code overflow="wrap" %}
```python
def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function

closure = outer_function(10)
print(closure(5))  # => 15
# Замыкание (closure) позволяет сохранить значение между вызовами и может быть использовано внутри inner_function даже после того, как outer_function уже завершила свою работу
```
{% endcode %}

{% code overflow="wrap" %}
```python
def add_number(n):
    def inner(x):
        return x + n
    return inner

add_five = add_number(5) # add_five хранит внутреннюю функцию c сохраненной переменной n == 5
add_ten = add_number(10) # а add_ten сохранила n == 10

print(add_five(3))  # 8
print(add_ten(3))   # 13
```
{% endcode %}

* Применение замыканий позволяет создавать функции с доступом к переменным, _находящимся вне их области видимости_ и запоминать значения переменных

```python
def password_protected(password):
    def inner():
        if password == 'secret':
            print("Access granted")
        else:
            print("Access denied")
    return inner

login = password_protected('secret')
login()  # Access granted
# таким образом функция login "запомнила" значение переменной password
```

* Внутри внешней функции мы можем создавать переменные и изменять их во внутренних функциях
* Для этого используется ключевое слово `nonlocal`**:**

{% code overflow="wrap" %}
```python
def maker(a):
    x = a * 5
    def add(b):
        nonlocal x # мы указываем, чтобы следующая инструкция изменила внешнюю переменную x
        return b + x
    return add

test = maker(6)
test(10)
# 40
```
{% endcode %}

* Пример использования замыкания для генерации ID:

```python
def id_generator():
    unique_id = 0

    def generate_id():
        nonlocal unique_id
        unique_id += 1
        return f"ID{unique_id}"

    return generate_id

get_id = id_generator()
print(get_id())  # ID1
print(get_id())  # ID2
```

_**Практика:**_

1. Напишите функцию которая принимает имя в качестве аргумента и добавляет к имени заданную строку. Используйте замыкание.

_**Пример работы программы:**_

```python
love_python = func("любит Python")
love_python("Игорь") # Игорь любит Python
love_python("Татьяна") # Татьяна любит Python
```

2. Создайте функцию для генерации паролей. Функция должна принимать символы, из которых будет генерироваться пароль (установите для этого значение по умолчанию), и длину пароля. При каждом вызове она должна возвращать новый случайный пароль. Используйте замыкание и модули `random` и `string`

_**Пример работы программы:**_

```python
generate_8_char_password = password_generator(8)
print(generate_8_char_password())  # Например: "rT3uF9pW"
print(generate_8_char_password())  # Еще один случайный пароль
```

### Карринг

* **Карринг** (currying) — это техника в функциональном программировании, при которой функция, принимающая несколько аргументов, преобразуется в последовательность функций, каждая из которых принимает по одному аргументу.&#x20;
* Это позволяет вам создавать более специализированные функции и частично применять аргументы.

```python
# функция сложения двух чисел
def add_nums(x, y):
    return x + y


# применяем карринг
def add(x):
    def add_x(y):
        return x + y
    return add_x

# Создаем функцию для сложения на 5
add_5 = add(5)

# Теперь можем использовать add_5 как отдельную функцию
result = add_5(3)  # Результат: 8
```

* Ещё один пример:

```python
def greet(greeting):
    def greet_name(name):
        return f'{greeting}, {name}!'
    return greet_name

say_hi = greet('Привет')
say_hello = greet('Здравствуй')

print(say_hi('Анна'))  # Результат: "Привет, Анна!"
print(say_hello('Петр'))  # Результат: "Здравствуй, Петр!"
```

* Карринг удобен, когда вы хотите создавать множество функций, используя один и тот же "шаблон" и частично применять аргументы.

_**Практика:**_

* Создайте функцию умножения двух чисел. Используйте карринг

### Декораторы

* Иногда нам нужно модифицировать существующую функцию, не меняя при этом исходный код
* **Декоратор** — это функция, которая принимает одну функцию в качестве аргумента и возвращает другую функцию. По сути это "обертка" для нашей функции, которая добавляет ей функционал

```python
def func_decorator(func):
    def wrapper(): 
        print("---------что-то делаем перед вызовом функции ------")
        res = func() 
        print("---------что-то делаем после вызова функции-------")
        return res 
    return wrapper

def some_func():
    print("Работает функция some_func!")
    
func_decorator(some_func)()
# ---------что-то делаем перед вызовом функции ------
# Работает функция some_func!
# ---------что-то делаем после вызова функции-------
```

* Добавим аргументы и создадим дополнительную переменную для задекорированной функции:

```python
def func_decorator(func):
    def wrapper(num1, num2): 
        print("---------что-то делаем перед вызовом функции ------")
        res = func(num1, num2) 
        print("---------что-то делаем после вызова функции-------")
        return res 
    return wrapper

def some_func(num1, num2):
    print(f"Работает функция some_func! Кстати числа равны {num1} и {num2}")
    
upgrade_some_func = func_decorator(some_func)
upgrade_some_func(5, 10)
```

* Для того чтобы сделать декоратор универсальным,  можно сразу указать _все возможные аргументы_ (позиционные и ключевые) таким образом:

```python
def func_decorator(func):
    def wrapper(*args, **kwargs): 
        print("---------что-то делаем перед вызовом функции ------")
        res = func(*args, **kwargs) 
        print("---------что-то делаем после вызова функции-------")
        return res 
    return wrapper
    
def some_func(num1, num2):
    print(f"Работает функция some_func! Кстати числа равны {num1} и {num2}")
    
upgrade_some_func = func_decorator(some_func)
upgrade_some_func(3, 5)
```

* В Python есть "синтаксический сахар" — более удобная форма записи для декораторов:

{% code overflow="wrap" %}
```python
@func_decorator # декорируем функцию some_func
def some_func(num1, num2):
    print(f"Работает функция some_func! Кстати числа равны {num1} и {num2}")

some_func(3, 5) # т.к. мы декорировали функцию перед определением, она сработает вместе с декоратором
```
{% endcode %}
