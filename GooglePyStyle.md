<!--
AUTHORS:
Prefer only GitHub-flavored Markdown in external text.
See README.md for details.
-->

# Google Python Style Guide

<!-- markdown="1" is required for GitHub Pages to render the TOC properly. -->

<details markdown="1">
  <summary>Оглавление</summary>

-   [1 Описание](#s1-background)
-   [2 Правила языка Python](#s2-python-language-rules)
    *   [2.1 Lint](#s2.1-lint)
    *   [2.2 Импорты (Imports)](#s2.2-imports)
    *   [2.3 Пакеты (Packages)](#s2.3-packages)
    *   [2.4 Исключения (Exceptions)](#s2.4-exceptions)
    *   [2.5 Глобальные переменные (Global variables)](#s2.5-global-variables)
    *   [2.6 Nested/Local/Inner Classes and Functions](#s2.6-nested)
    *   [2.7 Comprehensions & Generator Expressions](#s2.7-comprehensions)
    *   [2.8 Default Iterators and Operators](#s2.8-default-iterators-and-operators)
    *   [2.9 Генераторы (Generators)](#s2.9-generators)
    *   [2.10 Лямбда-функции (Lambda Functions)](#s2.10-lambda-functions)
    *   [2.11 Условные выражения (Conditional Expressions)](#s2.11-conditional-expressions)
    *   [2.12 Значения аргумента по умолчанию](#s2.12-default-argument-values)
    *   [2.13 Свойства (Properties)](#s2.13-properties)
    *   [2.14 True/False Проверок (оценок)](#s2.14-truefalse-evaluations)
    *   [2.16 Lexical Scoping](#s2.16-lexical-scoping)
    *   [2.17 Декораторы функций и методов](#s2.17-function-and-method-decorators)
    *   [2.18 Многопоточность](#s2.18-threading)
    *   [2.19 Характеристики мощности](#s2.19-power-features)
    *   [2.20 Современный  Python: from \_\_future\_\_ imports](#s2.20-modern-python)
    *   [2.21 Тип Аннотированный код](#s2.21-type-annotated-code)
-   [3 Правила стиля Python](#s3-python-style-rules)
    *   [3.1 Точка с запятой](#s3.1-semicolons)
    *   [3.2 Длины строк](#s3.2-line-length)
    *   [3.3 Скобки](#s3.3-parentheses)
    *   [3.4 Отступы](#s3.4-indentation)
        +   [3.4.1 Trailing commas in sequences of items?](#s3.4.1-trailing-commas)
    *   [3.5 Пустые строки](#s3.5-blank-lines)
    *   [3.6 Разделение пробелом](#s3.6-whitespace)
    *   [3.7 Shebang Line](#s3.7-shebang-line)
    *   [3.8 Комментарии и строки документов](#s3.8-comments-and-docstrings)
        +   [3.8.1 Docstrings](#s3.8.1-comments-in-doc-strings)
        +   [3.8.2 Модули (Modules)](#s3.8.2-comments-in-modules)
        +   [3.8.3 Функции и методы](#s3.8.3-functions-and-methods)
        +   [3.8.4 Классы (Classes)](#s3.8.4-comments-in-classes)
        +   [3.8.5 Блоки и входящие комментарии (Block and Inline Comments)](#s3.8.5-block-and-inline-comments)
        +   [3.8.6 Пунктуация, орфография и грамматика (Punctuation, Spelling, and Grammar)](#s3.8.6-punctuation-spelling-and-grammar)
    *   [3.10 Строки](#s3.10-strings)
        +   [3.10.1 Журналирование, логирование (Logging)](#s3.10.1-logging)
        +   [3.10.2 Сообщения об ошибки](#s3.10.2-error-messages)
    *   [3.11 Files, Sockets, and similar Stateful Resources](#s3.11-files-sockets-closeables)
    *   [3.12 TODO Comments](#s3.12-todo-comments)
    *   [3.13 Imports formatting](#s3.13-imports-formatting)
    *   [3.14 Statements](#s3.14-statements)
    *   [3.15 Accessors](#s3.15-accessors)
    *   [3.16 Название (Naming)](#s3.16-naming)
        +   [3.16.1 Имена, которых следует избегать (Names to Avoid)](#s3.16.1-names-to-avoid)
        +   [3.16.2 Соглашения об именовании (Naming Conventions)](#s3.16.2-naming-conventions)
        +   [3.16.3 Имя файла (File Naming)](#s3.16.3-file-naming)
        +   [3.16.4 Guidelines derived from Guido's Recommendations](#s3.16.4-guidelines-derived-from-guidos-recommendations)
    *   [3.17 Main](#s3.17-main)
    *   [3.18 Длина функции (Function length)](#s3.18-function-length)
    *   [3.19 Аннотации к типу (Type Annotations)](#s3.19-type-annotations)
        +   [3.19.1 Общие правила (General Rules)](#s3.19.1-general-rules)
        +   [3.19.2 Разрыв линии (Line Breaking)](#s3.19.2-line-breaking)
        +   [3.19.3 Forward Declarations](#s3.19.3-forward-declarations)
        +   [3.19.4 Значения по умолчанию (Default Values)](#s3.19.4-default-values)
        +   [3.19.5 NoneType](#s3.19.5-nonetype)
        +   [3.19.6 Type Aliases](#s3.19.6-type-aliases)
        +   [3.19.7 Ignoring Types](#s3.19.7-ignoring-types)
        +   [3.19.8 Typing Variables](#s3.19.8-typing-variables)
        +   [3.19.9 Кортеж vs список (Tuples vs Lists)](#s3.19.9-tuples-vs-lists)
        +   [3.19.10 TypeVars](#s3.19.10-typevars)
        +   [3.19.11 Строковые типы (String types)](#s3.19.11-string-types)
        +   [3.19.12 Imports For Typing](#s3.19.12-imports-for-typing)
        +   [3.19.13 Условный импорт (Conditional Imports)](#s3.19.13-conditional-imports)
        +   [3.19.14 Циклические зависимости (Circular Dependencies)](#s3.19.14-circular-dependencies)
        +   [3.19.15 Generics](#s3.19.15-generics)
        +   [3.19.16 Build Dependencies](#s3.19.16-build-dependencies)
-   [4 Parting Words](#4-parting-words)

</details>

<a id="s1-background"></a>
<a id="1-background"></a>

<a id="background"></a>
## 1 Описание 

Python является основным динамическим языком в Google. 
Этот список руководств по стилю (*что можно, а что нельзя делать*) 
для написания кода (программ) на Python.

Чтобы помочь Вам правильно отформатировать код, мы создали [settings file for Vim](google_python_style.vim). For Emacs, the default settings should be fine.

Мнигие команды искользуют [yapf](https://github.com/google/yapf/) авто-форматирование, чтобы не спорить о нем.

<a id="s2-python-language-rules"></a>
<a id="2-python-language-rules"></a>

<a id="python-language-rules"></a>
## 2 Правила языка Python 

<a id="s2.1-lint"></a>
<a id="21-lint"></a>

<a id="lint"></a>
### 2.1 Lint 

Запуск `pylint` на Вашем коде используется этот [pylintrc](https://google.github.io/styleguide/pylintrc).

<a id="s2.1.1-definition"></a>
<a id="211-definition"></a>

<a id="lint-definition"></a>
#### 2.1.1 Определения (описание) 

`pylint`
это инструмент для поиска ошибок (bugs) и проблем стилей в коде Python.
Он находит проблемы, которые ловяться (находятся) компилятором для не динмаических языков как C и C++. 
Из-за динамической природы Python, некоторые предупреждения могут быть неверными;
Тем не менее, ложные предупреждения должны быть нечастыми.

<a id="s2.1.2-pros"></a>
<a id="212-pros"></a>

<a id="lint-pros"></a>
#### 2.1.2 Плюсы 

Легко обнаруживает ошибки, такие как опечатки, using-vars-before-assignment, и т.д.

<a id="s2.1.3-cons"></a>
<a id="213-cons"></a>

<a id="lint-cons"></a>
#### 2.1.3 Минусы 

`pylint`
не идеален. Чтобы воспользоваться этим, иногда нам нужно написать об этом,... 
подавить его предупреждения или исправить.

<a id="s2.1.4-decision"></a>
<a id="214-decision"></a>

<a id="lint-decision"></a>
#### 2.1.4 Решение 

Убедитесь, что Вы используете 
`pylint`
в Вашем коде.


Подавлять предупреждения, если они неуместны, с тем чтобы не скрывать другие.
Для подавления предупреждений вы можете задать line-level коментарий:

```python
dict = 'something awful'  # (Плохая идея) Bad Idea... pylint: disable=redefined-builtin
```

`pylint`
предупреждения идентифицируются по (названию) имени (`empty-docstring`)
Специальные предупреждения Google начинаются с `g-`.

Если причина подавления не ясна из имени, добавьте объяснение.

Подавление таким образом имеет то преимущество, 
что мы можем легко искать подавления и пересматривать их.

Вы можете получать лист
`pylint`
предупреждений слудеющим путем:

```shell
pylint --list-msgs
```

Чтобы получить больше информации о конкретном сообщении, используйте:

```shell
pylint --help-msg=C6409
```

Предпочитаете `pylint: disable` устаревшую форму `pylint: disable-msg`.

Предупреждение о неиспользованном аргументе может быть удалено путём удаления переменных в начале функции. 
Всегда включите комментарий, поясняющий, почему вы его удаляете. 
"Неиспользованный" достаточно. 
Например:

```python
def viking_cafe_order(spam: str, beans: str, eggs: Optional[str] = None) -> str:
    del beans, eggs  # Unused by vikings.(неиспользуется в vikings)
    return spam + spam + spam
```

Другие распространенные формы подавления этого предупреждения включают использование '`_`'
в качестве идентификатора неиспользуемого аргумента или префикса имени аргумента
'`unused_`', или присвоение им '`_`'. Эти формы разрешены, но больше не рекомендуются.
Эти break callers, которые передают аргументы по имени и не настаивают на том,
что аргументы фактически не используются.

<a id="s2.2-imports"></a>
<a id="22-imports"></a>

<a id="imports"></a>
### 2.2 (Импорты) Imports 

Использовать инструкции `import` для пакетов (packages) и модулей (modules), 
а не для отдельных классов (classes) или функций (functions).
Импорт из [typing module](#typing-imports),
[typing_extensions module](https://github.com/python/typing/tree/master/typing_extensions),
и
[six.moves module](https://six.readthedocs.io/#module-six.moves)
освобождены от этого правила.

<a id="s2.2.1-definition"></a>
<a id="221-definition"></a>

<a id="imports-definition"></a>
#### 2.2.1 Определение 

Механизм многократного использования для обмена кодами из одного модуля в другой.

<a id="s2.2.2-pros"></a>
<a id="222-pros"></a>

<a id="imports-pros"></a>
#### 2.2.2 Плюсы 

Простаое упраление пространством имен. 
Источник каждого идентификатора указывается последовательным образом; 
`x.Obj` говорит что объект `Obj` определяется в модуле `x`.

<a id="s2.2.3-cons"></a>
<a id="223-cons"></a>

<a id="imports-cons"></a>
#### 2.2.3 Минусы 

Имена молулей могут сталкиваться (конфликтовать, вступать в противоречия).
Некоторые имена модулей слишком длинные, это может вызвать неудобства.

<a id="s2.2.4-decision"></a>
<a id="224-decision"></a>

<a id="imports-decision"></a>
#### 2.2.4 Решение 

*   Используйте `import x` для импорта пакетов и модулей.
*   Используйте `from x import y` где `x` это пакет (package) и `y` имя модулья.
*   Используйте `from x import y as z` если два модуля с именем `y`  или если модуль
    `y` имеет слишком длинное название (неудобное).
*   Исмользуйте `import y as z` только тогда когда `z` является стандартной аббревиатурой (напрмимер `np` для
    `numpy`).

Например, модуль `sound.effects.echo` может быть импортирован следующим образом:

```python
from sound.effects import echo
...
echo.EchoFilter(input, output, delay=0.7, atten=4)
```

Не использовать относительные имена при импорте. 
Даже если модуль находится в том же пакете, используйте полное имя пакета. 
Это помогает предотвратить непреднамеренный импорт пакта (package) дважды.

<a id="s2.3-packages"></a>
<a id="23-packages"></a>

<a id="packages"></a>
### 2.3 Пакеты (Packages) 

Импортировать каждый модуль, используйте полное имя пути модуля.

<a id="s2.3.1-pros"></a>
<a id="231-pros"></a>

<a id="packages-pros"></a>
#### 2.3.1 Плюсы 

Избегает конфликтов в именах модулей или неправильного импорта из-за того,
что путь поиска модуля не соответствует ожиданиям автора.
Это облегчает поиск модулей.

<a id="s2.3.2-cons"></a>
<a id="232-cons"></a>

<a id="packages-cons"></a>
#### 2.3.2 Минусы 

(Makes it harder to deploy code because you have to replicate the package
hierarchy. Not really a problem with modern deployment mechanisms.)
Усложняет установку кода, так как вам нужно воспроизвести иерархию пакетов. 
Не проблема с современными механизмами развертывания.

<a id="s2.3.3-decision"></a>
<a id="233-decision"></a>

<a id="packages-decision"></a>
#### 2.3.3 Решение 

Все новые коды должны импортировать каждый модуль по его полному имени пакета.

Импорт должен быть следующим:

```python
Yes:
  # Reference absl.flags in code with the complete name (verbose). (Ссылки absl.flags в коде с полным именем (verbose).)
  import absl.flags
  from doctor.who import jodie

  FLAGS = absl.flags.FLAGS
```

```python
Yes:
  # Reference flags in code with just the module name (common).(Ссылки флаги в коде только с именем модуля (общий))
  from absl import flags
  from doctor.who import jodie

  FLAGS = flags.FLAGS
```

_(предположим, что этот файл находится в `doctor/who/` где `jodie.py` также существует)_

```python
No:
  # Неясно, какой модуль хотел автор и что будет импортировано. Фактически.  
  # Реальное поведение импорта зависит от внешних факторов, контролирующих sys.path.
  # Какой возможный модуль джоди намеревался импортировать автор?
  import jodie
```

Каталог, в котором расположена основная двоичная папка, не следует рассматривать как каталог,
находящийся в файловой `sys.path`, несмотря на то, что это происходит в некоторых средах.
В этом случае код должен предполагать, что `import jodie` относится к третьей стороне или 
пакету верхнего уровня с именем `jodie`, а не к локальному `jodie.py`.


<a id="s2.4-exceptions"></a>
<a id="24-exceptions"></a>

<a id="exceptions"></a>
### 2.4 Исключения 

Исключения допускаются, но должны применяться осторожно.

<a id="s2.4.1-definition"></a>
<a id="241-definition"></a>

<a id="exceptions-definition"></a>
#### 2.4.1 Определение 

Исключения являются средством выхода из нормального потока управления 
для обработки ошибок или других исключительных условий.

<a id="s2.4.2-pros"></a>
<a id="242-pros"></a>

<a id="exceptions-pros"></a>
#### 2.4.2 Плюсы 

Управляющий поток обычного операционного кода не загроможден кодом обработки ошибок. 
Это также позволяет управляющему потоку пропускать несколько кадров, 
когда происходит определенное условие, например, возвращение из вложенных функций N в один шаг вместо того, 
чтобы пропускать коды ошибок.

<a id="s2.4.3-cons"></a>
<a id="243-cons"></a>

<a id="exceptions-cons"></a>
#### 2.4.3 Минусы 

Может вызвать путаницу в потоке управления. 
При вызове библиотеки легко пропустить случаи ошибок.

<a id="s2.4.4-decision"></a>
<a id="244-decision"></a>

<a id="exceptions-decision"></a>
#### 2.4.4 Решение 

Исключения должны осуществляться при соблюдении определенных условий:

-  Используйте встроенные классы исключений, когда это имеет смысл. 
   Например,  поднимите значение `ValueError`,  чтобы указать на ошибку программирования, 
   подобную нарушенному предварительному условию 
   (например, если вы получили отрицательное число, но требовали положительное). 
   Не используйте `assert` утверждения для проверки значений аргументов публичного API.
   `assert` используется для обеспечения внутренней корректности,
   а не для обеспечения правильного использования или указания на какое-либо неожиданное событие.
   Если в последнем случае желательно сделать исключение, 
   используйте заявление о поднятии вопроса.
   Например:
    
    ```python
    Yes:
      def connect_to_next_port(self, minimum: int) -> int:
        """Connects to the next available port.

        Args:
          minimum: A port value greater or equal to 1024.

        Returns:
          The new minimum port.

        Raises:
          ConnectionError: If no available port is found.
        """
        if minimum < 1024:
          # Note that this raising of ValueError is not mentioned in the doc
          # string's "Raises:" section because it is not appropriate to
          # guarantee this specific behavioral reaction to API misuse.
          raise ValueError(f'Min. port must be at least 1024, not {minimum}.')
        port = self._find_next_open_port(minimum)
        if not port:
          raise ConnectionError(
              f'Could not connect to service on port {minimum} or higher.')
        assert port >= minimum, (
            f'Unexpected port {port} when minimum was {minimum}.')
        return port
    ```

    ```python
    No:
      def connect_to_next_port(self, minimum: int) -> int:
        """Connects to the next available port.

        Args:
          minimum: A port value greater or equal to 1024.

        Returns:
          The new minimum port.
        """
        assert minimum >= 1024, 'Minimum port must be at least 1024.'
        port = self._find_next_open_port(minimum)
        assert port is not None
        return port
    ```
-   Библиотеки или пакеты могут определять свои собственные исключения. 
    При этом они должны наследовать от существующего класса исключений. 
    Имена исключений должны заканчиваться на `Error` и не должны вводить повторение
    (`foo.FooError`).

-   Никогда не используйте обработку всех типов (catch-all) `except:` заявление или уловка `Exception` или
    `StandardError`, за исключением

    -   повторное выдвижение исключения или
    -   создание изолированной точки в программе, где исключения не распространяются, 
        а регистрируются и подавляются вместо этого, например, 
        защита потока от падения путем охраны его самого внешнего блока..
    
    Python является очень терпимым в этом отношении и `except:` действительно уловит все,
    включая имена с ошибками, sys.exit() вызовы, прерывания Ctrl+C, 
    unittest сбои (failures) и все виды исключений, которые вы просто не хотите ловить.

-   Минимизация количества кода в блоке `try`/`except`. 
    Чем больше тело `try`, тем больше вероятность того, 
    что исключение будет поднято строкой кода, который вы не ожидали создать исключение.
    В этих случаях блок `try`/`except` скрывает реальную ошибку.

-   Для выполнения кода используйте `finally` независимо от того, сделано ли исключение в блоке `try`. 
    Это часто полезно для очистки, то есть закрытия файла.


<a id="s2.5-global-variables"></a>
<a id="25-global-variables"></a>

<a id="global-variables"></a>
### 2.5 Глобальные переменные (Global variables) 

Избегайте глобальных переменных.

<a id="s2.5.1-definition"></a>
<a id="251-definition"></a>

<a id="global-variables-definition"></a>
#### 2.5.1 Определение 

Переменные, объявленные на уровне модуля или в качестве атрибутов класса.

<a id="s2.5.2-pros"></a>
<a id="252-pros"></a>

<a id="global-variables-pros"></a>
#### 2.5.2 Плюсы 

Иногда полезно.

<a id="s2.5.3-cons"></a>
<a id="253-cons"></a>

<a id="global-variables-cons"></a>
#### 2.5.3 Минусы 

Имеет возможность изменить поведение модуля во время импорта, 
потому что назначения глобальным переменным производятся при первом импорте модуля.

<a id="s2.5.4-decision"></a>
<a id="254-decision"></a>

<a id="global-variables-decision"></a>
#### 2.5.4 Решение 

Избегать глобальных переменных.

Хотя технически они являются переменными, допускаются и поощряются константы уровня модуля. 
Например: `_MAX_HOLY_HANDGRENADE_COUNT = 3`. 
Константы должны называться с использованием все заглавных букв с подчеркиванием.
Смотреть (Название) [Naming](#s3.16-naming) ниже.

В случае необходимости глобальные переменные должны быть объявлены на уровне модулей и 
введены в модуль путем добавления "_" к названию.
Внешний доступ должен осуществляться через публичные функции уровня модуля.
Смотерть (Название) [Naming](#s3.16-naming) ниже.

<a id="s2.6-nested"></a>
<a id="26-nested"></a>

<a id="nested-classes-functions"></a>
### 2.6 Вложенные/локальные/внутренние классы и функции (Nested/Local/Inner Classes and Functions)

Вложенные локальные функции или классы хороши, когда используются для закрытия локальной переменной. 
Внутренние классы хороши.

<a id="s2.6.1-definition"></a>
<a id="261-definition"></a>

<a id="nested-classes-functions-definition"></a>
#### 2.6.1 Определение 

Класс может быть определен внутри метода, функции или класса.
Функция может быть определена внутри метода или функции.
Вложенные функции имеют доступ только для чтения к переменным, 
определенным в вложенных областях.

<a id="s2.6.2-pros"></a>
<a id="262-pros"></a>

<a id="nested-classes-functions-pros"></a>
#### 2.6.2 Плюсы

Позволяет определить классы и функции полезности, которые используются только в очень ограниченном масштабе. 
Очень
[ADT](http://www.google.com/url?sa=D&q=http://en.wikipedia.org/wiki/Abstract_data_type)-y.
Обычно используется для декораторов.

<a id="s2.6.3-cons"></a>
<a id="263-cons"></a>

<a id="nested-classes-functions-cons"></a>
#### 2.6.3 Минусы 

Вложенные функции и классы не могут быть проверены напрямую.
Вложение может сделать внешнюю функцию длиннее и менее читаемой.

<a id="s2.6.4-decision"></a>
<a id="264-decision"></a>

<a id="nested-classes-functions-decision"></a>
#### 2.6.4 Решение 

Они хороши с некоторыми оговорками.
Избегайте вложенных функций или классов, за исключением тех случаев, 
когда они закрываются над локальным значением, отличным `self` или `cls`.
Не вкладывайте функцию, чтобы скрыть ее от пользователей модуля.
Вместо этого, префикс его имени с `_` на уровне модуля, чтобы его можно было получить с помощью тестов.


<a id="s2.7-comprehensions"></a>
<a id="s2.7-list_comprehensions"></a>
<a id="27-list_comprehensions"></a>
<a id="list_comprehensions"></a>
<a id="list-comprehensions"></a>

<a id="comprehensions"></a>
### 2.7 Понимание и генераторные выражения (Comprehensions & Generator Expressions) 

Можно использовать для простых случаев.

<a id="s2.7.1-definition"></a>
<a id="271-definition"></a>

<a id="comprehensions-definition"></a>
#### 2.7.1 Определение 

Понимание List, Dict и Set, а также выражения генераторов обеспечивают сжатый и эффективный
способ создания типов контейнеров и итераторов без использования 
традиционных циклов, `map()`, `filter()`, или `lambda`.

<a id="s2.7.2-pros"></a>
<a id="272-pros"></a>

<a id="comprehensions-pros"></a>
#### 2.7.2 Плюсы 

Простое понимание может быть более ясным и простым, чем другие методы создания диктов, списков или множеств. 
Генераторные выражения могут быть очень эффективными, поскольку они избегают создания списка полностью.

<a id="s2.7.3-cons"></a>
<a id="273-cons"></a>

<a id="comprehensions-cons"></a>
#### 2.7.3 Минусы 

Сложные понимания или генераторные выражения могут быть трудно читаемы.

<a id="s2.7.4-decision"></a>
<a id="274-decision"></a>

<a id="comprehensions-decision"></a>
#### 2.7.4 Решение 

Можно использовать для простых случаев. 
Каждая часть должна соответствовать одной строке: 
выражение отображения, условие `for`, выражение фильтра. 
Множественные `for` условия или выражения фильтров не допускаются.
Вместо этого используйте циклов, когда все становится более сложным.

```python
Yes:
  result = [mapping_expr for value in iterable if filter_expr]

  result = [{'key': value} for value in iterable
            if a_long_filter_expression(value)]

  result = [complicated_transform(x)
            for x in iterable if predicate(x)]

  descriptive_name = [
      transform({'key': key, 'value': value}, color='black')
      for key, value in generate_iterable(some_input)
      if complicated_condition_is_met(key, value)
  ]

  result = []
  for x in range(10):
      for y in range(5):
          if x * y > 10:
              result.append((x, y))

  return {x: complicated_transform(x)
          for x in long_generator_function(parameter)
          if x is not None}

  squares_generator = (x**2 for x in range(10))

  unique_names = {user.name for user in users if user is not None}

  eat(jelly_bean for jelly_bean in jelly_beans
      if jelly_bean.color == 'black')
```

```python
No:
  result = [complicated_transform(
                x, some_argument=x+1)
            for x in iterable if predicate(x)]

  result = [(x, y) for x in range(10) for y in range(5) if x * y > 10]

  return ((x, y, z)
          for x in range(5)
          for y in range(5)
          if x != y
          for z in range(5)
          if y != z)
```

<a id="s2.8-default-iterators-and-operators"></a>

<a id="default-iterators-operators"></a>
### 2.8 Итераторы и операторы по умолчанию

Используйте стандартные итераторы и операторы для типов, поддерживающих их,
таких как списки, словари и файлы.

<a id="s2.8.1-definition"></a>
<a id="281-definition"></a>

<a id="default-iterators-operators-definition"></a>
#### 2.8.1 Определение 

Типы контейнеров, такие как словари и списки, 
определяют стандартные итераторы и операторов тестирования принадлежности 
("in" и "not in").

<a id="s2.8.2-pros"></a>
<a id="282-pros"></a>

<a id="default-iterators-operators-pros"></a>
#### 2.8.2 Плюсы 

По умолчанию итераторы и операторы просты и эффективны. 
Они выражают операцию напрямую, без дополнительных вызовов метода.
Функция, использующая операторы по умолчанию, является обобщённой.
Она может быть использована для любого типа, поддерживающего операцию.

<a id="s2.8.3-cons"></a>
<a id="283-cons"></a>

<a id="default-iterators-operators-cons"></a>
#### 2.8.3 Минусы 

Вы не можете определить тип объектов, прочитав имена методов 
(например, "has_key()" означает словарь). 
Это также преимущество.

<a id="s2.8.4-decision"></a>
<a id="284-decision"></a>

<a id="default-iterators-operators-decision"></a>
#### 2.8.4 Решение 

Используйте стандартные итераторы и операторы для типов, поддерживающих их, 
таких как списки, словари и файлы. Встроенные типы также определяют методы итератора. 
Эти методы предпочтительнее методов, которые возвращают списки, за исключением того,
что вы не должны (мутировать, изменять) трансформировать контейнер, перебирая его.

```python
Yes:  for key in adict: ...
      if key not in adict: ...
      if obj in alist: ...
      for line in afile: ...
      for k, v in adict.items(): ...
      for k, v in six.iteritems(adict): ...
```

```python
No:   for key in adict.keys(): ...
      if not adict.has_key(key): ...
      for line in afile.readlines(): ...
      for k, v in dict.iteritems(): ...
```

<a id="s2.9-generators"></a>
<a id="29-generators"></a>

<a id="generators"></a>
### 2.9 Генераторы (Generators) 

Используйте генераторы по мере необходимости.

<a id="s2.9.1-definition"></a>
<a id="291-definition"></a>

<a id="generators-definition"></a>
#### 2.9 Определение 

Функция генератора возвращает итератор, который даёт значение при выполнении
инструкции параметризованная. После получения значения состояние выполнения функции
генератора приостанавливается до следующего значения.

<a id="s2.9.2-pros"></a>
<a id="292-pros"></a>

<a id="generators-pros"></a>
#### 2.9.2 Плюсы 

Более простой код, поскольку состояние локальных переменных и поток управления 
сохраняются для каждого вызова. Генератор использует меньше памяти, чем функция,
которая создает целый список значений одновременно.

<a id="s2.9.3-cons"></a>
<a id="293-cons"></a>

<a id="generators-cons"></a>
#### 2.9.3 Минусы 

Ни одного.

<a id="s2.9.4-decision"></a>
<a id="294-decision"></a>

<a id="generators-decision"></a>
#### 2.9.4 Решение 

Хорошо. Используйте "Yields:" вместо "Returns:" в docstring для функций генератора.


<a id="s2.10-lambda-functions"></a>
<a id="210-lambda-functions"></a>

<a id="lambdas"></a>
### 2.10 Лямбда-функции (Lambda Functions) 

Хорошо для одного лайнера. Предпочитаем выражения генератора вместо `map()` или `filter()`
с `lambda`.


<a id="s2.10.1-definition"></a>
<a id="2101-definition"></a>

<a id="lambdas-definition"></a>
#### 2.10.1 Определение 

Lambdas определяет анонимные функции в выражении, в отличие от заявления.

<a id="s2.10.2-pros"></a>
<a id="2102-pros"></a>

<a id="lambdas-pros"></a>
#### 2.10.2 Плюсы 

Удобно.

<a id="s2.10.3-cons"></a>
<a id="2103-cons"></a>

<a id="lambdas-cons"></a>
#### 2.10.3 Минусы 

Труднее прочитать и отладить, чем локальные функции. Отсутствие имен означает, 
что стек следов труднее понять. Выразительность ограничена, 
так как функция может содержать только выражение.

<a id="s2.10.4-decision"></a>
<a id="2104-decision"></a>

<a id="lambdas-decision"></a>
#### 2.10.4 Решение 

Хорошо использовать их для одного лайнера.
Если код внутри лямбда-функции длиннее 60-80 шаров,
вероятно, лучше определить его как обычный
(вложенная функция) [nested function](#lexical-scoping).


Для общих операций, таких как умножение, используйте функции 
из модуля `operator` вместо лямбда-функций.
Например, предпочитаем `operator.mul` для `lambda x, y: x * y`.

<a id="s2.11-conditional-expressions"></a>
<a id="211-conditional-expressions"></a>

<a id="conditional-expressions"></a>
### 2.11 Условные выражения (Conditional Expressions) 

Хорошо для простых случаев.

<a id="s2.11.1-definition"></a>
<a id="2111-definition"></a>

<a id="conditional-expressions-definition"></a>
#### 2.11.1 Определение 

Условные выражения (иногда называемые "тернарным оператором") являются механизмами, 
которые обеспечивают более короткий синтаксис для утверждений.
К примеру: `x = 1 if cond else 2`.

<a id="s2.11.2-pros"></a>
<a id="2112-pros"></a>

<a id="conditional-expressions-pros"></a>
#### 2.11.2 Плюсы 

Короче и удобнее, чем заявление.

<a id="s2.11.3-cons"></a>
<a id="2113-cons"></a>

<a id="conditional-expressions-cons"></a>
#### 2.11.3 Минусы 

Может быть труднее прочитать, чем заявление.
Условие может быть трудно найти, если выражение длинное.

<a id="s2.11.4-decision"></a>
<a id="2114-decision"></a>

<a id="conditional-expressions-decision"></a>
#### 2.11.4 Решение 

Хорошо использовать для простых случаев.
Каждая часть должна соответствовать одной строке: 
истинное выражение, если-выражение, другое-выражение 
(true-expression, if-expression, else-expression).
Используйте полный текст, если ситуация усложняется.

```python
Yes:
    one_line = 'yes' if predicate(value) else 'no'
    slightly_split = ('yes' if predicate(value)
                      else 'no, nein, nyet')
    the_longest_ternary_style_that_can_be_done = (
        'yes, true, affirmative, confirmed, correct'
        if predicate(value)
        else 'no, false, negative, nay')
```

```python
No:
    bad_line_breaking = ('yes' if predicate(value) else
                         'no')
    portion_too_long = ('yes'
                        if some_long_module.some_long_predicate_function(
                            really_long_variable_name)
                        else 'no, false, negative, nay')
```

<a id="s2.12-default-argument-values"></a>
<a id="212-default-argument-values"></a>

<a id="default-arguments"></a>
### 2.12 Значения аргумента по умолчанию (Default Argument Values) 

Хорошо в большинстве случаев.

<a id="s2.12.1-definition"></a>
<a id="2121-definition"></a>

<a id="default-arguments-definition"></a>
#### 2.12.1 Определение 

Значения переменных можно задать в конце списка параметров функции, например, 
`def foo(a, b=0):`. Если `foo` вызывается только с одним аргументом, `b` имеет значение 0.
Если оно вызывается с двумя аргументами, `b` имеет значение второго аргумента.

<a id="s2.12.2-pros"></a>
<a id="2122-pros"></a>

<a id="default-arguments-pros"></a>
#### 2.12.2 Плюсы 

Часто у вас есть функция, которая использует множество значений по умолчанию, 
но в редких случаях вы хотите отменить значения по умолчанию. 
Значения аргументов по умолчанию обеспечивают простой способ сделать это, 
не требуя определения множества функций для редких исключений. 
Поскольку Python не поддерживает перегруженные методы/функции, 
аргументы по умолчанию являются простым способом "фальсификации" ("faking") поведения перегрузки.

<a id="s2.12.3-cons"></a>
<a id="2123-cons"></a>

<a id="default-arguments-cons"></a>
#### 2.12.3 Минусы 

Аргументы по умолчанию оцениваются один раз во время загрузки модуля. 
Это может вызвать проблемы, если аргумент является изменяемым объектом, 
таким как список или словарь. Если функция изменяет объект 
(например, с помощью элемента в список), значение по умолчанию изменяется.

<a id="s2.12.4-decision"></a>
<a id="2124-decision"></a>

<a id="default-arguments-decision"></a>
#### 2.12.4 Определение 

Можно использовать со следующей оговоркой:
Не используйте изменяемые объекты в качестве значений по умолчанию в определении функции 
или метода.

```python
Yes: def foo(a, b=None):
         if b is None:
             b = []
Yes: def foo(a, b: Optional[Sequence] = None):
         if b is None:
             b = []
Yes: def foo(a, b: Sequence = ()):  # Empty tuple OK since tuples are immutable
         ...
```

```python
No:  def foo(a, b=[]):
         ...
No:  def foo(a, b=time.time()):  # The time the module was loaded???
         ...
No:  def foo(a, b=FLAGS.my_thing):  # sys.argv has not yet been parsed...
         ...
No:  def foo(a, b: Mapping = {}):  # Could still get passed to unchecked code
         ...
```

<a id="s2.13-properties"></a>
<a id="213-properties"></a>

<a id="properties"></a>
### 2.13 Свойства (Properties) 

Свойства могут использоваться для контроля получения или установки атрибутов, 
которые требуют тривиального, но не вызывающего удивления вычисления или логики. 
Реализации свойств должны соответствовать общим ожиданиям регулярного доступа к атрибутам:
они дешевы, прямолинейны и не вызывают удивления.

<a id="s2.13.1-definition"></a>
<a id="2131-definition"></a>

<a id="properties-definition"></a>
#### 2.13.1 Определение 

Способ обтекания метода требует получения и установки атрибута в
качестве стандартного доступа к атрибутам,
когда вычисление является легким.

<a id="s2.13.2-pros"></a>
<a id="2132-pros"></a>

<a id="properties-pros"></a>
#### 2.13.2 Плюсы 

Удобочитаемость повышается за счет исключения явных вызовов получения и 
набора методов для доступа к простому атрибуту. Позволяет вычислениям быть ленивыми. 
Рассмотрел способ Pythonic для поддержания интерфейса класса. 
С точки зрения производительности, разрешение обхода свойств требует тривиального
доступа или методов, когда прямой доступ к переменной является разумным. 
Это также позволяет добавлять методы доступа в будущем без разрыва интерфейса.

<a id="s2.13.3-cons"></a>
<a id="2133-cons"></a>

<a id="properties-cons"></a>
#### 2.13.3 Минусы 

Может скрывать побочные эффекты, подобные перегрузке оператора. 
Может вводить в заблуждение подклассы.

<a id="s2.13.4-decision"></a>
<a id="2134-decision"></a>

<a id="properties-decision"></a>
#### 2.13.4 Решение 

Свойства допускаются, но, как и перегрузка оператора, должны использоваться
только в случае необходимости и соответствовать ожиданиям типичного доступа атрибута;
следуйте по [getters and setters](#getters-and-setters) правила в противном случае.

Например, использование свойства для простого получения и установки внутреннего атрибута 
не допускается: не происходит вычисления, так что свойство не требуется
([make it public instead](#getters-and-setters)). Для сравнения, использование свойства 
для контроля доступа к атрибутам, или вычисление *тривиально*
производного значения, разрешено: логика тривиальна, но неудивительна.

Свойства должны быть созданы с помощью `@property` (свойство)
[decorator](#s2.17-function-and-method-decorators). Ручное выполнение 
дескриптора свойств считается а [power feature](#power-features).

Наследование с собственностью может быть неочевидным, если само имущество не отменено. 
Таким образом, необходимо убедиться в том, что методы обеспечения доступа вызывается 
свойством (используя метод [template method design pattern](https://en.wikipedia.org/wiki/Template_method_pattern)).

```python
Yes: import math

     class Square:
         """A square with two properties: a writable area and a read-only perimeter.

         To use:
         >>> sq = Square(3)
         >>> sq.area
         9
         >>> sq.perimeter
         12
         >>> sq.area = 16
         >>> sq.side
         4
         >>> sq.perimeter
         16
         """

         def __init__(self, side: float):
             self.side = side

         @property
         def area(self) -> float:
             """Area of the square."""
             return self._get_area()

         @area.setter
         def area(self, area: float):
             self._set_area(area)

         def _get_area(self) -> float:
             """Indirect accessor to calculate the 'area' property."""
             return self.side ** 2

         def _set_area(self, area: float):
             """Indirect setter to set the 'area' property."""
             self.side = math.sqrt(area)

         @property
         def perimeter(self) -> float:
             return self.side * 4
```

<a id="s2.14-truefalse-evaluations"></a>
<a id="214-truefalse-evaluations"></a>

<a id="truefalse-evaluations"></a>
### 2.14 True/False Evaluations (Оценка) 

Если возможно, используйте "неявное" значение false.

<a id="s2.14.1-definition"></a>
<a id="2141-definition"></a>

<a id="truefalse-evaluations-definition"></a>
#### 2.14.1 Определение 

Python оценивает определённые значения как `False` в логическом контексте. 
Быстрое "эмпирическое правило" означает, что все "пустые" значения считаются ложными,
так что `0, None, {}, ''` все оцениваются как ложные в булевском контексте.

<a id="s2.14.2-pros"></a>
<a id="2142-pros"></a>

<a id="truefalse-evaluations-pros"></a>
#### 2.14.2 Плюсы 

Условия, использующие Python booleans, легче читать и менее подвержены ошибкам. 
В большинстве случаев они также быстрее.

<a id="s2.14.3-cons"></a>
<a id="2143-cons"></a>

<a id="truefalse-evaluations-cons"></a>
#### 2.14.3 Минусы 

Может показаться странным для разработчиков С/С++.

<a id="s2.14.4-decision"></a>
<a id="2144-decision"></a>

<a id="truefalse-evaluations-decision"></a>
#### 2.14.4 Решение 

Если возможно, используйте "неявный" ложный, то есть `if foo:` вместо `if foo =!
[]:`. Есть несколько оговорок, которые вы должны иметь в виду:

-   Всегда используйте `if foo is None:` (or `is not None`), чтобы проверить значение `None`. 
    Например, при тестировании переменной или аргумента по умолчанию, который по умолчанию равен `None`
    было задано какое-либо другое значение. Другое значение может быть значением, 
    которое ложно в логическом контексте!

-   Никогда не сравнивайте булеву переменную с `False` используя `==`. 
    Вместо этого используйте `if not x:`. Если вам нужно отличить `False` от `None`
    то свяжите эти выражения, например, `if not x and x is not None:`.

-   Для последовательностей (строк, списков, кортежей) следует использовать тот факт, 
    что пустые последовательности являются ложными, так что `if seq:` и `if not seq:`
    предпочтительны по сравнению с `if len(seq):` и `if not len(seq):` соответственно.

-   При обращении с целыми числами неявный ложный может быть связан с большим риском,
    чем с выгодой (то есть, случайным обращением с `None` как 0). 
    Можно сравнить значение, известное как целое (и не являющееся результатом `len()`) 
    против целого числа 0.

    ```python
    Yes: if not users:
             print('no users')

         if i % 10 == 0:
             self.handle_multiple_of_ten()

         def f(x=None):
             if x is None:
                 x = []
    ```

    ```python
    No:  if len(users) == 0:
             print('no users')

         if not i % 10:
             self.handle_multiple_of_ten()

         def f(x=None):
             x = x or []
    ```

-   Обратите внимание, что значение `'0'` (то есть `0` как строка) имеет значение true.


<a id="s2.16-lexical-scoping"></a>
<a id="216-lexical-scoping"></a>

<a id="lexical-scoping"></a>
### 2.16 Lexical Scoping 

Можно использовать.

<a id="s2.16.1-definition"></a>
<a id="2161-definition"></a>

<a id="lexical-scoping-definition"></a>
#### 2.16.1 Определение 

Вложенная функция Python может относиться к переменным, определённым во вложении функций, 
но не может назначать их. Переменные привязки разрешаются с помощью лексического анализа, 
то есть на основе статического текста программы. Любое назначение имени в блоке заставит Python
рассматривать все ссылки на это имя как локальную переменную, даже если использование предшествует
назначению. Если происходит глобальное объявление, имя рассматривается как глобальная переменная.

Примером использования этой функции является:

```python
def get_adder(summand1: float) -> Callable[[float], float]:
    """Returns a function that adds numbers to a given number."""
    def adder(summand2: float) -> float:
        return summand1 + summand2

    return adder
```

<a id="s2.16.2-pros"></a>
<a id="2162-pros"></a>

<a id="lexical-scoping-pros"></a>
#### 2.16.2 Плюсы 

Часто приводит к более четкому, более элегантному коду. 
Особенно комфортно для опытных программистов Lisp и Scheme (и Haskell и ML и ...).

<a id="s2.16.3-cons"></a>
<a id="2163-cons"></a>

<a id="lexical-scoping-cons"></a>
#### 2.16.3 Минусы 

Может привести к путанице в ошибках. Например, этот пример основан на
[PEP-0227](http://www.google.com/url?sa=D&q=http://www.python.org/dev/peps/pep-0227/):

```python
i = 4
def foo(x: Iterable[int]):
    def bar():
        print(i, end='')
    # ...
    # A bunch of code here
    # ...
    for i in x:  # Ah, i *is* local to foo, so this is what bar sees
        print(i, end='')
    bar()
```

Таким образом, `foo([1, 2, 3])`, будет напечатано: `1 2 3 3`, а не `1 2 3 4`.

<a id="s2.16.4-decision"></a>
<a id="2164-decision"></a>

<a id="lexical-scoping-decision"></a>
#### 2.16.4 Решение 

Можно использовать.

<a id="s2.17-function-and-method-decorators"></a>
<a id="217-function-and-method-decorators"></a>
<a id="function-and-method-decorators"></a>

<a id="decorators"></a>
### 2.17 Декораторы функций и методов

Используйте декораторы осторожно, когда есть явное преимущество. 
Избегайте `staticmethod` и ограничите использование метода `classmethod`.

<a id="s2.17.1-definition"></a>
<a id="2171-definition"></a>

<a id="decorators-definition"></a>
#### 2.17.1 Определение 

[Decorators for Functions and Methods](https://docs.python.org/3/glossary.html#term-decorator)
(a.k.a "the `@` notation"). One common decorator is `@property`, used for
converting ordinary methods into dynamically computed attributes. However, the
decorator syntax allows for user-defined decorators as well. Specifically, for
some function `my_decorator`, this:

Один общий декоратор - это `@property`, используемое для преобразования обычных методов
в динамически вычисляемые атрибуты. Тем не менее, синтаксис декоратора позволяет также 
использование декораторов, определенных пользователем. В частности, для некоторых функций
`my_decorator`:


```python
class C:
    @my_decorator
    def method(self):
        # method body ...
```

эквивалентно:

```python
class C:
    def method(self):
        # method body ...
    method = my_decorator(method)
```

<a id="s2.17.2-pros"></a>
<a id="2172-pros"></a>

<a id="decorators-pros"></a>
#### 2.17.2 Плюсы 

Элегантно определяет некоторые преобразования для метода; 
преобразование может устранить некоторые повторяющиеся коды,
обеспечить применение инвариантов и т.д.

<a id="s2.17.3-cons"></a>
<a id="2173-cons"></a>

<a id="decorators-cons"></a>
#### 2.17.3 Минусы 

Декораторы могут выполнять произвольные операции на аргументах функции или 
возвращаемых значениях, что приводит к неожиданному скрытому поведению. 
Кроме того, декораторы работают во время импорта. Ошибки в декоративном коде 
практически невозможно восстановить.

<a id="s2.17.4-decision"></a>
<a id="2174-decision"></a>

<a id="decorators-decision"></a>
#### 2.17.4 Решение 

Используйте декораторов осмотрительно, когда есть явное преимущество. 
Декораторы должны следовать тем же руководящим принципам, что и функции. 
Декоративный `pydoc` должен четко указывать, что данная функция является декоратором. 
Напишите модульные тесты для декораторов.

Избегайте внешних зависимостей в самом декораторе (например, не полагайтесь на файлы,
сокеты, соединения баз данных и т. д.), так как они могут быть недоступны,
когда декоратор работает (во время импорта, возможно, из `pydoc` или других инструментов).
Декоратор, вызываемый с допустимыми параметрами, должен (насколько это возможно) 
быть гарантирован во всех случаях.

Декораторы - это особый случай "кода верхнего уровня" - смотрите [main](#s3.17-main)
для дальнейшего обсуждения.

Никогда не используйте `staticmethod` никогда не используйте, если только это не необходимо
для интеграции с API, определённым в существующей библиотеке. Вместо этого напишите функцию 
уровня модуля.

Использовать `classmethod` только при записи именованного конструктора или рутинного задания 
класса, который модифицирует необходимые глобальные состояния, такие как кэш для всего процесса.

<a id="s2.18-threading"></a>
<a id="218-threading"></a>

<a id="threading"></a>
### 2.18 Многопоточность 

Не полагайтесь на атомарность (atomicity) встроенных типов.

В то время как встроенные в Python типы данных, такие как словари, похоже, имеют атомные операции,
есть угловые случаи, где они не атомарны (например, если `__hash__`
или `__eq__` реализуются как методы Python) и на их атомарность не следует полагаться. 
Также не следует полагаться на назначение атомных переменных 
(поскольку это в свою очередь зависит от словарей).

В качестве предпочтительного способа передачи данных между потоками используйте тип данных модуля `Queue`.
В противном случае используйте модуль резьбы и его примитивы блокировки.
Вместо использования замков более низкого уровня предпочтение отдается переменным условиям и `threading.Condition`.

<a id="s2.19-power-features"></a>
<a id="219-power-features"></a>

<a id="power-features"></a>
### 2.19 Характеристики мощности

Избегать этих особенностей.

<a id="s2.19.1-definition"></a>
<a id="2191-definition"></a>

<a id="power-features-definition"></a>
#### 2.19.1 Определение 

Python - это чрезвычайно гибкий язык и дает вам много модных функций 
такие как пользовательские метаклассы, доступ к байт-коду, компиляция на лету, 
динамическое наследование, переустановка объектов, импорт хаков, отражение 
(например, некоторые виды использования `getattr()`), модификация внутренних элементов системы,
методы `__del__` реализация индивидуальной очистки и т.д.

<a id="s2.19.2-pros"></a>
<a id="2192-pros"></a>

<a id="power-features-pros"></a>
#### 2.19.2 Плюсы 

Это мощные языковые возможности. Они могут сделать ваш код более компактным.

<a id="s2.19.3-cons"></a>
<a id="2193-cons"></a>

<a id="power-features-cons"></a>
#### 2.19.3 Минусы 

Очень заманчиво использовать эти "крутые" черты, когда в них нет абсолютной необходимости. 
Труднее читать, понимать и отлаживать код, в котором используются необычные функции. 
Поначалу это не кажется таким способом (для первоначального автора), но при повторном просмотре кода он, 
как правило, сложнее, чем более длинный, но простой.

<a id="s2.19.4-decision"></a>
<a id="2194-decision"></a>

<a id="power-features-decision"></a>
#### 2.19.4 Решение 

Избегайте этих особенностей в вашем коде.

Стандартные библиотечные модули и классы, которые используют эти функции самостоятельно, 
можно использовать (например, `abc.ABCMeta`, `dataclasses` и `enum`).


<a id="s2.20-modern-python"></a>
<a id="220-modern-python"></a>

<a id="modern-python"></a>
### 2.20 Новый Python: from \_\_future\_\_ imports 

Семантические изменения новой языковой версии могут быть включены за специальным будущим импортом, 
чтобы позволить их на основе каждого файла в более ранних рабочих часах.

<a id="s2.20.1-definition"></a>
<a id="2201-definition"></a>

<a id="modern-python-definition"></a>
#### 2.20.1 Описание 

Возможность включить некоторые из более современных функций через заявления `from __future__ import` 
позволяет использовать функции из ожидаемых будущих версий Python.

<a id="s2.20.2-pros"></a>
<a id="2202-pros"></a>

<a id="modern-python-pros"></a>
#### 2.20.2 Плюсы 

Это доказало, что делает обновление версии во время выполнения более гладким, 
так как изменения могут быть сделаны на основе каждого файла при объявлении совместимости и 
предотвращении регрессии в этих файлах. Современный код лучше поддерживается, 
так как он с меньшей вероятностью будет накапливать технические долги, которые будут 
проблематичными при будущих обновлениях времени выполнения.

<a id="s2.20.3-cons"></a>
<a id="2203-cons"></a>

<a id="modern-python-cons"></a>
#### 2.20.3 Минусы 

Такой код может не сработать на очень старых версиях устного перевода до представления 
необходимого будущего заявления. Необходимость в этом более характерна для проектов,
осуществляемых в самых различных условиях.

<a id="s2.20.4-decision"></a>
<a id="2204-decision"></a>

<a id="modern-python-decision"></a>
#### 2.20.4 Описание 

##### from \_\_future\_\_ imports

Рекомендуется использовать инструкции `from __future__ import`. Это позволяет данному исходному
файлу начать использовать более современные синтаксические возможности Python сегодня. 
После того, как вам больше не нужно запускать версию, где функции скрыты за импортом `__future__`, 
вы можете удалить эти строки.

В коде, который может выполняться на версиях, старых как 3.5, а не >= 3.7, импорт:

```python
from __future__ import generator_stop
```

Для унаследованного кода, на котором лежит бремя продолжения поддержки 2.7, импортируйте:

```python
from __future__ import absolute_import
from __future__ import division
from __future__ import print_function
```

Дополнительную информацию можно получить на веб-сайте по адресу:
[Python future statement definitions](https://docs.python.org/3/library/__future__.html)
документации.

Пожалуйста, не удаляйте эти импортированные данные до тех пор, пока вы не будете уверены, 
что код используется только в достаточно современной среде. Даже если вы в данный момент 
не используете функцию, которую позволяет вам конкретный будущий импорт в вашем коде сегодня,
сохранение его в файле предотвращает последующие изменения кода непреднамеренно в зависимости
от более старого поведения.

Use other `from __future__` import statements as you see fit. We did not include
`unicode_literals` in our recommendations for 2.7 as it was not a clear win due
to implicit default codec conversion consequences it introduced in many places
within 2.7. Most dual-version 2-and-3 code was better off with explicit use of
`b''` and `u''` bytes and unicode string literals where necessary.

Используйте другие импортные инструкции `from __future__`, как считаете нужным.
Мы не включили `unicode_literals` в наши рекомендации для 2.7, поскольку это не была
ясная победа из-за имплицитных последствий кодеков по умолчанию, которые она ввела
во многих местах в 2.7. Большинство двойственных кодов 2-и-3 было лучше при явном 
использовании байтов `b''` и `u''` и строковых символов unicode.


##### Шесть будущих и прошлых библиотек

Когда ваш проект все еще нуждается в поддержке использования в Python 2 и 3, используйте
[six](https://pypi.org/project/six/),
[future](https://pypi.org/project/future/), и
[past](https://pypi.org/project/past/) библиотеки по вашему усмотрению. Они существуют,
чтобы сделать твой код чище и проще.

<a id="s2.21-type-annotated-code"></a>
<a id="s2.21-typed-code"></a>
<a id="221-type-annotated-code"></a>
<a id="typed-code"></a>

<a id="typed-code"></a>
### 2.21 Type Annotated Code 

Вы можете аннотировать код Python 3 с подсказками типа согласно
[PEP-484](https://www.python.org/dev/peps/pep-0484/), и проверить код во время сборки с помощью инструмента проверки типа,
например [pytype](https://github.com/google/pytype).


Аннотации типов могут быть в источнике или в
[stub pyi file](https://www.python.org/dev/peps/pep-0484/#stub-files). По возможности, 
аннотации должны быть в источнике. Используйте файлы pyi для модулей сторонних разработчиков или расширения.


<a id="s2.21.1-definition"></a>
<a id="2211-definition"></a>

<a id="typed-code-definition"></a>
#### 2.21.1 Определение 

Аннотации типа (или "подсказки типа" ("type hints")) 
предназначены для аргументов функции или метода и возвращаемых значений:

```python
def func(a: int) -> List[int]:
```

Можно также указать тип переменной, используя аналогичный 
[PEP-526](https://www.python.org/dev/peps/pep-0526/) синтаксис:

```python
a: SomeType = some_func()
```

Или с помощью комментария типа в коде, который должен поддерживать устаревшие версии Python.

```python
a = some_func()  # type: SomeType
```

<a id="s2.21.2-pros"></a>
<a id="2212-pros"></a>

<a id="typed-code-pros"></a>
#### 2.21.2 Плюсы 

Аннотации типов улучшают удобочитаемость и содержание вашего кода. 
Проверка типа преобразует множество ошибок времени выполнения в 
ошибки времени сборки и уменьшит возможность использования [Power Features](#power-features).

<a id="s2.21.3-cons"></a>
<a id="2213-cons"></a>

<a id="typed-code-cons"></a>
#### 2.21.3 Минусы

Необходимо постоянно обновлять типовые декларации.
Вы можете увидеть ошибки типа, которые, по вашему мнению, являются допустимыми кодами. 
Использование
[type checker](https://github.com/google/pytype)
может уменьшить вашу способность использовать [Power Features](#power-features).

<a id="s2.21.4-decision"></a>
<a id="2214-decision"></a>

<a id="typed-code-decision"></a>
#### 2.21.4 Определение 

При обновлении кода настоятельно рекомендуется включить анализ типа Python. 
При добавлении или изменении общедоступных API, включите аннотации типов и включите проверку
через pytype в системе сборки. Поскольку статический анализ является относительно новым для Python,
мы признаем, что нежелательные побочные эффекты (такие как ошибочно выводимые типы) могут
препятствовать принятию некоторыми проектами. В таких ситуациях авторам рекомендуется добавить
комментарий с TODO или ссылку на ошибку, описывающую проблему(ы),
которая в настоящее время препятствует принятию аннотаций типа в файле BUILD или в самом коде, 
когда это уместно.

<a id="s3-python-style-rules"></a>
<a id="3-python-style-rules"></a>

<a id="python-style-rules"></a>
## 3 Правила стиля Python (Python Style Rules) 

<a id="s3.1-semicolons"></a>
<a id="31-semicolons"></a>

<a id="semicolons"></a>
### 3.1 Точками с запятой (Semicolons) 

Не прерывайте ваши строки с точками с запятой и не используйте точки с запятой, 
чтобы поместить два утверждения на одну строку.

<a id="s3.2-line-length"></a>
<a id="32-line-length"></a>

<a id="line-length"></a>
### 3.2 Длина строки

Максимальная длина линии составляет *80 символов*.

Явные исключения из ограничения в 80 знаков:

-   Длинные отчеты по импорту.
-   URL, имена путей или длинные флаги в комментариях.
-   Длинные строковые константы уровня модуля, не содержащие пробелы, 
    которые не могут быть разделены между строками, такими как URL или имена путей.
    -   Pylint выводит из строя комментарии. (e.g.: `# pylint: disable=invalid-name`)
    

Не используйте продолжение обратной линии, за исключением `with` заявлениями, 
требующими трех или более контекстных менеджеров.

Использовать Python's
[implicit line joining inside parentheses, brackets and braces](http://docs.python.org/reference/lexical_analysis.html#implicit-line-joining).
При необходимости можно добавить дополнительную пару скобок вокруг выражения.

```python
Да: foo_bar(self, width, height, color='black', design=None, x='foo',
             emphasis=None, highlight=0)

     if (width == 0 and height == 0 and
         color == 'red' and emphasis == 'strong'):
```

Когда буквенная строка не умещается на одной строке, используйте скобки для неявного соединения строк.

```python
x = ('This will build a very long long '
     'long long long long long long string')
```

В комментариях разместите длинные URL на своей собственной линии, если необходимо.

```python
Да:  # See details at
      # http://www.example.com/us/developer/documentation/api/content/v2.0/csv_file_name_extension_full_specification.html
```

```python
Нет:  # See details at
     # http://www.example.com/us/developer/documentation/api/content/\
     # v2.0/csv_file_name_extension_full_specification.html
```

При определении выражения `with` с выражением, охватывающим три или более строк, 
допускается продолжение обратной косой линии. Для двух строк выражения используйте вложенную 
`with` инструкцией:


```python
Да:  with very_long_first_expression_function() as spam, \
           very_long_second_expression_function() as beans, \
           third_thing() as eggs:
          place_order(eggs, beans, spam, beans)
```

```python
Нет:  with VeryLongFirstExpressionFunction() as spam, \
          VeryLongSecondExpressionFunction() as beans:
       PlaceOrder(beans, spam)
```

```python
Да:  with very_long_first_expression_function() as spam:
          with very_long_second_expression_function() as beans:
              place_order(beans, spam)
```

Обратите внимание на отступы элементов в повторяющейся строке примеры выше; 
см. [indentation](#s3.4-indentation) раздел для объяснения.

Во всех других случаях, когда строка превышает 80 символов, и
[yapf](https://github.com/google/yapf/)
auto-formatter не помогает перенести строку ниже предельного значения,
строка может превышать это максимальное значение. В тех случаях, когда это целесообразно, 
авторы поощряются к тому, чтобы вручную разорвать эту линию в соответствии с 
приведенными выше примечаниями.

<a id="s3.3-parentheses"></a>
<a id="33-parentheses"></a>

<a id="parentheses"></a>
### 3.3 Скобки 

Используйте скобки экономно.

Можно, хотя и не обязательно, использовать скобки вокруг трусиков. 
Не используйте их в заявлениях о возврате или условных заявлениях,
за исключением использования скобок для подразумеваемого продолжения строки или для указания кортежа.

```python
Да: if foo:
         bar()
     while x:
         x = bar()
     if x and y:
         bar()
     if not x:
         bar()
     # For a 1 item tuple the ()s are more visually obvious than the comma.
     onesie = (foo,)
     return foo
     return spam, beans
     return (spam, beans)
     for (x, y) in dict.items(): ...
```

```python
Нет:  if (x):
         bar()
     if not(x):
         bar()
     return (foo)
```

<a id="s3.4-indentation"></a>
<a id="34-indentation"></a>

<a id="indentation"></a>
### 3.4 Отступы

Отступить блоки кода с *4 пробелами*.

Никогда не используйте вкладки и не смешивайте вкладки и пробелы. 
В случае предполагаемого продолжения строки, вы должны выровнять 
упакованные элементы либо вертикально, как показано в примерах
[line length](#s3.2-line-length) раздел; или использовать откидной отступ в 4 места,
в этом случае после открытой скобки или скобки на первой строке ничего не должно быть.

```python
Да:   # Aligned with opening delimiter
       foo = long_function_name(var_one, var_two,
                                var_three, var_four)
       meal = (spam,
               beans)

       # Aligned with opening delimiter in a dictionary
       foo = {
           'long_dictionary_key': value1 +
                                  value2,
           ...
       }

       # 4-space hanging indent; nothing on first line
       foo = long_function_name(
           var_one, var_two, var_three,
           var_four)
       meal = (
           spam,
           beans)

       # 4-space hanging indent in a dictionary
       foo = {
           'long_dictionary_key':
               long_dictionary_value,
           ...
       }
```

```python
Нет:    # Stuff on first line forbidden
       foo = long_function_name(var_one, var_two,
           var_three, var_four)
       meal = (spam,
           beans)

       # 2-space hanging indent forbidden
       foo = long_function_name(
         var_one, var_two, var_three,
         var_four)

       # No hanging indent in a dictionary
       foo = {
           'long_dictionary_key':
           long_dictionary_value,
           ...
       }
```

<a id="s3.4.1-trailing-comma"></a>
<a id="s3.4.1-trailing-commas"></a>
<a id="s3.4.1-trailing_comma"></a>
<a id="s3.4.1-trailing_commas"></a>
<a id="341-trailing_comma"></a>
<a id="341-trailing_commas"></a>
<a id="trailing_comma"></a>
<a id="trailing_commas"></a>

<a id="trailing-comma"></a>
#### 3.4.1 Следящие запятые в последовательностях?

Замкнутые запятые в последовательностях позиций рекомендуются только в том случае, 
если маркер закрывающего контейнера `]`, `)` или `}` не находится на одной строке с конечным элементом. 
Наличие обратной запятой также используется в качестве подсказки для нашего авто-форматера кода Python 
[YAPF](https://pypi.org/project/yapf/), чтобы перенаправить его на автоформатирование контейнера
в одну строку при наличии `,` после окончательного элемента.


```python
Да:   golomb3 = [0, 1, 3]
Да:   golomb4 = [
           0,
           1,
           4,
           6,
       ]
```

```python
Нет:    golomb4 = [
           0,
           1,
           4,
           6
       ]
```

<a id="s3.5-blank-lines"></a>
<a id="35-blank-lines"></a>

<a id="blank-lines"></a>
### 3.5 Пустые строки 

Две пустые строки между определениями верхнего уровня, будь то функциональные или классовые определения.
Одна незаполненная строка между определениями метода и между строкой `class` и первой строкой. 
После строки `def` пустота отсутствует. 
Используйте одиночные пустые строки, как вы считаете нужным в функциях или методах.

Незаполненные строки не обязательно привязывать к определению. Например, комментарии, 
непосредственно предшествующие определению функции, класса и метода, могут иметь смысл. 
Подумайте, может ли ваш комментарий быть более полезным в качестве части документальной строки.

<a id="s3.6-whitespace"></a>
<a id="36-whitespace"></a>

<a id="whitespace"></a>
### 3.6 Пробелы

Следуйте стандартным типографическим правилам использования пространств вокруг пунктуации.

Нет пробела внутри скобок, скобок или скобок.

```python
Да: spam(ham[1], {'eggs': 2}, [])
```

```python
Нет:  spam( ham[ 1 ], { 'eggs': 2 }, [ ] )
```

Нет пробела перед запятой, точкой с запятой или двоеточием.
Используйте пробел после запятой, запятой или двоеточия, кроме как в конце линии.

```python
Да: if x == 4:
         print(x, y)
     x, y = y, x
```

```python
Нет:  if x == 4 :
         print(x , y)
     x , y = y , x
```

Нет пробела перед открытым пареном/скобкой, 
в которой начинается список аргументов, индексация или разрезание.

```python
Да: spam(1)
```

```python
Нет:  spam (1)
```

```python
Да: dict['key'] = list[index]
```

```python
Нет:  dict ['key'] = list [index]
```

Ни следа за пробелом.

Surround binary operators with a single space on either side for assignment
(`=`), comparisons (`==, <, >, !=, <>, <=, >=, in, not in, is, is not`), and
Booleans (`and, or, not`). Use your better judgment for the insertion of spaces
around arithmetic operators (`+`, `-`, `*`, `/`, `//`, `%`, `**`, `@`).

```python
Да: x == 1
```

```python
Нет:  x<1
```

Never use spaces around `=` when passing keyword arguments or defining a default
parameter value, with one exception:
[when a type annotation is present](#typing-default-values), _do_ use spaces
around the `=` for the default parameter value.

```python
Да: def complex(real, imag=0.0): return Magic(r=real, i=imag)
Да: def complex(real, imag: float = 0.0): return Magic(r=real, i=imag)
```

```python
Нет:  def complex(real, imag = 0.0): return Magic(r = real, i = imag)
Нет:  def complex(real, imag: float=0.0): return Magic(r = real, i = imag)
```

Don't use spaces to vertically align tokens on consecutive lines, since it
becomes a maintenance burden (applies to `:`, `#`, `=`, etc.):

```python
Да:
  foo = 1000  # comment
  long_name = 2  # comment that should not be aligned

  dictionary = {
      'foo': 1,
      'long_name': 2,
  }
```

```python
Нет:
  foo       = 1000  # comment
  long_name = 2     # comment that should not be aligned

  dictionary = {
      'foo'      : 1,
      'long_name': 2,
  }
```


<a id="Python_Interpreter"></a>
<a id="s3.7-shebang-line"></a>
<a id="37-shebang-line"></a>

<a id="shebang-line"></a>
### 3.7 Shebang Line 

Most `.py` files do not need to start with a `#!` line. Start the main file of a
program with
`#!/usr/bin/env python3` (to support virtualenvs) or `#!/usr/bin/python3` per
[PEP-394](https://www.python.org/dev/peps/pep-0394/).

This line is used by the kernel to find the Python interpreter, but is ignored by Python when importing modules. It is only necessary on a file intended to be executed directly.

<a id="s3.8-comments-and-docstrings"></a>
<a id="s3.8-comments"></a>
<a id="38-comments-and-docstrings"></a>

<a id="documentation"></a>
### 3.8 Comments and Docstrings 

Обязательно используйте правильный стиль для модуля, функции, документооборота метода и внутренних комментариев.

<a id="s3.8.1-comments-in-doc-strings"></a>
<a id="381-docstrings"></a>
<a id="comments-in-doc-strings"></a>

<a id="docstrings"></a>
#### 3.8.1 Docstrings 

Python uses _docstrings_ to document code. A docstring is a string that is the
first statement in a package, module, class or function. These strings can be
extracted automatically through the `__doc__` member of the object and are used
by `pydoc`.
(Try running `pydoc` on your module to see how it looks.) Always use the three
double-quote `"""` format for docstrings (per
[PEP 257](https://www.google.com/url?sa=D&q=http://www.python.org/dev/peps/pep-0257/)).
Документальная строка должна быть организована как суммарная строка (одна физическая строка, 
не превышающая 80 символов), оканчивающаяся точкой, вопросительным знаком или восклицательным 
знаком. При записи больше (рекомендуется), за ней должна следовать пустая строка, 
за которой следует остальная строка, начинающаяся с той же позиции курсора, что и первая
кавычка первой строки. Ниже приводятся дополнительные руководящие принципы форматирования 
для документарных строк.

<a id="s3.8.2-comments-in-modules"></a>
<a id="382-modules"></a>
<a id="comments-in-modules"></a>

<a id="module-docs"></a>
#### 3.8.2 Модули 

Каждый файл должен содержать лицензионные шаблоны. Выберите соответствующий шаблон для лицензии, используемой проектом 
(например, Apache 2.0, BSD, LGPL, GPL)

Файлы должны начинаться с документарной строки, описывающей содержимое и использование модуля.

```python
"""A one line summary of the module or program, terminated by a period.

Leave one blank line.  The rest of this docstring should contain an
overall description of the module or program.  Optionally, it may also
contain a brief description of exported classes and functions and/or usage
examples.

  Typical usage example:

  foo = ClassFoo()
  bar = foo.FunctionBar()
"""
```


<a id="s3.8.3-functions-and-methods"></a>
<a id="383-functions-and-methods"></a>
<a id="functions-and-methods"></a>

<a id="function-docs"></a>
#### 3.8.3 Функции и Методы

В настоящем разделе "функция" означает метод, функцию или генератор.

Функция должна иметь документарную строку, если она не удовлетворяет всем следующим критериям:

-   не видимый снаружи
-   очень короткие
-   очевидные

Документальная строка должна давать достаточно информации для записи вызова функции 
без чтения кода функции. Документальная строка должна описывать вызывающий синтаксис 
функции и её семантику, но, как правило, не детали её реализации, если только эти 
детали не относятся к тому, как эта функция будет использоваться. Например, функция,
которая изменяет один из аргументов в качестве побочного эффекта, должна отметить это
в своей документарной строке. В противном случае, тонкие, но важные детали реализации функции,
которые не имеют отношения к звонящему, лучше выразить как комментарии наряду с кодом, 
чем в документарной строке функции.

The docstring should be descriptive-style (`"""Fetches rows from a
Bigtable."""`) rather than imperative-style (`"""Fetch rows from a
Bigtable."""`). The docstring for a `@property` data descriptor should use the
same style as the docstring for an attribute or a
<a href="#doc-function-args">function argument</a> (`"""The Bigtable path."""`,
rather than `"""Returns the Bigtable path."""`).

Метод, который преобразует метод из базового класса, может иметь простую документальную строку, 
отсылающую читателя в докструну метода, например, `"""See base
class."""` Смысл в том, что нет необходимости повторять во многих местах документацию,
которая уже присутствует в документарной строке базового метода. Однако, если поведение 
преобладающего метода существенно отличается от метода переопределения, или необходимо
предоставить детали (например, документирование дополнительных побочных эффектов),
требуется документация, по крайней мере, с этими различиями в методе.

Некоторые аспекты той или иной функции должны быть отражены в специальных разделах, перечисленных ниже.
Каждая секция начинается с линии, которая заканчивается двоеточием. Все разделы, кроме заголовка, 
должны иметь указатель, состоящий из двух или четырех пробелов (быть последовательными в файле). 
Эти разделы могут быть опущены в случаях, когда имя и подпись функции достаточно информативны, 
чтобы её можно было описать с помощью однолинейной документарной строки.

<a id="doc-function-args"></a>
[*Args:*](#doc-function-args)
:   List each parameter by name. A description should follow the name, and be
    separated by a colon followed by either a space or newline. If the
    description is too long to fit on a single 80-character line, use a hanging
    indent of 2 or 4 spaces more than the parameter name (be consistent with the
    rest of the docstrings in the file). The description should include required
    type(s) if the code does not contain a corresponding type annotation. If a
    function accepts `*foo` (variable length argument lists) and/or `**bar`
    (arbitrary keyword arguments), they should be listed as `*foo` and `**bar`.

<a id="doc-function-returns"></a>
[*Returns:* (or *Yields:* for generators)](#doc-function-returns)
:   Describe the type and semantics of the return value. If the function only
    returns None, this section is not required. It may also be omitted if the
    docstring starts with Returns or Yields (e.g. `"""Returns row from Bigtable
    as a tuple of strings."""`) and the opening sentence is sufficient to
    describe the return value. Do not imitate 'NumPy style'
    ([example](http://numpy.org/doc/stable/reference/generated/numpy.linalg.qr.html)),
    which frequently documents a tuple return value as if it were multiple
    return values with individual names (never mentioning the tuple). Instead,
    describe such a return value as: "Returns a tuple (mat_a, mat_b), where
    mat_a is ..., and ...". The auxiliary names in the docstring need not
    necessarily correspond to any internal names used in the function body (as
    those are not part of the API).

<a id="doc-function-raises"></a>
[*Raises:*](#doc-function-raises)
:   List all exceptions that are relevant to the interface followed by a
    description. Use a similar exception name + colon + space or newline and
    hanging indent style as described in *Args:*. You should not document
    exceptions that get raised if the API specified in the docstring is violated
    (because this would paradoxically make behavior under violation of the API
    part of the API).

```python
def fetch_smalltable_rows(table_handle: smalltable.Table,
                          keys: Sequence[Union[bytes, str]],
                          require_all_keys: bool = False,
) -> Mapping[bytes, Tuple[str]]:
    """Fetches rows from a Smalltable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by table_handle.  String keys will be UTF-8 encoded.

    Args:
        table_handle: An open smalltable.Table instance.
        keys: A sequence of strings representing the key of each table
          row to fetch.  String keys will be UTF-8 encoded.
        require_all_keys: If True only rows with values set for all keys will be
          returned.

    Returns:
        A dict mapping keys to the corresponding table row data
        fetched. Each row is represented as a tuple of strings. For
        example:

        {b'Serak': ('Rigel VII', 'Preparer'),
         b'Zim': ('Irk', 'Invader'),
         b'Lrrr': ('Omicron Persei 8', 'Emperor')}

        Returned keys are always bytes.  If a key from the keys argument is
        missing from the dictionary, then that row was not found in the
        table (and require_all_keys must have been False).

    Raises:
        IOError: An error occurred accessing the smalltable.
    """
```

Аналогичным образом, допускается также такое отклонение от значения `Args:` с разрывом линии:

```python
def fetch_smalltable_rows(table_handle: smalltable.Table,
                          keys: Sequence[Union[bytes, str]],
                          require_all_keys: bool = False,
) -> Mapping[bytes, Tuple[str]]:
    """Fetches rows from a Smalltable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by table_handle.  String keys will be UTF-8 encoded.

    Args:
      table_handle:
        An open smalltable.Table instance.
      keys:
        A sequence of strings representing the key of each table row to
        fetch.  String keys will be UTF-8 encoded.
      require_all_keys:
        If True only rows with values set for all keys will be returned.

    Returns:
      A dict mapping keys to the corresponding table row data
      fetched. Each row is represented as a tuple of strings. For
      example:

      {b'Serak': ('Rigel VII', 'Preparer'),
       b'Zim': ('Irk', 'Invader'),
       b'Lrrr': ('Omicron Persei 8', 'Emperor')}

      Returned keys are always bytes.  If a key from the keys argument is
      missing from the dictionary, then that row was not found in the
      table (and require_all_keys must have been False).

    Raises:
      IOError: An error occurred accessing the smalltable.
    """
```

<a id="s3.8.4-comments-in-classes"></a>
<a id="384-classes"></a>
<a id="comments-in-classes"></a>

<a id="class-docs"></a>
#### 3.8.4 Классы 

Классы должны иметь документальную строку ниже определения класса, описывающего класс.
Если ваш класс имеет публичные атрибуты, они должны быть задокументированы здесь в
`Attributes` и следовать тому же формату, что и
[function's `Args`](#doc-function-args) сечение.

```python
class SampleClass:
    """Summary of class here.

    Longer class information....
    Longer class information....

    Attributes:
        likes_spam: A boolean indicating if we like SPAM or not.
        eggs: An integer count of the eggs we have laid.
    """

    def __init__(self, likes_spam: bool = False):
        """Inits SampleClass with blah."""
        self.likes_spam = likes_spam
        self.eggs = 0

    def public_method(self):
        """Performs operation blah."""
```

<a id="s3.8.5-block-and-inline-comments"></a>
<a id="comments-in-block-and-inline"></a>
<a id="s3.8.5-comments-in-block-and-inline"></a>
<a id="385-block-and-inline-comments"></a>

<a id="comments"></a>
#### 3.8.5 Block and Inline Comments (Блоки и входящие комментарии)

The final place to have comments is in tricky parts of the code. If you're going
to have to explain it at the next [code review](http://en.wikipedia.org/wiki/Code_review),
you should comment it now. Complicated operations get a few lines of comments
before the operations commence. Non-obvious ones get comments at the end of the
line.

```python
# We use a weighted dictionary search to find out where i is in
# the array.  We extrapolate position based on the largest num
# in the array and the array size and then do binary search to
# get the exact number.

if i & (i-1) == 0:  # True if i is 0 or a power of 2.
```

Для улучшения разборчивости, эти комментарии должны начинаться по меньшей мере 
на 2 пробела от кода с символом комментария `#`, за которым должно следовать 
по крайней мере одно пространство перед текстом самого комментария.

On the other hand, never describe the code. Assume the person reading the code
knows Python (though not what you're trying to do) better than you do.

```python
# ПЛОХОЙ КОММЕНТАРИЙ: Теперь пройдитесь по массиву Ь и убедитесь, что когда я появлюсь
# следующим элементом is i+1
```

<!-- The next section is copied from the C++ style guide. -->

<a id="s3.8.6-punctuation-spelling-and-grammar"></a>
<a id="386-punctuation-spelling-and-grammar"></a>
<a id="spelling"></a>
<a id="punctuation"></a>
<a id="grammar"></a>

<a id="punctuation-spelling-grammar"></a>
#### 3.8.6 Пунктуация, орфография и грамматика

Обратите внимание на пунктуацию, правописание и грамматику;
легче читать хорошо написанные комментарии, чем плохо написанные.

Комментарии должны быть такими же читаемыми, как и описательный текст, 
с надлежащей капитализацией и пунктуацией. Во многих случаях полные предложения 
удобочитаемы больше, чем фрагменты предложений. Более короткие комментарии, 
такие как комментарии в конце строки кода, иногда могут быть менее формальными, 
но вы должны соответствовать своему стилю.

Хотя это может быть досадно, когда рецензент кода указывает, 
что вы используете запятую, когда вы должны использовать точку с запятой, 
очень важно, чтобы исходный код поддерживал высокий уровень четкости и читаемости. 
Правильная пунктуация, орфография и грамматика помогают в достижении этой цели.

<a id="s3.10-strings"></a>
<a id="310-strings"></a>

<a id="strings"></a>
### 3.10 Strings 

Use an
[f-string](https://docs.python.org/3/reference/lexical_analysis.html#f-strings),
the `%` operator, or the `format` method for formatting strings, even when the
parameters are all strings. Use your best judgment to decide between `+` and `%`
(or `format`) though. Do not use `%` or the `format` method for pure
concatenation.

```python
Yes: x = a + b
     x = '%s, %s!' % (imperative, expletive)
     x = '{}, {}'.format(first, second)
     x = 'name: %s; score: %d' % (name, n)
     x = 'name: {}; score: {}'.format(name, n)
     x = f'name: {name}; score: {n}'
```

```python
No: x = '%s%s' % (a, b)  # use + in this case
    x = '{}{}'.format(a, b)  # use + in this case
    x = first + ', ' + second
    x = 'name: ' + name + '; score: ' + str(n)
```

Avoid using the `+` and `+=` operators to accumulate a string within a loop. In
some conditions, accumulating a string with addition can lead to quadratic
rather than linear running time. Although common accumulations of this sort may
be optimized on CPython, that is an implementation detail. The conditions under
which an optimization applies are not easy to predict and may change. Instead,
add each substring to a list and `''.join` the list after the loop terminates,
or write each substring to an `io.StringIO` buffer. These techniques
consistently have amortized-linear run time complexity.

```python
Yes: items = ['<table>']
     for last_name, first_name in employee_list:
         items.append('<tr><td>%s, %s</td></tr>' % (last_name, first_name))
     items.append('</table>')
     employee_table = ''.join(items)
```

```python
No: employee_table = '<table>'
    for last_name, first_name in employee_list:
        employee_table += '<tr><td>%s, %s</td></tr>' % (last_name, first_name)
    employee_table += '</table>'
```

Be consistent with your choice of string quote character within a file. Pick `'`
or `"` and stick with it. It is okay to use the other quote character on a
string to avoid the need to backslash-escape quote characters within the string.

```python
Yes:
  Python('Why are you hiding your eyes?')
  Gollum("I'm scared of lint errors.")
  Narrator('"Good!" thought a happy Python reviewer.')
```

```python
No:
  Python("Why are you hiding your eyes?")
  Gollum('The lint. It burns. It burns us.')
  Gollum("Always the great lint. Watching. Watching.")
```

Prefer `"""` for multi-line strings rather than `'''`. Projects may choose to
use `'''` for all non-docstring multi-line strings if and only if they also use
`'` for regular strings. Docstrings must use `"""` regardless.

Multi-line strings do not flow with the indentation of the rest of the program.
If you need to avoid embedding extra space in the string, use either
concatenated single-line strings or a multi-line string with
[`textwrap.dedent()`](https://docs.python.org/3/library/textwrap.html#textwrap.dedent)
to remove the initial space on each line:

```python
  No:
  long_string = """Это довольно некрасиво.
Не делайте так.
"""
```

```python
  Yes:
  long_string = """Это нормально, если ваш вариант использования может 
      принимать внешние ведущие пространства."""
```

```python
  Yes:
  long_string = ("И это нормально, если ты не можешь принять\n" +
                 "внешние ведущие пространства.")
```

```python
  Yes:
  long_string = ("И это тоже хорошо, если ты не можешь принять\n"
                 "внешние ведущие пространства.")
```

```python
  Yes:
  import textwrap

  long_string = textwrap.dedent("""\
      This is also fine, because textwrap.dedent()
      will collapse common leading spaces in each line.""")
```

<a id="s3.10.1-logging"></a>
<a id="3101-logging"></a>
<a id="logging"></a>

<a id="logging"></a>
#### 3.10.1 Logging 

For logging functions that expect a pattern-string (with %-placeholders) as
their first argument: Always call them with a string literal (not an f-string!)
as their first argument with pattern-parameters as subsequent arguments. Some
logging implementations collect the unexpanded pattern-string as a queryable
field. It also prevents spending time rendering a message that no logger is
configured to output.

```python
  Yes:
  import tensorflow as tf
  logger = tf.get_logger()
  logger.info('TensorFlow Version is: %s', tf.__version__)
```

```python
  Yes:
  import os
  from absl import logging

  logging.info('Current $PAGER is: %s', os.getenv('PAGER', default=''))

  homedir = os.getenv('HOME')
  if homedir is None or not os.access(homedir, os.W_OK):
    logging.error('Cannot write to home directory, $HOME=%r', homedir)
```

```python
  No:
  import os
  from absl import logging

  logging.info('Current $PAGER is:')
  logging.info(os.getenv('PAGER', default=''))

  homedir = os.getenv('HOME')
  if homedir is None or not os.access(homedir, os.W_OK):
    logging.error(f'Cannot write to home directory, $HOME={homedir!r}')
```

<a id="s3.10.2-error-messages"></a>
<a id="3102-error-messages"></a>
<a id="error-messages"></a>

<a id="error-messages"></a>
#### 3.10.2 Error Messages 

Error messages (such as: message strings on exceptions like `ValueError`, or
messages shown to the user) should follow three guidelines:

1.  The message needs to precisely match the actual error condition.

2.  Interpolated pieces need to always be clearly identifiable as such.

3.  They should allow simple automated processing (e.g. grepping).

```python
  Yes:
  if not 0 <= p <= 1:
    raise ValueError(f'Маловероятно: {p!r}')

  try:
    os.rmdir(workdir)
  except OSError as error:
    logging.warning('Не удалось удалить каталог (причина: %r): %r',
                    error, workdir)
```

```python
  No:
  if p < 0 or p > 1:  # PROBLEM: also false for float('nan')!
    raise ValueError(f'Not a probability: {p!r}')

  try:
    os.rmdir(workdir)
  except OSError:
    # PROBLEM: Message makes an assumption that might not be true:
    # Deletion might have failed for some other reason, misleading
    # whoever has to debug this.
    logging.warning('Directory already was deleted: %s', workdir)

  try:
    os.rmdir(workdir)
  except OSError:
    # PROBLEM: The message is harder to grep for than necessary, and
    # not universally non-confusing for all possible values of `workdir`.
    # Imagine someone calling a library function with such code
    # using a name such as workdir = 'deleted'. The warning would read:
    # "The deleted directory could not be deleted."
    logging.warning('The %s directory could not be deleted.', workdir)
```

<a id="s3.11-files-sockets-closeables"></a>
<a id="s3.11-files-and-sockets"></a>
<a id="311-files-and-sockets"></a>
<a id="files-and-sockets"></a>

<a id="files"></a>
### 3.11 Files, Sockets, and similar Stateful Resources 

Explicitly close files and sockets when done with them. This rule naturally
extends to closeable resources that internally use sockets, such as database
connections, and also other resources that need to be closed down in a similar
fashion. To name only a few examples, this also includes
[mmap](https://docs.python.org/3/library/mmap.html) mappings,
[h5py File objects](https://docs.h5py.org/en/stable/high/file.html), and
[matplotlib.pyplot figure windows](https://matplotlib.org/2.1.0/api/_as_gen/matplotlib.pyplot.close.html).

Leaving files, sockets or other such stateful objects open unnecessarily has
many downsides:

-   They may consume limited system resources, such as file descriptors. Code
    that deals with many such objects may exhaust those resources unnecessarily
    if they're not returned to the system promptly after use.
-   Holding files open may prevent other actions such as moving or deleting
    them, or unmounting a filesystem.
-   Files and sockets that are shared throughout a program may inadvertently be
    read from or written to after logically being closed. If they are actually
    closed, attempts to read or write from them will raise exceptions, making
    the problem known sooner.

Furthermore, while files and sockets (and some similarly behaving resources) are
automatically closed when the object is destructed, coupling the lifetime of the
object to the state of the resource is poor practice:

-   There are no guarantees as to when the runtime will actually invoke the
    `__del__` method. Different Python implementations use different memory
    management techniques, such as delayed garbage collection, which may
    increase the object's lifetime arbitrarily and indefinitely.
-   Unexpected references to the file, e.g. in globals or exception tracebacks,
    may keep it around longer than intended.

Relying on finalizers to do automatic cleanup that has observable side effects
has been rediscovered over and over again to lead to major problems, across many
decades and multiple languages (see e.g.
[this article](https://wiki.sei.cmu.edu/confluence/display/java/MET12-J.+Do+not+use+finalizers)
for Java).

The preferred way to manage files and similar resources is using the
[`with` statement](http://docs.python.org/reference/compound_stmts.html#the-with-statement):

```python
with open("hello.txt") as hello_file:
    for line in hello_file:
        print(line)
```

For file-like objects that do not support the `with` statement, use
`contextlib.closing()`:

```python
import contextlib

with contextlib.closing(urllib.urlopen("http://www.python.org/")) as front_page:
    for line in front_page:
        print(line)
```

In rare cases where context-based resource management is infeasible, code
documentation must explain clearly how resource lifetime is managed.

<a id="s3.12-todo-comments"></a>
<a id="312-todo-comments"></a>

<a id="todo"></a>
### 3.12 TODO Comments 

Use `TODO` comments for code that is temporary, a short-term solution, or
good-enough but not perfect.

A `TODO` comment begins with the string `TODO` in all caps and a parenthesized
name, e-mail address, or other identifier
of the person or issue with the best context about the problem. This is followed
by an explanation of what there is to do.

The purpose is to have a consistent `TODO` format that can be searched to find
out how to get more details. A `TODO` is not a commitment that the person
referenced will fix the problem. Thus when you create a
`TODO`, it is almost always your name
that is given.

```python
# TODO(kl@gmail.com): Use a "*" here for string repetition.
# TODO(Zeke) Change this to use relations.
```

If your `TODO` is of the form "At a future date do something" make sure that you
either include a very specific date ("Fix by November 2009") or a very specific
event ("Remove this code when all clients can handle XML responses.").

<a id="s3.13-imports-formatting"></a>
<a id="313-imports-formatting"></a>

<a id="imports-formatting"></a>
### 3.13 Imports formatting 

Imports should be on separate lines; there are
[exceptions for `typing` imports](#typing-imports).

E.g.:

```python
Yes: import os
     import sys
     from typing import Mapping, Sequence
```

```python
No:  import os, sys
```


Imports are always put at the top of the file, just after any module comments
and docstrings and before module globals and constants. Imports should be
grouped from most generic to least generic:

1.  Python future import statements. For example:

    ```python
    from __future__ import absolute_import
    from __future__ import division
    from __future__ import print_function
    ```

    See [above](#from-future-imports) for more information about those.

2.  Python standard library imports. For example:

    ```python
    import sys
    ```

3.  [third-party](https://pypi.org/) module
    or package imports. For example:

    
    ```python
    import tensorflow as tf
    ```

4.  Code repository
    sub-package imports. For example:

    
    ```python
    from otherproject.ai import mind
    ```

5.  **Deprecated:** application-specific imports that are part of the same
    top level
    sub-package as this file. For example:

    
    ```python
    from myproject.backend.hgwells import time_machine
    ```

    You may find older Google Python Style code doing this, but it is no longer
    required. **New code is encouraged not to bother with this.** Simply treat
    application-specific sub-package imports the same as other sub-package
    imports.

    
Within each grouping, imports should be sorted lexicographically, ignoring case,
according to each module's full package path (the `path` in `from path import
...`). Code may optionally place a blank line between import sections.

```python
import collections
import queue
import sys

from absl import app
from absl import flags
import bs4
import cryptography
import tensorflow as tf

from book.genres import scifi
from myproject.backend import huxley
from myproject.backend.hgwells import time_machine
from myproject.backend.state_machine import main_loop
from otherproject.ai import body
from otherproject.ai import mind
from otherproject.ai import soul

# Older style code may have these imports down here instead:
#from myproject.backend.hgwells import time_machine
#from myproject.backend.state_machine import main_loop
```


<a id="s3.14-statements"></a>
<a id="314-statements"></a>

<a id="statements"></a>
### 3.14 Statements 

Generally only one statement per line.

However, you may put the result of a test on the same line as the test only if
the entire statement fits on one line. In particular, you can never do so with
`try`/`except` since the `try` and `except` can't both fit on the same line, and
you can only do so with an `if` if there is no `else`.

```python
Да:

  if foo: bar(foo)
```

```python
Нет:

  if foo: bar(foo)
  else:   baz(foo)

  try:               bar(foo)
  except ValueError: baz(foo)

  try:
      bar(foo)
  except ValueError: baz(foo)
```

<a id="s3.15-accessors"></a>
<a id="s3.15-access-control"></a>
<a id="315-access-control"></a>
<a id="access-control"></a>
<a id="accessors"></a>

<a id="getters-and-setters"></a>
### 3.15 Getters and Setters 

Функции Getter и Setter (также называемые аксессуарами и мутаторами) должны использоваться, 
когда они обеспечивают значимую роль или поведение для получения или установки значения переменной.

В частности, они должны использоваться в тех случаях, когда получение или установка переменной 
является сложной задачей или когда затраты являются значительными либо в настоящее время, 
либо в разумном будущем.

If, for example, a pair of getters/setters simply read and write an internal
attribute, the internal attribute should be made public instead. By comparison,
if setting a variable means some state is invalidated or rebuilt, it should be a
setter function. The function invocation hints that a potentially non-trivial
operation is occurring. Alternatively, [properties](#properties) may be an
option when simple logic is needed, or refactoring to no longer need getters and
setters.

Getters and setters should follow the [Naming](#s3.16-naming) guidelines, such
as `get_foo()` and `set_foo()`.

If the past behavior allowed access through a property, do not bind the new
getter/setter functions to the property. Any code still attempting to access the
variable by the old method should break visibly so they are made aware of the
change in complexity.

<a id="s3.16-naming"></a>
<a id="316-naming"></a>

<a id="naming"></a>
### 3.16 Naming 

`module_name`, `package_name`, `ClassName`, `method_name`, `ExceptionName`,
`function_name`, `GLOBAL_CONSTANT_NAME`, `global_var_name`, `instance_var_name`,
`function_parameter_name`, `local_var_name`.


Function names, variable names, and filenames should be descriptive; eschew
abbreviation. In particular, do not use abbreviations that are ambiguous or
unfamiliar to readers outside your project, and do not abbreviate by deleting
letters within a word.

Always use a `.py` filename extension. Never use dashes.

<a id="s3.16.1-names-to-avoid"></a>
<a id="3161-names-to-avoid"></a>

<a id="names-to-avoid"></a>
#### 3.16.1 Names to Avoid 

-   single character names, except for specifically allowed cases:

    -   counters or iterators (e.g. `i`, `j`, `k`, `v`, et al.)
    -   `e` as an exception identifier in `try/except` statements.
    -   `f` as a file handle in `with` statements

    Please be mindful not to abuse single-character naming. Generally speaking,
    descriptiveness should be proportional to the name's scope of visibility.
    For example, `i` might be a fine name for 5-line code block but within
    multiple nested scopes, it is likely too vague.

-   dashes (`-`) in any package/module name

-   `__double_leading_and_trailing_underscore__` names (reserved by Python)

-   offensive terms

-   names that needlessly include the type of the variable (for example:
    `id_to_name_dict`)

<a id="s3.16.2-naming-conventions"></a>
<a id="3162-naming-convention"></a>

<a id="naming-conventions"></a>
#### 3.16.2 Naming Conventions 

-   "Internal" means internal to a module, or protected or private within a
    class.

-   Prepending a single underscore (`_`) has some support for protecting module
    variables and functions (linters will flag protected member access).

-   Prepending a double underscore (`__` aka "dunder") to an instance variable
    or method effectively makes the variable or method private to its class
    (using name mangling); we discourage its use as it impacts readability and
    testability, and isn't *really* private. Prefer a single underscore.

-   Place related classes and top-level functions together in a
    module.
    Unlike Java, there is no need to limit yourself to one class per module.

-   Use CapWords for class names, but lower\_with\_under.py for module names.
    Although there are some old modules named CapWords.py, this is now
    discouraged because it's confusing when the module happens to be named after
    a class. ("wait -- did I write `import StringIO` or `from StringIO import
    StringIO`?")

-   Underscores may appear in *unittest* method names starting with `test` to
    separate logical components of the name, even if those components use
    CapWords. One possible pattern is `test<MethodUnderTest>_<state>`; for
    example `testPop_EmptyStack` is okay. There is no One Correct Way to name
    test methods.

<a id="s3.16.3-file-naming"></a>
<a id="3163-file-naming"></a>

<a id="file-naming"></a>
#### 3.16.3 Имя файла

Python filenames must have a `.py` extension and must not contain dashes (`-`).
This allows them to be imported and unittested. If you want an executable to be
accessible without the extension, use a symbolic link or a simple bash wrapper
containing `exec "$0.py" "$@"`.

<a id="s3.16.4-guidelines-derived-from-guidos-recommendations"></a>
<a id="3164-guidelines-derived-from-guidos-recommendations"></a>

<a id="guidelines-derived-from-guidos-recommendations"></a>
#### 3.16.4 Guidelines derived from [Guido](https://en.wikipedia.org/wiki/Guido_van_Rossum)'s Recommendations 

<table rules="all" border="1" summary="Guidelines from Guido's Recommendations"
       cellspacing="2" cellpadding="2">

  <tr>
    <th>Type</th>
    <th>Public</th>
    <th>Internal</th>
  </tr>

  <tr>
    <td>Packages</td>
    <td><code>lower_with_under</code></td>
    <td></td>
  </tr>

  <tr>
    <td>Modules</td>
    <td><code>lower_with_under</code></td>
    <td><code>_lower_with_under</code></td>
  </tr>

  <tr>
    <td>Classes</td>
    <td><code>CapWords</code></td>
    <td><code>_CapWords</code></td>
  </tr>

  <tr>
    <td>Exceptions</td>
    <td><code>CapWords</code></td>
    <td></td>
  </tr>

  <tr>
    <td>Functions</td>
    <td><code>lower_with_under()</code></td>
    <td><code>_lower_with_under()</code></td>
  </tr>

  <tr>
    <td>Global/Class Constants</td>
    <td><code>CAPS_WITH_UNDER</code></td>
    <td><code>_CAPS_WITH_UNDER</code></td>
  </tr>

  <tr>
    <td>Global/Class Variables</td>
    <td><code>lower_with_under</code></td>
    <td><code>_lower_with_under</code></td>
  </tr>

  <tr>
    <td>Instance Variables</td>
    <td><code>lower_with_under</code></td>
    <td><code>_lower_with_under</code> (protected)</td>
  </tr>

  <tr>
    <td>Method Names</td>
    <td><code>lower_with_under()</code></td>
    <td><code>_lower_with_under()</code> (protected)</td>
  </tr>

  <tr>
    <td>Function/Method Parameters</td>
    <td><code>lower_with_under</code></td>
    <td></td>
  </tr>

  <tr>
    <td>Local Variables</td>
    <td><code>lower_with_under</code></td>
    <td></td>
  </tr>

</table>


<a id="s3.17-main"></a>
<a id="317-main"></a>

<a id="math-notation"></a>
#### 3.16.5 Математическая нотация

For mathematically heavy code, short variable names that would otherwise violate
the style guide are preferred when they match established notation in a
reference paper or algorithm. When doing so, reference the source of all naming
conventions in a comment or docstring or, if the source is not accessible,
clearly document the naming conventions. Prefer PEP8-compliant
`descriptive_names` for public APIs, which are much more likely to be
encountered out of context.

<a id="main"></a>
### 3.17 Main 

In Python, `pydoc` as well as unit tests require modules to be importable. If a
file is meant to be used as an executable, its main functionality should be in a
`main()` function, and your code should always check `if __name__ == '__main__'`
before executing your main program, so that it is not executed when the module
is imported.

When using [absl](https://github.com/abseil/abseil-py), use `app.run`:

```python
from absl import app
...

def main(argv: Sequence[str]):
    # process non-flag arguments
    ...

if __name__ == '__main__':
    app.run(main)
```

В противном случае, использовать:

```python
def main():
    ...

if __name__ == '__main__':
    main()
```

All code at the top level will be executed when the module is imported. Be
careful not to call functions, create objects, or perform other operations that
should not be executed when the file is being `pydoc`ed.

<a id="s3.18-function-length"></a>
<a id="318-function-length"></a>

<a id="function-length"></a>
### 3.18 Длина функции

Предпочитают маленькие и сфокусированные функции.

Мы признаем, что длинные функции иногда уместны, поэтому нет жесткого ограничения на длину функции. 
Если функция превышает около 40 строк, подумайте о том, может ли она быть разрушена без ущерба для 
структуры программы.

Даже если ваша долгая функция работает прекрасно сейчас, кто-то, модифицируя ее через несколько месяцев,
может добавить новое поведение. Это может привести к ошибкам, которые трудно найти.
Простота и краткость ваших функций облегчает другим людям чтение и изменение вашего кода.

При работе с кодом можно найти длинные и сложные функции. Не пугайтесь изменения существующего кода:
если работа с такой функцией оказывается сложной, вы обнаруживаете, что ошибки трудно отладить, 
или вы хотите о использовать часть в нескольких различных контекстах,
рассмотреть разделение функции на более мелкие и более управляемые части.

<a id="s3.19-type-annotations"></a>
<a id="319-type-annotations"></a>

<a id="type-annotations"></a>
### 3.19 Аннотации к типу 

<a id="s3.19.1-general-rules"></a>
<a id="s3.19.1-general"></a>
<a id="3191-general-rules"></a>

<a id="typing-general"></a>
#### 3.19.1 General Rules 

*   Familiarize yourself with
    [PEP-484](https://www.python.org/dev/peps/pep-0484/).
*   In methods, only annotate `self`, or `cls` if it is necessary for proper
    type information. e.g., `@classmethod def create(cls: Type[T]) -> T: return
    cls()`
*   If any other variable or a returned type should not be expressed, use `Any`.
*   You are not required to annotate all the functions in a module.
    -   At least annotate your public APIs.
    -   Use judgment to get to a good balance between safety and clarity on the
        one hand, and flexibility on the other.
    -   Annotate code that is prone to type-related errors (previous bugs or
        complexity).
    -   Annotate code that is hard to understand.
    -   Annotate code as it becomes stable from a types perspective. In many
        cases, you can annotate all the functions in mature code without losing
        too much flexibility.

<a id="s3.19.2-line-breaking"></a>
<a id="3192-line-breaking"></a>

<a id="typing-line-breaking"></a>
#### 3.19.2 Разрыв линии

Try to follow the existing [indentation](#indentation) rules.

После аннотации многие подписи функций станут "одним параметром в строке".

```python
def my_method(self,
              first_var: int,
              second_var: Foo,
              third_var: Optional[Bar]) -> int:
  ...
```

Всегда предпочитаем разбивку между переменными, а не, например, 
между именами переменных и аннотациями типов. Однако, если все сходится на одной линии, вперед.

```python
def my_method(self, first_var: int) -> int:
  ...
```

Если комбинация имени функции, последнего параметра и типа возврата слишком длинная, отступ 4 в новой строке.

```python
def my_method(
    self, first_var: int) -> Tuple[MyLongType1, MyLongType1]:
  ...
```

When the return type does not fit on the same line as the last parameter, the
preferred way is to indent the parameters by 4 on a new line and align the
closing parenthesis with the `def`.

```python
Да:
def my_method(
    self, other_arg: Optional[MyLongType]
) -> Dict[OtherLongType, MyLongType]:
  ...
```

`pylint`
позволяет переместить заключительную скобку в новую строку и выравнять ее с открывающей строкой, 
но это не так удобочитаемо.

```python
Нет:
def my_method(self,
              other_arg: Optional[MyLongType]
             ) -> Dict[OtherLongType, MyLongType]:
  ...
```

Как и в приведенных выше примерах, предпочитают не разбивать типы.
Однако иногда они слишком длинные, чтобы быть на одной строке (старайтесь сохранить подвиды неизменными).

```python
def my_method(
    self,
    first_var: Tuple[List[MyLongType1],
                     List[MyLongType2]],
    second_var: List[Dict[
        MyLongType3, MyLongType4]]) -> None:
  ...
```

If a single name and type is too long, consider using an
[alias](#typing-aliases) for the type. The last resort is to break after the
colon and indent by 4.

```python
Да:
def my_function(
    long_variable_name:
        long_module_name.LongTypeName,
) -> None:
  ...
```

```python
Нет:
def my_function(
    long_variable_name: long_module_name.
        LongTypeName,
) -> None:
  ...
```

<a id="s3.19.3-forward-declarations"></a>
<a id="3193-forward-declarations"></a>

<a id="forward-declarations"></a>
#### 3.19.3 Forward Declarations 

If you need to use a class name from the same module that is not yet defined --
for example, if you need the class inside the class declaration, or if you use a
class that is defined below -- use a string for the class name.

```python
class MyClass:

  def __init__(self,
               stack: List["MyClass"]) -> None:
```

<a id="s3.19.4-default-values"></a>
<a id="3194-default-values"></a>

<a id="typing-default-values"></a>
#### 3.19.4 Значения по умолчанию 

As per
[PEP-008](https://www.python.org/dev/peps/pep-0008/#other-recommendations), use
spaces around the `=` _only_ for arguments that have both a type annotation and
a default value.

```python
Да:
def func(a: int = 0) -> int:
  ...
```

```python
Нет:
def func(a:int=0) -> int:
  ...
```

<a id="s3.19.5-nonetype"></a>
<a id="s3.19.5-none-type"></a>
<a id="3195-nonetype"></a>

<a id="none-type"></a>
#### 3.19.5 NoneType 

In the Python type system, `NoneType` is a "first class" type, and for typing
purposes, `None` is an alias for `NoneType`. If an argument can be `None`, it
has to be declared! You can use `Union`, but if there is only one other type,
use `Optional`.

Use explicit `Optional` instead of implicit `Optional`. Earlier versions of PEP
484 allowed `a: str = None` to be interpreted as `a: Optional[str] = None`, but
that is no longer the preferred behavior.

```python
Да:
def func(a: Optional[str], b: Optional[str] = None) -> str:
  ...
def multiple_nullable_union(a: Union[None, str, int]) -> str:
  ...
```

```python
Нет:
def nullable_union(a: Union[None, str]) -> str:
  ...
def implicit_optional(a: str = None) -> str:
  ...
```

<a id="s3.19.6-type-aliases"></a>
<a id="s3.19.6-aliases"></a>
<a id="3196-type-aliases"></a>
<a id="typing-aliases"></a>

<a id="type-aliases"></a>
#### 3.19.6 Type Aliases (Тип Псевдонимы)  

You can declare aliases of complex types. The name of an alias should be
CapWorded. If the alias is used only in this module, it should be \_Private.

Например, если имя модуля вместе с именем типа является слишком длинным:

```python
_ShortName = module_with_long_name.TypeWithLongName
ComplexMap = Mapping[str, List[Tuple[int, int]]]
```

Другими примерами являются сложные вложенные типы и множественные возвращаемые переменные из функции (как кортеж).

<a id="s3.19.7-ignoring-types"></a>
<a id="s3.19.7-ignore"></a>
<a id="3197-ignoring-types"></a>

<a id="typing-ignore"></a>
#### 3.19.7 Ignoring Types 


Можно отключить проверку типа в строке со специальным комментарием `# type: ignore`.

`pytype` has a disable option for specific errors (similar to lint):

```python
# pytype: disable=attribute-error
```

<a id="s3.19.8-typing-variables"></a>
<a id="s3.19.8-comments"></a>
<a id="3198-typing-internal-variables"></a>

<a id="typing-variables"></a>
#### 3.19.8 Typing Variables 

Если внутренняя переменная имеет тип, который трудно или невозможно вывести, 
можно указать его тип несколькими способами.

<a id="type-comments"></a>
[*Type Comments:*](#type-comments)
:   Use a `# type:` comment on the end of the line

```python
a = SomeUndecoratedFunction()  # type: Foo
```

<a id="annotated-assignments"></a>
[*Annotated Assignments*](#annotated-assignments)
:   Use a colon and type between the variable name and value, as with function
    arguments.

```python
a: Foo = SomeUndecoratedFunction()
```

<a id="s3.19.9-tuples-vs-lists"></a>
<a id="s3.19.9-tuples"></a>
<a id="3199-tuples-vs-lists"></a>

<a id="typing-tuples"></a>
#### 3.19.9 Кортеж vs Список

Напечатанные списки могут содержать только объекты одного типа. 
Типизированные кортежи могут иметь либо один повторяющийся тип,
либо множество элементов с различными типами. Последний обычно 
используется как возвращаемый тип от функции.

```python
a = [1, 2, 3]  # type: List[int]
b = (1, 2, 3)  # type: Tuple[int, ...]
c = (1, "2", 3.5)  # type: Tuple[int, str, float]
```

<a id="s3.19.10-typevars"></a>
<a id="s3.19.10-type-var"></a>
<a id="31910-typevar"></a>
<a id="typing-type-var"></a>

<a id="typevars"></a>
#### 3.19.10 TypeVars 

The Python type system has
[generics](https://www.python.org/dev/peps/pep-0484/#generics). The factory
function `TypeVar` is a common way to use them.

Например:

```python
from typing import List, TypeVar
T = TypeVar("T")
...
def next(l: List[T]) -> T:
  return l.pop()
```

Тип TypeVar может быть ограничен:

```python
AddableType = TypeVar("AddableType", int, float, str)
def add(a: AddableType, b: AddableType) -> AddableType:
  return a + b
```

A common predefined type variable in the `typing` module is `AnyStr`. Use it for
multiple annotations that can be `bytes` or `unicode` and must all be the same
type.

```python
from typing import AnyStr
def check_length(x: AnyStr) -> AnyStr:
  if len(x) <= 42:
    return x
  raise ValueError()
```

<a id="s3.19.11-string-types"></a>
<a id="s3.19.11-strings"></a>
<a id="31911-string-types"></a>

<a id="typing-strings"></a>
#### 3.19.11 Строковые типы

Подходящий тип для аннотации строк зависит от версий Python, для которых предназначен код.

Prefer to use `str`, though `Text` is also acceptable. Be consistent in using
one or the other. For code that deals with binary data, use `bytes`. For Python
2 compatible code that processes text data (`str` or `unicode` in Python 2,
`str` in Python 3), use `Text`.

```python
def deals_with_text_data_in_py3(x: str) -> str:
  ...
def deals_with_binary_data(x: bytes) -> bytes:
  ...
def py2_compatible_text_data_processor(x: Text) -> Text:
  ...
```

In some uncommon Python 2 compatibility cases, `str` may make sense instead of
`Text`, typically to aid compatibility when the return types aren't the same
between Python 2 and Python 3. Never use `unicode` as it doesn't exist in Python
3. The reason this discrepancy exists is because `str` means something different
in Python 2 than in Python 3.

Нет:

```python
def py2_code(x: str) -> unicode:
  ...
```

Если тип может быть байт или текст, используйте `Union` с соответствующим типом текста.

```python
from typing import Text, Union
...
def py3_only(x: Union[bytes, str]) -> Union[bytes, str]:
  ...
def py2_compatible(x: Union[bytes, Text]) -> Union[bytes, Text]:
  ...
```

Если все строковые типы функции всегда одинаковы, например, если тип возврата тот же самый, 
что и тип аргумента в коде выше, используйте [AnyStr](#typing-type-var).

<a id="s3.19.12-imports-for-typing"></a>
<a id="s3.19.12-imports"></a>
<a id="31912-imports-for-typing"></a>

<a id="typing-imports"></a>
#### 3.19.12 Imports For Typing 

For classes from the `typing` module, always import the class itself. You are
explicitly allowed to import multiple specific classes on one line from the
`typing` module. Ex:

```python
from typing import Any, Dict, Optional
```

Given that this way of importing from `typing` adds items to the local
namespace, any names in `typing` should be treated similarly to keywords, and
not be defined in your Python code, typed or not. If there is a collision
between a type and an existing name in a module, import it using `import x as
y`.

```python
from typing import Any as AnyType
```

<a id="s3.19.13-conditional-imports"></a>
<a id="31913-conditional-imports"></a>

<a id="typing-conditional-imports"></a>
#### 3.19.13 Условный импорт

Использовать условный импорт только в исключительных случаях, когда необходимо избегать 
дополнительного импорта, необходимого для проверки типа во время выполнения. 
Такая тенденция не поощряется; следует отдавать предпочтение альтернативным вариантам,
таким, как изменение кода таким образом, чтобы это позволяло импортировать товары высшего уровня.

Imports that are needed only for type annotations can be placed within an `if
TYPE_CHECKING:` block.

-   Conditionally imported types need to be referenced as strings, to be forward
    compatible with Python 3.6 where the annotation expressions are actually
    evaluated.
-   Only entities that are used solely for typing should be defined here; this
    includes aliases. Otherwise it will be a runtime error, as the module will
    not be imported at runtime.
-   The block should be right after all the normal imports.
-   There should be no empty lines in the typing imports list.
-   Sort this list as if it were a regular imports list.
```python
import typing
if typing.TYPE_CHECKING:
  import sketch
def f(x: "sketch.Sketch"): ...
```

<a id="s3.19.14-circular-dependencies"></a>
<a id="s3.19.14-circular-deps"></a>
<a id="31914-circular-dependencies"></a>

<a id="typing-circular-deps"></a>
#### 3.19.14 Циклические зависимости

Циклические зависимости, вызванные печатью, являются запахами кода. 
Такой код является хорошим кандидатом для рефакторинга.
Хотя технически возможно сохранить циклические зависимости,
различные системы сборки не позволят вам сделать это, 
потому что каждый модуль должен зависеть от другого.

Replace modules that create circular dependency imports with `Any`. Set an
[alias](#typing-aliases) with a meaningful name, and use the real type name from
this module (any attribute of Any is Any). Alias definitions should be separated
from the last import by one line.

```python
from typing import Any

some_mod = Any  # some_mod.py imports this module.
...

def my_method(self, var: "some_mod.SomeType") -> None:
  ...
```

<a id="typing-generics"></a>
<a id="s3.19.15-generics"></a>
<a id="31915-generics"></a>

<a id="generics"></a>
#### 3.19.15 Generics (Лекарство)

При аннотации предпочитают указывать параметры типа для общих типов; в противном случае
[the generics' parameters will be assumed to be `Any`](https://www.python.org/dev/peps/pep-0484/#the-any-type).

```python
def get_names(employee_ids: List[int]) -> Dict[int, Any]:
  ...
```

```python
# These are both interpreted as get_names(employee_ids: List[Any]) -> Dict[Any, Any]
def get_names(employee_ids: list) -> Dict:
  ...

def get_names(employee_ids: List) -> Dict:
  ...
```

If the best type parameter for a generic is `Any`, make it explicit, but
remember that in many cases [`TypeVar`](#typing-type-var) might be more
appropriate:

```python
def get_names(employee_ids: List[Any]) -> Dict[Any, str]:
  """Returns a mapping from employee ID to employee name for given IDs."""
```

```python
T = TypeVar('T')
def get_names(employee_ids: List[T]) -> Dict[T, str]:
  """Returns a mapping from employee ID to employee name for given IDs."""
```


<a id="4-parting-words"></a>

<a id="consistency"></a>
## 4 Прощальные слова

*BE CONSISTENT*.

Если вы редактируете код, у вас есть несколько минут, чтобы посмотреть на код вокруг вас и
определить его стиль. Если они используют пространство вокруг всех своих арифметических операторов,
вы тоже должны. Если их комментарии имеют маленькие коробки хеш-меток вокруг них, 
то ваши комментарии имеют маленькие коробки хеш-метки вокруг них тоже.

Смысл руководства стилем в том, чтобы иметь общий словарь кодирования, чтобы люди могли сосредоточиться
на том, что вы говорите, а не на том, как вы это говорите. Мы представляем здесь правила глобального 
стиля, чтобы люди знали словарный запас, но местный стиль также важен. Если код, который вы добавляете
в файл, выглядит радикально отличным от существующего кода вокруг него, это сбивает читателей с ритма,
когда они идут читать его. Избегать этого.