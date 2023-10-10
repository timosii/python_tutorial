# Циклы

***

[**While**](cikly.md#while)\
[**For**](cikly.md#for)\
[**Валидация данных**](cikly.md#validaciya-dannykh)\
[**Вложенные циклы**](cikly.md#vlozhennye-cikly)\
[**Операторы break continue else**](cikly.md#operatory-break-continue-else)\
[**Практика**](cikly.md#praktika)

***

* Циклы --- это _структуры c повторением_.
* Одно выполнение любого циклического процесса называется **итерацией**

***

#### While

* **while** --- цикл с условием повторения

```python
# while - цикл с предусловием - условие повторяется перед итерацией

программа
...
while <условие>: 
	делаем раз 
	делаем два
продолжение программы
# проверяется условие - если True, то выполнится тело цикла
# дальше снова проверяется условие -
# если True - снова выполнится тело цикла. И так до тех пор, пока условие
# не станет False.
# если условие False с самого начала - тело цикла будет проигнорировано.
```

```python
a = 0
while a < 5: # пока условие True - выполняем блок ниже
	print(a)
	a += 1
# 0
# 1
# 2
# 3
# 4
```

* Бесконечные циклы

```python
keep_going = True
while keep_going:
	print("I'm working")
# этот цикл никогда не завершится, т.к. мы не меняем keep_going
# важно продумывать условие выхода из цикла
```

* Конструкция **while True** --- способ использовать _постусловие_ в while --- то есть когда условие проверяется во время итерации, а не перед ней

```python
N = 10
Sum = 0

while True:
	Sum += N
	N -= 1
	
	if N == 0: # вводим состояние, при котором нужно остановить цикл
		break
		
print(f"Sum of First 10 Numbers is {Sum}")
```

* Когда выполняется условие цикла while --- до или после того, как он выполнит итерацию?
* Сколько раз сообщение будет напечатано в первом примере? Сколько во втором?

```python
# пример 1
count = 0
while count > 0:
	print("Привет, Мир!")

# пример 2
count = 0
while count >= 0:
	print("Привет, Мир!")
```

***

#### For

* **for** --- цикл со счетчиком повторений
* Количество итераций _известно заранее_

```python
# for - цикл cо счетчиком

программа
...
for <переменная> in [значение1, значение2 ...]:
	делаем раз
	делаем два
продолжение программы
# переменной перед каждой итерацией цикла присваивается значение из списка
# когда список закончится, произойдет выход из цикла
```

```python
for name in["Tatyana", "Denis", "Vladimir", "Natalya"]:
	print(len(name))
	print(f"{name} " * 2)
# 7
# Tatyana Tatyana 
# 5
# Denis Denis 
# 8
# Vladimir Vladimir 
# 7
# Natalya Natalya 
```

```python
for number in [0, 1, 2, 3, 4, 5]:
	print(f"Квадрат числа {number} равен {number ** 2}")
# Квадрат числа 0 равен 0
# Квадрат числа 1 равен 1
# Квадрат числа 2 равен 4
# Квадрат числа 3 равен 9
# Квадрат числа 4 равен 16
# Квадрат числа 5 равен 25
```

* Диапазоны чисел. Функция **range()**
* **range()** создает итерируемый объект, пригодный для итеративной обработки в цикле
* Принимает аргументы: начало, конец и шаг диапазона
* При этом величина шага может быть отрицательной --- тогда сгенерируется обратная последовательность

```python
# генерация арифметической прогрессии - диапазона чисел
range(start, stop, step)
# start - число, с которого начинаем диапазон (по умолчанию 0)
# step - число, которым заканчиваем диапазон
# step - шаг диапазона (по умолчанию 1)
```

```python
for number in range(6):
	print(f"Квадрат числа {number} равен {number ** 2}")
# Квадрат числа 0 равен 0
# Квадрат числа 1 равен 1
# Квадрат числа 2 равен 4
# Квадрат числа 3 равен 9
# Квадрат числа 4 равен 16
# Квадрат числа 5 равен 25
```

* Что покажут фрагменты кода в примерах?

```python
# пример 1
for number in range(0, 501, 100):
	print(number)
# 0
# 100
# 200
# 300
# 400
# 500
```

```python
# пример 2
for number in range(10, 100, -10):
	print(number)
```

```python
# пример 3
for number in range(1000, 100, -100):
	print(number)
# 1000
# 900
# 800
# 700
# 600
# 500
# 400
# 300
# 200
```

* **Аккумулятор**, или аккумуляторная переменная

```python
s = 0
for num in range(10):
	s += 1
```

```python
total = 0
nums_count = 5
for num in range(nums_count):
	total += int(input("Введите число, которое хотите прибавить: "))

print(f"Общая сумма составила: {total}")
# Введите число, которое хотите прибавить: 5
# Введите число, которое хотите прибавить: 4
# Введите число, которое хотите прибавить: 3
# Введите число, которое хотите прибавить: 2
# Введите число, которое хотите прибавить: 1
# Общая сумма составила: 15
```

* Когда использовать **while**, а когда **for**?
  * **while** --- когда мы не знаем, сколько итераций нам предстоит
  * **for** --- когда мы знаем, сколько итераций предстоит

***

#### Валидация данных

* **Валидация данных** --- процесс проверки данных на корректность
* Корректность данных определяет разработчик
* _Например_, если по нашей задумке программа должна работать только с положительными числами, мы должны убедиться, что пользователь вводит положительное число --- то есть мы должны провалидировать входные данные

```python
score = int(input("Введите оценку за контрольную работу: "))
while score < 0 or score > 5:
    print("Ошибка: оценка не может быть отрицательной или выше 5")
    score = int(input("Введите правильную оценку: "))
```

```
Петр занимается торговлей. Он покупает товары по оптовой цене, делает
надбавку и продает по розничной, более высокой цене. Коэффицент надбавки
составляет 2.5. Так выглядит программа для добавления товаров:
```

```python
INCREASE = 2.5
keep_going = "да"

while keep_going == "да":
    opt_cost = float(input("Введите оптовую стоимость товара: "))
    retail = opt_cost * INCREASE
    print(f"Розничная цена составляет: {retail:.2f}")
    keep_going = input("Ещё есть товары? ")
```

```
Однако Петр стал замечать, что иногда в выводе появляются отрицательные
числа - видимо из-за опечаток сотрудников. Добавим валидацию данных для
программы:
```

```python
INCREASE = 2.5
keep_going = "да"

while keep_going == "да":
    opt_cost = float(input("Введите оптовую стоимость товара: "))
    while opt_cost <= 0:
        print("Проверьте корректность введенной цены!")
        opt_cost = float(input("Введите правильную оптовую стоимость товара: "))
    retail = opt_cost * INCREASE
    print(f"Розничная цена составляет: {retail:.2f}")
    keep_going = input("Ещё есть товары? ")
```

* Когда нужно валидировать данные?
* Приведите пример валидации данных

***

#### Вложенные циклы

```
Человеку необходимо подняться на 5-й этаж.
Сейчас он находится на первом этаже, между каждыми двумя этажами по 20 ступенек.
Пройдя 70 ступенек подряд, человек устает и останавливается, чтобы отдохнуть
```

```python
floor = 1
energy = 70
print(f"I'm on the {floor} floor")
while floor != 5:
    step = 0
    while step != 20:
        step += 1
        energy -= 1
        if energy == 0:
            print("I'm tired, I will rest a little")
            energy += 70
    floor += 1
    print(f"Now I'm on the {floor} floor")
print("I've got to the right floor")
# I'm on the 1 floor
# Now I'm on the 2 floor
# Now I'm on the 3 floor
# Now I'm on the 4 floor
# I'm tired, I will rest a little
# Now I'm on the 5 floor
# I've got to the right floor
```

* Во время _каждой_ итерации _внешнего_ цикла происходит выполнение _всех итераций_ внутреннего цикла

```python
for i in range(1, 10): # проитерироваться с 1 до 9
     for j in range(1, 10): 
     # в каждой итерации, т.е. при каждом значении i проитерироваться
     # с 1 до 9 при помощи переменной j
         print(i * j, end="\t") # перемножить i и j для каждой итерации
     print("\n") # по окончании каждого ВНЕШНЕГО цикла перейти на новую строку
# 1   2   3   4   5   6   7   8   9

# 2   4   6   8   10  12  14  16  18

# 3   6   9   12  15  18  21  24  27

# 4   8   12  16  20  24  28  32  36

# 5   10  15  20  25  30  35  40  45

# 6   12  18  24  30  36  42  48  54

# 7   14  21  28  35  42  49  56  63

# 8   16  24  32  40  48  56  64  72

# 9   18  27  36  45  54  63  72  81
```

```python
for hours in range(24):
     for minutes in range(60):
         for seconds in range(60):
             print(hours, ':', minutes, ':', seconds)
```

* Графика при помощи вложенных циклов

```python
for row in range(5):
    for col in range(6):
        print('*', end='')
    print()
# *****
# *****
# *****
# *****
# *****
# *****
```

```python
for row in range(8):
    for col in range(row + 1):
        print('*', end='')
    print()
# *
# **
# ***
# ****
# *****
# ******
# *******
```

```python
n = 7
for row in range(n):
    for col in range(n - row):
        print('*', end='')
    print()
# *******
# ******
# *****
# ****
# ***
# **
# *
```

```python
n = 7
for row in range(n):
    print('#', end='')
    for col in range(row):
        print(' ', end='')
    print('#')
##
# #
#  #
#   #
#    #
#     #
#      #
```

***

#### Операторы break continue else

* **break** --- прерывает выполнение цикла

```python
num = 15
for i in range(num):
	if i == 5:
		break
	print(i)
```

* **continue** --- пропустить текущий цикл и перейти к следующему

```python
for num in range(40, 51):
	if num == 45:
		continue
	print(num)
```

* **else** --- выполняется только тогда, когда выход из цикла был осуществлен НЕ через оператор break

```python
for num in range(5):
	print(num)
else:
	print("Числа закончились")
```

```python
i = 0
while i < 5:
	print(i)
	i += 1
else:
	print("Конец")
```

```python
for num in range(5):
	if num == 3:
		break
	else:
		print(num)
else:
	print("Числа закончились")
```

```python
i = 0
while i < 5:
	if i == 3:
		break
	else:
		print(i)
		i += 1
else:
	print("Конец")
```

* Пример программы, которая предлагает пользователю угадать число от 1 до 20. Для прекращения работы с программой пользователь может ввести отрицательное число

```python
from random import randint

n = 20
to_be_guessed = randint(1, 20)
guess = 0
while guess != to_be_guessed:
	guess = int(input("New number: "))
	if guess > 0:
		if guess > to_be_guessed:
			print("Number too large")
		else:
			print("Number too small")
	else:
		print("Sorry, that you're giving up!")
		break
else:
	print('Congratulation!')
```

### Практика

```
1. Напишите цикл while, который выводит числа от 0 до 100
2. Напишите цикл while, который позволяет пользователю ввести число. Число должно быть
умножено на 10 и результат присвоен переменной с именем product. Цикл должен
повторяться до тех пор, пока product меньше 1000. На экран выведите
количество пройденных циклов.
```

```
3. Пользователь вводит с клавиатуры два числа. Нужно показать все четные
числа в диапазоне между введенных чисел.

4. Напишите программу, вычисляющую сумму всех нечётных чисел в диапа-
зоне от до включительно (вводятся с клавиатуры).
 
5. Напишите программу, которая принимает от пользователя начало и конец 
диапазона. На экран выводятся числа этого диапазона и квадратные корни этих
чисел с точностью до 2 знаков после запятой

6. Пользователь вводит с клавиатуры число. Требуется посчитать факториал
числа. Например, если введено 3, факториал числа 1*2*3 = 6.
Формула для расчета факториала: n! = 1*2*3...*n, где n - число
для расчета факториала.

7. Пользователь вводит с клавиатуры длину линии. Нужно отобразить на экране
горизонтальную линию из *, указанной длины. Например, если было введено 7,
тогда вывод на экран будет такой: *******.
```

```
8. Напишите программу, которая запрашивает у пользователя числа до тех
пор, пока каждое следующее число больше предыдущего. В конце програм-
ма сообщает, сколько чисел было введено.
```

```
9. Написать игру "Угадай число". Программа загадывает число в диапазоне от 1
до 500. Пользователь пытается его угадать. Сначала вводится загаданное
программой число, затем число, введенное пользователем.

После каждой попытки программа выдает подсказки - больше или меньше его число
загаданного. Предусмотреть выход по 0 в случае, если пользователю надоело
угадывать число.

Дополнительно *: Реализовать валидацию данных. Реализовать статистику - за
сколько попыток угадано число. 

Дополнительно **: В статистике учитывать - сколько времени заняло угадывание.
Загаданное программой число должно быть случайным, т.е. выбираться случайным образом.
```

```
10. Создайте программу, играющую с пользователем в орла и решку. Программа
должна спрашивать у пользователя: орёл или решка. Если пользователь
вводит 0, то выбирает орла, 1 — решку, любое другое число — конец игры.
Программа должна вести учёт выигрышей и проигрышей и после каждого
раунда сообщать пользователю о состоянии его счёта. Пусть вначале на
счету 3 рубля и ставка в каждом коне 1 рубль. Если денег у пользователя
не осталось — игра прекращается.
Прим.: используйте модуль random для случайного выбора и функцию randint(a, b),
которая возвращает случайное целое число n, a <= n <= b
```