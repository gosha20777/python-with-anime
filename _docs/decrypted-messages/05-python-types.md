# Типы в python

`Декодированое сообщение от L: 05.aes256`

Ура! Если ты читаешь это сообщение - то ты добралась до программирования на Python.

![L](../img/L-2.jpg)

Сейчас начнется магия!

В этом сообщении я подготовил информацию о различных типах которые присутсвуют в Питоне. Понимание этого позволит понимать что происходит и искать и находить баги - ведь 50% багов в пито это ошибки присваивания типов.

## Классическая первая программа

[in]

```python
print('Hello world!')
```
[out]

    Hello world!

- не требуется специфических объявлений точки входа программы (main в C++) - код запускается с первой строки файла/ячейки
- `print` - стандартная функция языка, печатающая аргументы в стандартный поток вывода

## Операторы присваивания

[in]

```python
a = 5
print(a)
```
[out]

    5

[in]

```python
a, b, c = 5, 6, 7
print(a, b, c)
```
[out]

    5 6 7

## Ввод с клавиатуры

[in]

```python
f_name = input('Enter your first name:')
l_name = input('Enter your last name:')
print(f_name, l_name)
```
[out]

    Enter your first name:Murat
    Enter your last name:Apishev
    Murat Apishev

## Выполнение кода на Python в виде строки

[in]

```python
eval('123 + 45')
```
[out]

    168

[in]

```python
exec(
'''
a = 12
b = 3
print(a ** b)
''')
print(a, b)
```
[out]

    1728
    12 3

- `eval` позволяет вычислить выражение и возвращает его результат (чистая функция)
- `exec` позволяет запустить любой фрагмент кода на python (пример: ячейки Jupyter Notebook)

## Объекты и переменные

[in]

```python
4
```
[out]

    4

- создан объект типа `int`, который содержит значение 4
- поскольку на этот объект нет ссылок, он уничтожается после создания и печати

[in]

```python
a = 5
```

- создан объект типа `int`, в котором содержится значение 5
- затем создана переменная с именем `a`, которая ссылается на этот объект

[in]

```python
del a
```

- переменная `a` принудительно удалена
- объект, на который она ссылалась, тоже был удалён, поскольку больше на него нет ссылок

## Объекты и переменные

[in]

```python
a = 5
b = a
```

- создан объект типа `int`, в котором содержится значение 5
- затем создана переменная с именем `a`, которая ссылается на этот объект
- создана переменная `b`, которая указывает на тот же объект типа `int`

[in]

```python
a = a + 1  # equals to a += 1
print(b)
```
[out]

    5

- выражение `a = a + 1` создаёт новый объект типа `int`, равный 6
- переменная `a` начинает ссылаться на него и больше не связана с объектом, равным 5
- `b` продолжает ссылаться на него

## Объекты и переменные в Python

- Переменные $\ne$ объекты
- Объект - это сущность, созданная и используемая в коде
- Объектами являются числа, строки, контейнеры, классы, функции и т.п.
- Переменная - это именованная ссылка на объект
- У одного объекта может быть много ссылок-переменных
- Объекты являются строго типизированными, ссылки - нет

## Основные встроенные типы данных

- _логический, числовые, None_
- _строковые_
- _контейнерные: списки, словари, кортежи, множества_
- _файловый_
- _прочие: функции, классы, модули, сами типы_

Python -

- динамически типизируемый (сам следит за выводом типов)
- язык со строгой типизацией (объект заданного типа допускает только связанные с ним операции)

__Тип объекта можно получить с помощью функции type__

## Логический тип

[in]

```python
True or False
```
[out]

    True

[in]

```python
True or destroy_the_world()
```
[out]

    True

[in]

```python
True and (False or True)
```
[out]

    True

[in]

```python
bool()
```
[out]

    False

[in]

```python
type(True)
```
[out]

    bool

## Целые числа

В Python тип `int` поддерживает бесконечно большие числа

[in]

```python
2 + 5
```
[out]

    7

[in]

```python
4 // 3
```
[out]

    1

[in]

```python
4 % 3
```
[out]

    1

[in]

```python
2 ** 100
```
[out]

    1267650600228229401496703205376

[in]

```python
type(1)
```
[out]

    int

## Литераты типа int

[in]

```python
100, -20, 0  # decimal
```
[out]

    (100, -20, 0)

[in]

```python
0b11, 0B10  # binary
```
[out]

    (3, 2)

[in]

```python
0o11, 0O11  # octal
```
[out]

    (9, 9)

[in]

```python
0x90A, 0X9F # hexadecimal
```
[out]

    (2314, 159)

[in]

```python
bin(1000), oct(1000), hex(1000)
```
[out]

    ('0b1111101000', '0o1750', '0x3e8')

## Побитовые операции

Работаем с целыми числами как с битовыми массивами

[in]

```python
1 << 2  # 001b -> 100b == 4d
```
[out]

    4

[in]

```python
7 >> 1  # 111b -> 011b == 3d
```
[out]

    3

[in]

```python
1 & 2  # 01b || 10b == 00b
```
[out]

    0

[in]

```python
1 | 2  # 01b || 10b == 11b == 3d
```
[out]

    3

## Числа с плавающей точкой

Вещественные числа в Python - это тип `double` из C

[in]

```python
1.0 + 2
```
[out]

    3.0

[in]

```python
4 / 3
```
[out]

    1.3333333333333333

[in]

```python
3 ** 2.5
```
[out]

    15.588457268119896

[in]

```python
type(1.0)
```
[out]

    float

[in]

```python
type(float())
```
[out]

    float

## Литераты числовых типов языка

- Вещественные:

[in]

```python
1.3, 4., 1e+5, 1.0E+54
```
[out]

    (1.3, 4.0, 100000.0, 1e+54)

- Комплексные:

[in]

```python
3+4j, 2.0+1j, 5J
```
[out]

    ((3+4j), (2+1j), 5j)

- Расширение для дробных чисел

[in]

```python
import fractions
a = fractions.Fraction(1, 3 ** 1000000)
len(str(a.denominator))
```
[out]

    477122

## Сравнение чисел

[in]

```python
x, y, z = 1, 2, 3
```

[in]

```python
x < y < z
```
[out]

    True

[in]

```python
x < y >= z
```
[out]

    False

[in]

```python
x < y != z
```
[out]

    True

## Округление вещественных чисел

[in]

```python
11.0 // 3.0  # remove remainder
```
[out]

    3.0

[in]

```python
import math

print(math.trunc(4.7))  # move to zero
print(math.trunc(-4.7))
```
[out]

    4
    -4

[in]

```python
print(math.floor(4.7))  # move to lowest integer
print(math.floor(-4.7))
```
[out]

    4
    -5

[in]

```python
print(round(4.3))  # standart round
print(round(-4.7))
```
[out]

    4
    -5

## Полезные встроенные функции для чисел

[in]

```python
pow(2, 4) == 2 ** 4
```
[out]

    True

[in]

```python
abs(-2)
```
[out]

    2

[in]

```python
sum((1, 2, 3))
```
[out]

    6

[in]

```python
min(1, 2, -7, 44)
```
[out]

    -7

[in]

```python
import math
print(math.sqrt(4))
print(math.sin(8))
```
[out]

    2.0
    0.9893582466233818

### `Тип None`

[in]

```python
None == None
```
[out]

    True

[in]

```python
None or True
```
[out]

    True

[in]

```python
type(None)
```
[out]

    NoneType

[in]

```python
5 * None  # strong typing
```
[out]

    ---------------------------------------------------------------------------
    
    TypeError                                 Traceback (most recent call last)
    
    <ipython-input-40-8d0e337763fe> in <module>
    ----> 1 5 * None
    
    
    TypeError: unsupported operand type(s) for *: 'int' and 'NoneType'

### `Строки`

[in]

```python
s = 'qwerty'
type(s)
```
[out]

    str

[in]

```python
len(s)  # built-in function to get sequence length
```
[out]

    6

[in]

```python
s[0]  # make a copy of element
```
[out]

    'q'

[in]

```python
s[-1]  # make a copy of element
```
[out]

    'y'

[in]

```python
s[0: 3]  # make a copy of elements from 0 to 3 excluding
```
[out]

    'qwe'

[in]

```python
s + '-add-on'
```
[out]

    'qwerty-add-on'

## Подробнее об индексировани и срезах

[in]

```python
s = 'qwerty'
s[0]
```
[out]

    'q'

[in]

```python
s[0: 10]
```
[out]

    'qwerty'

[in]

```python
s[slice(1, 3)]
```
[out]

    'we'

[in]

```python
s[:10:2]  # QwErTy____
```
[out]

    'qet'

[in]

```python
s[::-1]
```
[out]

    'ytrewq'

## Операции над строками

[in]

```python
s + 5  # strong typing
```
[out]

    ---------------------------------------------------------------------------
    
    TypeError                                 Traceback (most recent call last)
    
    <ipython-input-48-bdd2275bd5ba> in <module>
    ----> 1 s + 5
    
    
    TypeError: can only concatenate str (not "int") to str

[in]

```python
s * 5  # strong typing
```
[out]

    'qwertyqwertyqwertyqwertyqwerty'

[in]

```python
s[0] = 'a'  # str type is immutable
```
[out]

    ---------------------------------------------------------------------------
    
    TypeError                                 Traceback (most recent call last)
    
    <ipython-input-59-99e5ad368a97> in <module>
    ----> 1 s[0] = 'a'  # str type is immutable
    
    
    TypeError: 'str' object does not support item assignment

## Операции над строками

[in]

```python
s = 'Qwe{}'.format('rty')
s
```
[out]

    'Qwerty'

[in]

```python
print(s.find('w'), s.find('9'))
```
[out]

    1 -1

[in]

```python
s.split('r')
```
[out]

    ['Qwe', 'ty']

[in]

```python
'-'.join(['New', 'York'])
```
[out]

    'New-York'

[in]

```python
s.replace('ty', 'TY')
```
[out]

    'QwerTY'

[in]

```python
s[0].isupper()
```
[out]

    True

## Как ещё можно задавать строки

[in]

```python
'qwe\'rty'
```
[out]

    "qwe'rty"

[in]

```python
"qwe'rty"
```
[out]

    "qwe'rty"

[in]

```python
'''qwe'rty'''
```
[out]

    "qwe'rty"

[in]

```python
'qwe\0rty'  # print hex code in '\xNN' format for non-printable characters
```
[out]

    'qwe\x00rty'

[in]

```python
'qwe\nrty'
```
[out]

    'qwe\nrty'

[in]

```python
print('qwe\nrty')  # we'll discuss difference between __repr__ and __str__ further
```
[out]

    qwe
    rty

## Форматирование строк

В Python есть похожих способа форматирования - выражение и метод

[in]

```python
'x = %d, y = %f' % (10.5, 11)
```
[out]

    'x = 10, y = 11.000000'

[in]

```python
'x = %o, y = %E' % (8, 1.0 / 3)  # octal format, exponential + upper case
```
[out]

    'x = 10, y = 3.333333E-01'

[in]

```python
'x = %10.2f' % (1.0 / 3)  # min width and precision
```
[out]

    'x =       0.33'

[in]

```python
# add leading zeros if len < min width
s = '''
x = %(value_1)010.2f
x = %(value_2)010.2f
''' % ({'value_1': 10000, 'value_2': 0.12345})

print(s)  # __str__
s         # __repr__
```
[out]

    x = 0010000.00
    x = 0000000.12
    
    
    
    
    
    
    '\nx = 0010000.00\nx = 0000000.12\n'

## Форматирование строк

[in]

```python
'x = {}, y = {}'.format(10, 20)
```
[out]

    'x = 10, y = 20'

[in]

```python
'x = {1}, y = {0}'.format(10, 20)
```
[out]

    'x = 20, y = 10'

[in]

```python
f'x = {10}, y = {20}'
```
[out]

    'x = 10, y = 20'

[in]

```python
'x = {val_1:f}, y = {val_2:010.2f}'.format(val_1=10, val_2=10)
```
[out]

    'x = 10.000000, y = 0000010.00'

[in]

```python
import sys
'platform: {sys_var.platform}'.format(sys_var=sys)
```
[out]

    'platform: linux'

## Строка как набор байтов

[in]

```python
b = bytearray(b'qwerty')
type(b)
```
[out]

    bytearray

[in]

```python
b[1] = ord('a')
b
```
[out]

    bytearray(b'qaerty')

- `bytearray` - массив байтов, в который можно записывать номера 8-битных символов
- в отличие от `str`, объекты этого типа являются изменяемыми
- функция `ord` возвращает по символу его номер в таблице ASCII

## Контейнерные типы: списки

[in]

```python
lst = [1, None, 'qwerty']
list([1, None, 'qwerty']) == lst  # list() gets any iterable object as input
```
[out]

    True

[in]

```python
lst[0] = [10, 20]
lst
```
[out]

    [[10, 20], None, 'qwerty']

- список - более общий аналог массива (не путать со структурой данных "список")
- элементы могут быть произвольного типа (в т.ч. и ссылками)
- сам список является изменяемым типом

## Списки

[in]

```python
len(lst)
```
[out]

    3

[in]

```python
type(lst)
```
[out]

    list

[in]

```python
lst[-1]
```
[out]

    'qwerty'

[in]

```python
lst[: 100]  # slice bounds can be exceed real ones
```
[out]

    [[10, 20], None, 'qwerty']

[in]

```python
lst[5]
```
[out]

    ---------------------------------------------------------------------------
    
    IndexError                                Traceback (most recent call last)
    
    <ipython-input-125-843c5cb805fc> in <module>
    ----> 1 lst[5]
    
    
    IndexError: list index out of range

## Операции над списками

[in]

```python
lst = [1, 2, 3]
lst.append(4)
lst
```
[out]

    [1, 2, 3, 4]

[in]

```python
print(lst.pop(), lst)
```
[out]

    4 [1, 2, 3]

[in]

```python
lst.sort(reverse=True)  # equals to lst.reverse()
lst
```
[out]

    [3, 2, 1]

[in]

```python
lst * 2
```
[out]

    [3, 2, 1, 3, 2, 1]

[in]

```python
lst + list('abc')
```
[out]

    [3, 2, 1, 'a', 'b', 'c']

## Списковые включения и генераторы списков

[in]

```python
[x ** 2 for x in [1, 2, 3]]  # list comprehension
```
[out]

    [1, 4, 9]

[in]

```python
lst = [x ** 2 for x in [1, 2, 3] if x > 1]
print(type(lst))

for _ in [1, 2]:  # _ means value we really don't need
    for e in lst:
        print(e)
```
[out]

    <class 'list'>
    4
    9
    4
    9

[in]

```python
lst = (x ** 2 for x in [1, 2, 3] if x > 1)  # list generator
print(type(lst))

for _ in [1, 2]:
    for e in lst:
        print(e)
```
[out]

    <class 'generator'>
    4
    9

## Снова про объекты и переменные

[in]

```python
a = [2]
b = a
a += [1]
print(b)
```
[out]

    [2, 1]

- список - изменяемый объект, создание новой ссылки не приводит к появлению нового объекта
- есть две переменные, указывающие на один и тот же список

[in]

```python
del a
print(b)
```
[out]

    [2, 1]

- удаление `a` не приводит у удалению списка, поскольку на него ещё ссылается `b`

## Копирование изменяемых объектов

[in]

```python
a = [1, 2, 3]
b = a[:]
b.append(4)
print(a)
```
[out]

    [1, 2, 3]

[in]

```python
a = [1, 2, 3]
b = a.copy()
b.append(4)
print(a)
```
[out]

    [1, 2, 3]

## Копирование вложенных изменяемых объектов

[in]

```python
a = [['a', 'b', 'c'], 2, 3]
b = a.copy()
b[0].append('d')
print(a)
print(b)
```
[out]

    [['a', 'b', 'c', 'd'], 2, 3]
    [['a', 'b', 'c', 'd'], 2, 3]

[in]

```python
import copy

a = [['a', 'b', 'c'], 2, 3]
b = copy.deepcopy(a)
b[0].append('d')
print(a)
print(b)
```
[out]

    [['a', 'b', 'c'], 2, 3]
    [['a', 'b', 'c', 'd'], 2, 3]

## Контейнерные типы: словари

- словарь (`dict`) - это ассоциативный массив (отображение), т.е. набор пар "ключ-значение"
- словарь поддерживает возможность быстро искать значение по ключу
- в Python словари реализованы на основе хэш-таблиц (сложность поиска O(1))
- словари также являются изменяемым типом данных
- значения могут иметь произвольный тип
- ключи - произвольный неизменяемый тип

## Словари

[in]

```python
type(dict()), type({})
```
[out]

    (dict, dict)

[in]

```python
# simple creation of nested structures!
d = {'1': 1, 's': 2, None: [1, {None: True}]}
d
```
[out]

    {'1': 1, 's': 2, None: [1, {None: True}]}

[in]

```python
d['s'] = 'two'
d
```
[out]

    {'1': 1, 's': 'two', None: 5}

[in]

```python
del d['1']  # remove object
print(d)
```
[out]

    {'s': 'two', None: 5}

[in]

```python
d2 = {('s', 3), ('a', 'b')}
```

## Операции над словарями

[in]

```python
d = dict.fromkeys(list('abcccc'))
d
```
[out]

    {'a': None, 'b': None, 'c': None}

[in]

```python
for k in d.keys():  # view object
    d[k] = ord(k)
d
```
[out]

    {'a': 97, 'b': 98, 'c': 99}

[in]

```python
for k, v in d.items():  # view object
    print(k, v)
```
[out]

    a 97
    b 98
    c 99

[in]

```python
D = dict(a=ord('a'), b=ord('b'), c=ord('c'))
d == D
```
[out]

    True

[in]

```python
d.update(d2)
d
```
[out]

    {'s': 3, None: 5, 'a': 'b'}

## Контейнерные типы: кортежи

- очень похожи на списки, но являются неизменяемыми

[in]

```python
type(()), type(tuple())
```
[out]

    (tuple, tuple)

[in]

```python
(1, 2, 'str', 4.0, None)
```
[out]

    (1, 2, 'str', 4.0, None)

[in]

```python
(1, 2) + (3.0, 6, None)
```
[out]

    (1, 2, 3.0, 6, None)

[in]

```python
tpl = tuple([1, 2, 3])
tpl[2]
```
[out]

    3

## Контейнерные типы: множества

- Как и словари, основаны на хэш-таблицах
- Элементы должны быть неизменяемыми

[in]

```python
type(set()), type({1}), type({})  # Empty '{}' is a dict, not a set!
```
[out]

    (set, set, dict)

[in]

```python
{1, 2, 3, 3, 2, 1, 'set', 'a'}
```
[out]

    {1, 2, 3, 'a', 'set'}

[in]

```python
s = {1, 2, 3}
s.add(4)
s
```
[out]

    {1, 2, 3, 4}

[in]

```python
s1, s2 = {1, 2, 3}, set([3, 4, 5])

print('{}\t{}\t{}\t{}'.format(s1 - s2, s1 | s2, s1 & s2, s1 < s2))
```
[out]

    {1, 2}    {1, 2, 3, 4, 5}    {3}    False

## Операции над множествами

[in]

```python
A, B = set('abc'), {'a', 'c', 'd'}
```

[in]

```python
A - B  # minus: in A and not in B (== A.difference(B))
```
[out]

    {'b'}

[in]

```python
A | B  # union: in A or in B (== A.union(B))
```
[out]

    {'a', 'b', 'c', 'd'}

[in]

```python
A & B  # intersection: in A and in B (== A.intersection(B))
```
[out]

    {'a', 'c'}

[in]

```python
A ^ B  # sym diff: (in A and not in B) and via versa (== A.symmetric_difference(B))
```
[out]

    {'b', 'd'}

## Операции над множествами

[in]

```python
A.add('e')
A
```
[out]

    {'a', 'b', 'c', 'e'}

[in]

```python
A.update(B)
A
```
[out]

    {'a', 'b', 'c', 'd', 'e'}

[in]

```python
A.remove('a')
A
```
[out]

    {'b', 'c', 'd', 'e'}

[in]

```python
'a' in A
```
[out]

    False

[in]

```python
{'a', 'b'} < A  # is subset (== {'a', 'b'}.issubset(A))
```
[out]

    True

## Файловый тип

[in]

```python
fin = open('some_file.txt', 'r')  # 'r' can be avoided
print(fin.read())
fin.close()
fin.closed
```
[out]

    hello
    world!
    
    
    
    
    
    
    True

[in]

```python
fin = open('some_file.txt', 'r')  # 'r' can be avoided

# strip removes blank and special characters from edges
lines = [line.strip() for line in fin.readlines()]

print(' '.join(lines))
fin.close()
fin.closed
```
[out]

    hello world!
    
    
    
    
    
    True

## Файловый менеджер контекста

[in]

```python
fin = open('some_file.txt', 'r')  # 'r' can be avoided
print(fin.read(), 0/0)
fin.close()
```
[out]

    ---------------------------------------------------------------------------
    
    ZeroDivisionError                         Traceback (most recent call last)
    
    <ipython-input-177-4fbd946c8ecb> in <module>
          1 fin = open('some_file.txt', 'r')  # 'r' can be avoided
    ----> 2 print(fin.read(), 0/0)
          3 fin.close()
    
    
    ZeroDivisionError: division by zero

[in]

```python
fin.closed
```
[out]

    False

## Файловый менеджер контекста

[in]

```python
with open('some_file.txt', 'r') as fin:
    print(fin.read(), 0/0)
```
[out]

    ---------------------------------------------------------------------------
    
    ZeroDivisionError                         Traceback (most recent call last)
    
    <ipython-input-183-0f73f85c4f29> in <module>
          1 with open('some_file.txt', 'r') as fin:
    ----> 2     print(fin.read(), 0/0)
    
    
    ZeroDivisionError: division by zero

[in]

```python
fin.closed
```
[out]

    True

## Запись в файл

- отступы используются для обозначения операторных блоков (вместо фигурных скобок в C++)

[in]

```python
with open('some_file.txt', 'a') as fout:
    fout.write('additional string')
```

[in]

```python
with open('some_file.txt', 'r') as fin:
    print(fin.read())
```
[out]

    hello
    world!
    additional string

[in]

```python
with open('some_file.txt', 'w') as fout:
    fout.write('new\ncontent')
```

[in]

```python
with open('some_file.txt', 'r') as fin:
    print(fin.read())
```
[out]

    new
    content

## Содержимое файлов как массив байтов

Полезно при работе с сериализаторами

[in]

```python
s = bytearray('строка', 'utf-8')
with open('tmp.bin', 'wb') as fout:
    fout.write(s)
```

[in]

```python
with open('tmp.bin', 'r') as fin:
    print(list(fin.read()))
```
[out]

    ['с', 'т', 'р', 'о', 'к', 'а']

[in]

```python
with open('tmp.bin', 'rb') as fin:
    print(list(fin.read()))
```
[out]

    [209, 129, 209, 130, 209, 128, 208, 190, 208, 186, 208, 176]

[in]

```python
len('з'.encode('utf-8'))
```
[out]

    2

## Атрибуты объекта

- любой объект в Python имеет атрибуты: набор полей и методов, определяющих свойства объекта и способы работы с ним
- атрибуты можно читать, устанавливать и менять
- список всех атрибутов получается с помощью встроенной функции `dir`

[in]

```python
print(len(dir(5)))
print(dir(5)[: 4])
```
[out]

    70
    ['__abs__', '__add__', '__and__', '__bool__']

[in]

```python
a = 5
a.__and__(0)  # exactly the same as 'a and 0'
```
[out]

    0

## Как правильно называть переменные

- `regular_variable`
- `ClassName`
- `SOME_CONSTANT_10`
- `__private_class_field_or_method`
- `__magic_method__` or `__special_field__`

__Не используйте переменные с unicode-символами__:

- `плохое_имя_для_переменной`

## Идентификатор объекта

- у каждого объекта в Python есть целочисленный идентификатор
- на время жизни объекта он является уникальным
- получить идентификатор объекта можно с помощью функции `id`


[in]

```python
a = 10
b = 12
print(id(a), id(b))
```

[out]

    93923529852224 93923529852288


- идентификатор зависит от реализации, это может быть адрес в памяти
- у одинаковых константных объектов этот идентификатор всегда одинаковый


[in]

```python
a, b = 10, 10
c, d = 12, 12
print(id(a), id(b), '\n')
print(id(c), id(d))
```

[out]

    93923529852224 93923529852224 
    
    93923529852288 93923529852288


## Идентификатор константного объекта

- таким образом, одинаковые константы хранятся в единственном экземпляре
- Python делает так для экономии памяти
- типы в Python тоже являются объектами


[in]

```python
print(id(type(12)), id(type(5)), id(int), '\n')
print(id(None), id(type(None)))
```

[out]

    93923529721376 93923529721376 93923529721376 
    
    93923529715952 93923529715552


- проверка равенства идентификаторов делается с помощью оператора `is`


[in]

```python
a = None
print(a is None)
print(a == None)
```

[out]

    True
    True


## Идентификатор изменяемого объекта

- два одинаковых списка не идентичны:


[in]

```python
a = [1, 2, 3]
b = [1, 2, 3]
a is b
```




[out]

    False



- две ссылки на один список идентичны:


[in]

```python
c = a
a is c
```




[out]

    True



- и все между собой, очевидно, равны:


[in]

```python
a == b == c
```




[out]

    True



## Почему на None надо проверять с помощью is


[in]

```python
# https://stackoverflow.com/questions/3257919/what-is-the-difference-between-is-none-and-none

class Foo:
    def __eq__(self,other):  # magic method: == operator
        return True

foo=Foo()

print(foo==None)

print(foo is None)
```

[out]

    True
    False


- кроме того, проверка на идентичность в общем случае быстрее, чем на эквивалентность

## Стадии жизни объекта

- Создание объекта приводит к выделению фрагмента памяти
- У каждого объекта есть счётчик ссылок
- Каждое новая ссылающаяся переменная увеличивает этот счётчик на единицу
- Ссылку можно удалить с помощью оператора `del`
- Когда счётчик ссылок на объект становится равным 0, объект удаляется
- Удаление и создание объектов может не приводит к изменениям памяти в некоторых случаях из-за кэширования (например 0 или None)
- Но в общем случае память выделяется и освобождается

## Сборщик мусора

- Освобождение памяти производит сборщик мусора (Garbage Collector)
- Памяти освобождается не моментально, а в некоторый недетерминированный момент
- Одной из сложностей поиска объектов для удаления являются т.н. циклические ссылки


[in]

```python
a = [None]
a[0] = a
del a
```

- Сборщик мусора умеет работать с такими случаями

## Полезные функции


[in]

```python
import gc
gc.collect()  # call collection immediately
```


[in]

```python
import sys
a = 1
print(sys.getrefcount(a))  # cached popular value
print(sys.getrefcount('some str'))  # 1 after creation, 1 temporary, 1 - ???
```

[out]

    2331
    3


## Слабые ссылки

- Иногда возникает необходимость вести учёт объектов только когда они используются где-нибудь ещё
- Но само слежение уже создаёт ссылку, из-за которой объект будет оставаться в памяти
- Слабые ссылки дают возможность вести учёт объекта без создания ссылок на них
- Для этого используется модуль weakref
- Классическое приложение - кэширование объектов, пересоздание которых является затратным
- Слабые ссылки нельзя создавать на объекты базовых типов

## Слабые ссылки


[in]

```python
# http://old.pynsk.ru/posts/2015/Sep/19/tainstvo-standartnoi-biblioteki-slabye-ssylki-weakref/#.XkhkS9kueV4

import weakref, gc

class A:
    def __init__(self, value):
        self.value = value
    def __repr__(self):  # magic method: information for print
        return str(self.value)

a = A(10)  # create object and strong reference
d = weakref.WeakValueDictionary()  # dict with weak references

d['k'] = a
d['k']
```

[out]

    10


[in]

```python
del a
gc.collect()
d['k']
```




[out]

    10



- при запуске из терминала получается вывод "KeyError: 'k'"
- видимо, в ноутбуке создаются дополнительные неявные ссылки

