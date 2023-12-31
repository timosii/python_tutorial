# Обзор языков программирования

* **низкоуровневые** языки программирования — ближе к машинному языку, сложнее для человека
* **высокоуровневые** языки программирования — дальше от машинного языка, проще для человека

**Исходный код** — код программы, написанный на языке программирования

Способы превращения исходного кода в машинный:

* **компиляция** — исходная программа транслируется (переводится) один раз при помощи программы: компилятора.
  * Программа запускается и работает уже будучи переведенной в машинный код, засчет этого работает быстрее
  * Процесс компиляции может занимать значительное количество времени
  * Сгенерированный двоичный код зависит от платформы — компилировать программу нужно под каждую платформу отдельно
  * Доступа к исходному коду в скомпилированной программе нет
* **интерпретация** — исходная программы транслируется каждый раз при запуске программы.
  * Пользователю нужен интерпретатор для запуска
  * Исходный код выполняется интерпретатором, а значит не зависит от платформы
  * Есть доступ к исходному коду.

В зависимости от того, каким образом происходит перевод в машинный язык, языки программированрия бывают **компилируемыми**: _C, C++, Erlang, Haskell, Rust, Go_ и **интерпретируемыми**: _PHP, Ruby, Python и JavaScript_

_Дополнительные материалы:_\
[Компиляция и интерпретация кода — в чем разница?](https://ru.hexlet.io/blog/posts/kompilyatsiya-i-interpretatsiya-koda-chto-eto-takoe-i-v-chem-raznitsa)
