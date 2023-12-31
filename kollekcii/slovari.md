# Словари

**Словарь** — объект-контейнер, который хранит коллекцию данных. Каждый элемент в словаре имеет две части: **ключ** и **значение**. Ключ используют, чтобы установить местонахождение конкретного значения.

_Примеры словарей:_

* "Большой толковый словарь" — пары _слово_: _его значение_
* Идентификационный номер и имя сотрудника компании. По номеру мы можем установить имя сотрудника. Пары _номер_: _имя_

Пары ключ: значение часто называются _отображениями (mappings)_, потому что по каждому ключу поставлено в соответствие значение, т.к. каждый ключ как бы _отображается на соответствующее ему значение_

```python
# создание словаря
phonebook = {'Сергей': '555-1111', 'Татьяна': '555-2222', 'Олег': '555-3333'}
# словарь phonebook содержит три элемента -- три пары ключ: значение
```

```python
# доступ к значению словаря
phonebook['Сергей'] # 555-1111
phonebook['Татьяна'] # 555-2222
```

* Значения в словаре могут быть объектами любого типа, но ключи должны быть немутируемыми (неизменяемыми) объектами
* При этом в одном словаре могут храниться ключи и значения разных типов

```python
test_dict = {1: ['Hi', 'Hello']}
test_dict_2 = {['Hi', 'Hello']: 2} # будет ошибка -- список изменяемый объект
```

* Вхождение в словарь

```python
phonebook = {'Сергей': '555-1111', 'Татьяна': '555-2222', 'Олег': '555-3333'}
if 'Сергей' in phonebook:
    print(phonebook['Сергей'])
    
if 'Александр' not in phonebook:
    print('Александр не найден')
```

_**Практика:**_

* Создайте словарь, где числа от 1 до 5 являются ключами, а их запись текстом — значениями (напр. "один", "два" и т.д.)
* Напишите функцию, которая принимает в качестве параметров словарь и число, которое нужно найти. Если число есть в словаре — верните `True`, иначе — `False`
* При помощи функции определите, есть ли в словаре числа: 2, 4, 6, 8

#### Добавление элементов в существующий словарь

Словарь — мутируемый объект, значит мы можем добавлять в него элементы

```python
имя_словаря[ключ] = значение # общий формат
phonebook['Антонина'] = '555-1234' # добавим новый элемент словаря
phonebook['Сергей'] = '555-4321' # если элемент существует, заменим значение
```

#### Удаление элементов словаря

{% code overflow="wrap" %}
```python
del phonebook['Сергей'] # удаляем элемент словаря
phonebook['Сергей'] # пытаемся получить доступ к несуществующему элементу -- получим ошибку KeyError
del phonebook['Антон'] # пытаемся удалить несуществующий элемент -- тоже получим ошибку KeyError
# Чтобы не получить ошибку при удалении элемента, воспользуемся оператором in
if 'Антон' in phonebook:
    del phonebook['Антон']
```
{% endcode %}

#### Получение количества элементов в словаре

```python
num_items = len(phonebook)
```

#### Создание пустого словаря

```python
phonebook = {}
phonebook['Сергей'] = '555-1111'
phonebook['Татьяна'] = '555-2222'
phonebook['Олег'] = '555-3333'
# создали пустой словарь и наполняем его в программе
phonebook = dict() # ещё один способ создания пустого словаря
```

_**Практика:**_

* Создайте пустой словарь
* Добавьте в него элементы — названия типов данных в Python в качестве ключей и один пример этого типа данных в качестве значения (например: 'int': 5)
* Удалите изменяемые типы данных
* Распечатайте получившийся результат

#### Применение цикла for для обхода словаря

Для перебора всех **ключей** словаря применяется цикл `for`:

```python
for key in phonebook:
    print(key)
    
for key in phonebook:
    print(key, phonebook[key])
```

_**Практика:**_

* Создайте словарь `capitals` из 5 элементов, где ключ — государство, значение — столица этого государства
* Создайте пустой список. Проитерируйтесь по словарю при помощи цикла `for`. Добавьте в список государства, столицы которых имеют длину больше 6 букв
* Распечатайте получившийся список

#### Основные  методы словарей

{% code overflow="wrap" %}
```python
dict.clear() - очищает словарь
dict.copy() - возвращает копию словаря

dict.get(key[, default]) - возвращает значение ключа, но если его нет, не бросает исключение, а возвращает default (по умолчанию None)

dict.items() - возвращает пары (ключ, значение)

dict.keys() - возвращает ключи в словаре

dict.pop(key[, default]) - удаляет ключ и возвращает значение. Если ключа нет, возвращает default (по умолчанию бросает исключение)

dict.popitem() - удаляет и возвращает пару (ключ, значение). Если словарь пуст, бросает исключение KeyError

dict.setdefault(key[, default]) - возвращает значение ключа, но если его нет, не 
бросает исключение, а создает ключ со значением default (по умолчанию None)

dict.values() - возвращает значения в словаре
```
{% endcode %}

#### Включение в словарь (dict comprehensions)

Это выражение, которое читает последовательность входных элементов и использует эти входные элементы **для создания словаря**. Включение в словарь _аналогично списковому включению._

{% code overflow="wrap" %}
```python
numbers = [1, 2, 3, 4, 5]
# создадим словарь, ключи в котором будут числа из numbers, а значениями - квадраты этих чисел
# т.е. мы хотим получить такой словарь: 
# {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
squares = {}
for n in numbers:
    squares[n] = n ** 2
# решим эту задачу при помощи включения в словарь:
squares = {n: n ** 2 for n in numbers} # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
# в левой части - выражение результата, т.е. то, что мы получим
# в правой части - выражение итерации - то, по чему итерируемся
# умножим на 2 и ключи и значения словаря squares
squares_double = {k * 2: v * 2 for k, v in squares.items()}
```
{% endcode %}

_**Практика:**_

1. При помощи включения в словарь создайте словарь, где ключи — элементы списка `numbers = [7, 3, 2, 12, 6]`, а значения — эти же числа, умноженные на 10
2. Предположим у нас есть словарь с оценками учеников:

{% code overflow="wrap" %}
```python
test_averages = {'Petr': 4, 'Sergey': 2, 'Tatyana': 7, 'Anatoliy': 10, 'Larisa': 12, 'Vladimir': 6, 'Olga': 3}
```
{% endcode %}

* Создайте новый словарь `high_scores`, в котором будут только те ученики, **чьи оценки больше 6**. Выполните задачу при помощи `dict_comprehensions`
