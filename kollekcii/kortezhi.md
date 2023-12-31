# Кортежи

Кортежи — неизменяемая последовательность

Это главное отличие **кортежей** от **списков**

```python
my_tuple = (1, 2, 3, 4, 5) # создание кортежа
names = ("Sergey", "Tatyana", "Oleg")
for n in names: # обход элементов кортежа
    print(n)

# кортежи поддерживают индексацию
name = names[0]
for i in range(len(names)): 
    print(names[i])
```

Кортежи поддерживают те же самые операции, что и списки, за исключением тех,  которые изменяют содержимое списка: `append(), remove(), insert(), reverse(), sort()`

Как создать **кортеж с одним элементом**:

```python
my_tuple = (1,) # создастся кортеж
value = (1) # создастся целочисленное значение
```

Зачем нужны кортежи?

* **Производительность**. Обработка кортежа выполняется быстрее, чем обработка списка
* **Безопасность**. Содержимое кортежа изменять нельзя, а значит мы можем быть уверены, что данные в нём не будут (например, случайно) изменены
* Некоторые операции в Python требуют применения кортежа

Преобразование между списками и кортежами

```python
nnumber_tuple = (1, 2, 3)
number_list = list(number_tuple)
str_list = ['один', 'два', 'три']
str_tuple = tuple(str_list)
```

_**Интерактив:**_

* В чём главное различие между списком и кортежем?
* Приведите причины существования кортежей
* Допустим, что переменная `my_list` ссылается на список. Напишите инструкцию, которая преобразует его в кортеж
* Допустим, что переменная `my_tuple` ссылается на кортеж. Напишите инструкцию, которая преобразует его в список

_**Практика:**_

* Создайте кортеж строк. Напечатайте последний элемент кортежа. Напечатайте длину каждой строки.&#x20;
* Создайте два кортежа, содержащих по одному элементу. Создайте третий кортеж, который будет содержать элементы обоих кортежей.
* Создайте кортеж чисел. Преобразуйте его в список, удалите последний элемент и преобразуйте результат в кортеж. Напечатайте его.
* Создайте кортеж из 5 элементов — случайных чисел в диапазоне от 0 до 1000.
