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

* Внутренняя функция может действовать как _замыкание._&#x20;
* _**Замыкание**_ — это функция, которая находится внутри другой функции и ссылается на переменные, объявленные в теле внешней функции
* Эта функция запоминает значения из внешней области видимости, даже если эта область уже недоступна

```python
def say_name(name):
    def say_goodbye():
        print(f"Don't say me goodbye, {name}!")

    return say_goodbye

f = say_name("Sergey")
f2 = say_name("Python")
f()
f2()
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

```python
def add_number(n):
    def inner(x):
        return x + n
    return inner

add_five = add_number(5)
add_ten = add_number(10)

print(add_five(3))  # 8
print(add_ten(3))   # 13
```

* Применение замыканий позволяет создавать функции с доступом к переменным, _находящимся вне их области видимости_

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
```
