# Стандарты написания кода

* В каждом языке программирования есть свой стандарт написания кода — набор правил, который рекомендовано соблюдать
* Стандарт, принятый в Python, называется [**PEP 8** ](https://pep8.org/)

Посмотрите на _примеры кода._ Попробуйте предположить, что делает функция:

<details>

<summary>Первый  пример</summary>

```python
def s(i,d,s):
 t=0
 for j in i:
  t+=j
 if d:
  t-=(t*s)
 return t
```

</details>

<details>

<summary>Второй пример</summary>

```python
def calculate_total_cost(items, discount, size_of_discount):
    total = 0
    for item_cost in items:
        total += item_cost
    if discount:
        total -= (total * size_of_discount)
    return total
```

</details>

_Основные моменты:_

* 4 пробела в качестве отступа. Не используйте табуляцию.
* Именуйте функции и переменные в стиле "snake\_case"
* Соблюдайтедлину строки 79 символов, длину комментариев 72 символа
* Вокруг операторов ставьте пробелы. Кроме присвоения для аргументов функций — тогда пробел вокруг "=" не ставится
* Используйте пропуск строки для отделения смысловых частей кода
* Используйте пропуск в две строки между функциями

_Несколько примеров:_&#x20;

```python
# YES — ДЕЛАЙТЕ ТАК:
spam(ham[1], {eggs: 2})
spam(1)
x = 1
y = 2
long_variable = 3
#----------
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)
#----------
def complex(real, imag=0.0):
    return magic(r=real, i=imag)

#NO — ВНИМАНИЕ (!) — ТАК НЕ РЕКОМЕНДОВАНО ДЕЛАТЬ:
spam( ham[ 1 ], { eggs: 2 } )
spam (1)
x             = 1
y             = 2
long_variable = 3
#----------
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
#----------
def complex(real, imag = 0.0):
    return magic(r = real, i = imag)
```
