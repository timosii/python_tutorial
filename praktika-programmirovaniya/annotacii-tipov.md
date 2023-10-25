# Аннотации типов

**Аннотации типов** — это возможность указать типы параметров и возвращаемое значение у функции в Python.&#x20;

* Это не требование языка, но помогает программистам в дальнейшей разработке: улучшает читаемость кода и повышает его надежность.

Давайте рассмотрим простой пример функции без аннотаций типов:

```python
def concat(first, second):
    return first + second
```

* Эта функция конкатенирует две строки в одну. При этом с первого взгляда на код сложно понять, что происходит в нем: какие типы у аргументов, почему функция работает со строками, а не складывает, например, два числа.
* Если в дальнейшем использовать эту функцию в коде, то может возникнуть необходимость проверять типы аргументов перед передачей их в функцию, что увеличивает объем кода и затрудняет его понимание.

Теперь давайте добавим **аннотации типов к функции**:

```python
def concat(first: str, second: str) -> str:
    return first + second
```

* Здесь мы указали, что аргументы `first` и `second` должны быть строкового типа (`str`). Возвращаемое значение тоже будет строковым. Когда мы будем использовать эту функцию в коде, нам будет проще понять, какие типы аргументов можно передавать и какой тип возвращаемого значения ожидается.

Аннотации типов также могут быть использованы для **определения типов переменных** внутри функции. Например:

```python
def double(n: int) -> int:
    result: int = n * 2
    return result
```

* В этом примере мы определили тип переменной `result` как `int`, используя аннотацию типа.

Аннотации типов — это не строгая проверка типов в Python.&#x20;

* Python остаётся динамически типизированным языком; аннотации типов не влияют на то, какой аргумент может быть передан в функцию и что она может вернуть
* Но использование аннотации типов упрощает чтение и понимание кода и помогает обнаружить ошибки

_**Практика:**_

* Реализуйте функцию `word_multiply()`. Она должна принимать два параметра:
  * Строку
  * Число, которое обозначает, сколько раз нужно повторить строку

```python
# пример работы функции
text = 'python'
print(word_multiply(text, 2)) # => pythonpython
print(word_multiply(text, 0)) # => 
```

* Укажите аннотации типов при объявлении функции