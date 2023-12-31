# Переменные\*

* Переменная — ссылка на объект в памяти. Можно представлять её как бирку — она связывается с объектом и обладает именем. А сам объект содержит значение и тип данных.
* Имя переменной не должно совпадать с _ключевыми словами_:

```python
import keyword
print(keyword.kwlist)
# ['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await',
# 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except',
# 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is',
# 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try',
# 'while', 'with', 'yield']
```

* Рекомендации (согласно стандарту PEP8):
  * имена переменных должны состоять из символов нижнего регистра
  * слова должны разделяться символом подчеркивания
  * имена переменных не могут начинаться с цифр
  * имена переменных не могут переопределять _встроенные имена (built-ins)_:

```python
dir(__builtins__) # список всех встроенных имен
# встроенные имена - это имена функций, классов и переменных,
# которые Python загружает автоматически
# встроенные имена технически можно использовать в качестве имени
# для переменной (ошибки не будет), но это не рекомендуется
```
