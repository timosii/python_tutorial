# Обработка исключений

***

**Практика**

***

Вспомним:

* Что такое ошибка в Python?
* Какие два типа ошибок выделяют?

***

Исключения (**Exceptions**) --- это логические ошибки, возникающие во время выполнения кода (в отличие от синтаксических, которые возникают _ДО_ выполнения кода)

Компьютер пытается сделать то, что мы его просим, но не может. Python готов к этому и обрабатывает такие ситуации --- и _выбрасывает (инициирует) исключение_

```python
3/0

~Traceback (most recent call last): # обратная трассировка
~  File "/home/runner/test/main.py", line 1, in <module>
~    3/0
~ZeroDivisionError: division by zero
```

Два подхода к обработке исключений:

* LBYL (Look Before You Leap: "_Посмотри, прежде чем прыгнуть_")
* Суть в том, чтобы проверить исключительную ситуацию _перед выполнением действия_

```python
number = 10
divisor = 0
if divisor != 0:
	result = number / divisor
else:
	result = None 
# значение None для представления неопределенного состояния
```

* EAFP (Easier to Ask for Forgiveness than Permission: "_Проще попросить прощения, чем разрешения_")
* Если операция завершается неудачей, исключение будет _перехвачено_ в **блоке исключения**
* Конструкция **try...except**:

```python
number = 10
divisor = 0
try:
	result = number / divisor
except ZeroDivisionError:
	result = None
~# внутри блока try расположены команды, которые могут выдавать исключения
~# если исключение произойдет, Python ищет блок except, который перехватывает исключение
```

```python
number_1 = 10 
number_2 = 0
number_3 = ''

try:
  result = number_1 + number_3
except TypeError as e:
  result = number_1 + number_2
~# переменной e присваивается объект: экземпляр исключения TypeError.
~# и с ней можно работать дальше в программе.
```

* Что делать, если мы не знаем, какое исключение может возникнуть?

```python
try:
	number = int(input())
	divisor = int(input())
	result = number / divisor
except ZeroDivisionError:
	result = "Ошибка деления на ноль!"
except ValueError:
	result = "Ошибка значения!"
```

```python
try:
	number = int(input())
	divisor = int(input())
	result = number / divisor
except (ZeroDivisionError, ValueError):
	result = "Возникла ошибка: либо деление на 0, либо ошибка значения"
except:
	result = "Что-то произошло"
```

```python
try:
	number = int(input())
	divisor = int(input())
	result = number / divisor
except Exception as ex:
    print(ex)
```

* конструкции try-except-else-finally:

```python
number_1 = 10 
number_2 = 0
number_3 = 1

try:
	result = number_1 + number_3
except:
	result = number_1 + number_2
else:
	result = number_1 ** 2
finally:
	print(result)
~# 100 т.к. выполнится try => else => finally
~# если number_3 будет строкой, мы попадем в except, тогда else не выполнится
~# finally выполнится всегда
~# в else добавляем код, который хотим запустить, если ошибок не возникло
```

```python
try:
    x = 1 / 0
except:
    print("Поймали ошибку")
finally:
    print("Эта строка все равно напечатается")
```

* _KeyboardInterrupt_ --- тоже вид исключения, который можно обработать. Тогда команда Ctrl + C перестанет срабатывать.

***

Помимо перехвата исключений мы можем также выдавать (инициировать) исключения в коде:

* **raise** --- возбудить исключение

```python
try:
	x = int(input())
    print(x / 0)
except:
    raise
# перехватим ошибку и возбудим её
```

```python
num = int(input())
if num % 2 == 0:
	raise Exception("Я не работаю с четными числами")
else:
	print(num)
~# инициируем собственные исключения - работают также как и встроенные
```

### Практика

```
1. Напишите программу, которая запрашивает ввод двух значений.
Если хотя бы одно из них не является числом, то должна выполняться
конкатенация строк. В остальных случаях введенные числа суммируются.

Примеры выполнения программы:

Первое значение: 4
Второе значение: 5
Результат: 9.0

Первое значение: a
Второе значение: 9
Результат: a9
```

```
2. Напишите программу, выполняющую функции простейшего каль-
кулятора. Программа получает два числа, а затем запрашивает опе-
ратор. Обеспечьте корректную обработку ввода, который не преоб-
разуется в числа. Обработайте ошибки деления на ноль.
```
