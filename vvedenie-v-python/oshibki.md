# Ошибки

* Ошибки бывают **синтаксические** и **лексические**
* Проверка синтаксиса осуществляется интерпретатором _до выполнения кода_.При отсутствии синтаксических ошибок начинается выполнение кода.
* Ошибки, возникшие _в процессе выполнения кода_ называются **лексическими**.

```python
# синтаксические ошибки
print("Hello)
print("Hello"
```

```python
# логическая ошибка
prit("Hello")
# код запустится - но результатом будет ошибка NameError
```

* Если код _запустился_, т.е. _не возникло синтаксических ошибок_, но в ходе выполнения возникла ошибка --- мы увидим **обратную трассировку**(трейсбек). Это все шаги работы программы от начала до возникновения ошибки.

```python
a = 5
b = 'H'

print(a + b)

# Traceback (most recent call last):
#	 File "main.py", line 5, in <module>
#	 	print(a + b)
# TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

### Практика

```
Запустите код с урока. Проанализируйте ошибки
```