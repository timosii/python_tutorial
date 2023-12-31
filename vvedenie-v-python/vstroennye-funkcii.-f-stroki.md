# Встроенные функции. f-строки

***

[**Практика**](vstroennye-funkcii.-f-stroki.md#praktika)

***

* Функция **print()**

```python
print() # переход на новую строку
print("Hello") # Hello
print("Hello,", "World", sep='***') # Hello,***World
print("Hello" + "World") # HelloWorld
print("Hello", end='***') # Hello***
```

* Функция **input()**
* Результат работы функции input() — **строка**

```python
a = input() 
# программа предложит пользователю ввести значение,
# которое сохранится в переменную a
a = input("Введите значение a: ")
# строка внутри скобок называется промпт
# она отобразится в консоли перед вводом
```

* Функции **len() max() min() abs()**

```python
len("Hello") # 5 - возвращает длину переданной строки
abs(-54) # 54 - модуль переданного числа
max(5, 2, 10) # 10
min(5, 2, 10) # 2
```

* **Преобразование типов**

```python
int("5") # 5
float("5.0") # 5.0
str(567) # "567"
bool("Hello") # True
type(5) # <class int> узнать тип переданного значения
a = int(input()) # в переменной a сохраним число
```

* **f-строки**

```python
name = "Sergey"
print(f"Поприветствуем {name}") 
# Поприветствуем Sergey
num_1 = 5
num_2 = 11
print(f"Сложим {num_1} и {num_2} и получим {num_1 + num_2}")
# Сложим 5 и 11 и получим 16
```

* Каждый символ имеет свой код в [таблице символов ASCII](https://www.industrialnets.ru/files/misc/ascii.pdf)
* Когда мы сравниваем строки, сравниваются коды их символов
* Это называется **лексикографическим** сравнением строк

```python
name_1 = "Kirill"
name_2 = "Fedor"

print(name_1 > name_2)
~ # True

name_3 = "Kirill"
name_4 = "Katya"

print(name_3 < name_4)
~ # False
```

* **Округление. Функция round()**

```python
num = 3.1415926535
print(f"{num:.2f}") # 3.14
# округление до 2 знака - потому что перед f цифра 2
print(round(num, 2)) # 3.14
# также округление до 2 знака - второй аргумент функции round
```

### Практика

```
1. Пользователь вводит строку. Выведите на экран её длину.

2. Напишите программу, которая сравнивает три введенных символа.
Выведите на экран символ, который больше и его код.

3. Округлите число 7.88911 до сотых;
округлите число 2.25 до целого, выведите на экран сумму чисел.

4. Пользователь вводит сумму в одной валюте. Программа должна
конвертировать ее в другую валюту и результат отобразить на экран.
Валюты выберете самостоятельно.

5. Напишите программу сравнения двух введенных строк. Пользователь
вводит две строки, программа сначала выводит на экран ту, которая больше
и ту, которая меньше лексикографически; затем выводит на экран ту
которая длиннее и ту, которая короче по длине.
```
