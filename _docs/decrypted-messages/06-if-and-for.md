# Условия и циклы

`Декодированое сообщение от L: 11.IDEA-CBC`

Одна из важнейших основ любого хакерства это выбор гипотез и перебор вариантов.

![L](../img/L-3.jpg)

В жизни мы часто принимаем различные решения, и пробуем различные варианты для достижения цели. Для выражения этих мыслей и формирования логических последовательностей в программировании используются условия и циклы. Умение грамотно их использовать позволяет реализовать логику практически любой сложности. Освоив эти техники ты уже сможешь писать простые программы и автоматизировать различные процессы.

_От G:_
Помимо сообщения от L в конце я добавил еще немного информации о регулярных выражениях и модулях в стандартной библиотеки python, которые частенько применяются для решения различных задач, работы с текстом и написания API

## Условный оператор if


[in]

```python
if 3 % 3 == 0:
    print('success')
```
[out]

    success



[in]

```python
a = 5
if a == 2:
    print(2)
elif a == 4:
    print(4)
else:
    print(a)
```

[out]

    5



[in]

```python
print(a if a > 5 else 2.5)  # ternary operator
```

[out]

    2.5


## Оператор цикла while


[in]

```python
a = 5
while a > 4:
    print('Current a: {}'.format(a))
    a -= 1
```

[out]

    Current a: 5



[in]

```python
while True:  # infinity loop
    pass  # in Python 3 the equal statement is '...'
```


[in]

```python
a = 6
while a > 2:
    a -= 1
    if a == 5: continue
    if a == 3: break
    print(a)
else:
    print('else')
```

[out]

    4


- `pass` - оператор пустого действия
- `continue` - досрочный переход на следующую итерацию цикла
- `break` - досрочный выход из цикла
- `else` - обозначает секцию, которая выполняется, если цикл был завершён не по `break`

## Оператор цикла for

- в отличие от C/C++, в Python чаще всего используются range-based for-циклы
- классические циклы по индексам так же доступны, но при прочих равных менее предпочтительны


[in]

```python
lst = ['a', 'b', 'c']
for element in lst:  # range-based for
    print(element)
```

[out]

    a
    b
    c



[in]

```python
for index in range(len(lst)):  # index-based for
    print(lst[index])
```

[out]

    a
    b
    c


- функция `range` создаёт генератор, позволяющий итерироваться по последовательности чисел с заданными границами и шагом

## Оператор цикла for


[in]

```python
for x, y in [(1, 'a'), [2, 'b']]:
    print(x, y)
else:
    print('For-loop ended without break!')
```

[out]

    1 a
    2 b
    For-loop ended without break!



[in]

```python
for x, y, z in [[1, 2, 3], ['a', 'b', 'c'], [True, False, None]]:
    if isinstance(x, int):
        continue
    print(x, y, z)
```

[out]

    a b c


- `isinstance` - функция языка, позволяющая проверить принадлженость объекта типу (учитывает иерархию наследования типов)


## Модули

- любой файл на Python представляет собой модуль
- импорт модуля вызовет выполнение содержащегося в нём кода


[in]

```python
with open('test_module.py', 'w') as fout:
    fout.write('print(10)\n')
    fout.write('def new_print(a):\n\tprint(a)\n')
```

- создали текстовый файл и записали в него оператор печати и определение функции
- ключевое слово `def` используется для определения функций и классов (не единственный способ)


[in]

```python
import test_module
```

[out]

    10


- импортируем модуль, операторы выполнятся

__В стандартной библиотеке языка есть много полезных модулей - надо пользоваться__

## Пространства имён модулей


[in]

```python
new_print(5)
```


[out]

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-270-2209d66c60e3> in <module>
    ----> 1 new_print(5)
    

    NameError: name 'new_print' is not defined



[in]

```python
test_module.new_print(5)
```

[out]

    5



[in]

```python
from test_module import new_print
new_print(5)
```

[out]

    5


## Повторная загрузка модуля

- если модуль был один раз загружен (исполнен), второй импорт ничего не произведёт
- это верно даже в том случае, если модуль был изменён после импорта (!)


[in]

```python
import test_module  # no any output!
```

- но модуль можно перезагрузить принудительно


[in]

```python
from importlib import reload
reload(test_module)
```

[out]

    10





    <module 'test_module' from '/home/mel-lain/mipt-python/tmp/test_module.py'>



## Модуль collections

Стандартная задача: подсчёт числа элементов


[in]

```python
s = 'GDJKFHGKJXBZFVJHBJZBXXXXXXXXXXXXXXXXXXXHFG'
```


[in]

```python
d = {}
for element in s:
    if not element in d:
        d[element] = 0
    d[element] += 1

result = ''
for k, v in d.items():
    result += f'({k}: {v}) '
print(result.strip())
```

[out]

    (G: 3) (D: 1) (J: 4) (K: 2) (F: 3) (H: 3) (X: 20) (B: 3) (Z: 2) (V: 1)



[in]

```python
from collections import Counter

for k, v in Counter(s).items():
    print(f'({k}: {v}) ', end='')  # print can end not only with '\n'
print()
```

[out]

    (G: 3) (D: 1) (J: 4) (K: 2) (F: 3) (H: 3) (X: 20) (B: 3) (Z: 2) (V: 1) 


## Модуль os для работы с системой


[in]

```python
import os

os.path.exists('test.py')
```




[out]

    True




[in]

```python
os.path.isfile('test.py')
```




[out]

    True




[in]

```python
os.path.isdir('test.py')
```




[out]

    False




[in]

```python
len(os.listdir('.'))
```




[out]

    26




[in]

```python
addr = os.path.dirname(os.path.abspath('test.py'))
print(addr)
```


[in]

```python
os.path.join(*addr.split('/'))  # f(*[a, b, c]) -> f(a, b, c)
```




[out]

    'home/mel-lain/mipt-python/tmp'



## Модуль re для регулярных выражений


[in]

```python
import re
```

- `[]` - множество допустимых символов
- `-` - обозначает диапазон
- `*` - любое число повторений (в т.ч. 0)


[in]

```python
eng_letters = re.compile('[a-zA-Z]*')

print(eng_letters.match(''))
print(eng_letters.match('qwerty'))
print(eng_letters.match('йцукен'))
print(eng_letters.match('QWERTY'))
print(eng_letters.match('qweкен'))
```

[out]

    <re.Match object; span=(0, 0), match=''>
    <re.Match object; span=(0, 6), match='qwerty'>
    <re.Match object; span=(0, 0), match=''>
    <re.Match object; span=(0, 6), match='QWERTY'>
    <re.Match object; span=(0, 3), match='qwe'>


## Регулярные выражения

- Букву Ё прописываем отдельно, она вне диапазона
- Как в обычных строках, спецсимволы вносим как обычные с помощью `\`
- `+` - любое число повторений, но не менее одного


[in]

```python
eng_letters = re.compile('[a-zA-Zа-яА-ЯёЁ\\-.@]+')

print(eng_letters.match(''))
print(eng_letters.match('йцукен'))
print(eng_letters.match('Ёжик'))
print(eng_letters.match('Фрекен-Бок'))
print(eng_letters.match('mail@ya.ru'))
```

[out]

    None
    <re.Match object; span=(0, 6), match='йцукен'>
    <re.Match object; span=(0, 4), match='Ёжик'>
    <re.Match object; span=(0, 10), match='Фрекен-Бок'>
    <re.Match object; span=(0, 10), match='mail@ya.ru'>


## Регулярные выражения

- `^` - обозначает необходимость начала строки при совпадении
- `$` - обозначает необходимость конца строки при совпадении
- `{}` - после квадратных скобок позволяет ограничить количество вхождений символов


[in]

```python
phone_pattern = re.compile('^(\\+[0-9]{1} ?\\(?[0-9]{3}\\)? ?[0-9]{7})+$')

print(phone_pattern.match('89167698275'))
print(phone_pattern.match('+7 (916) 7698275'))
print(phone_pattern.match('+7(916)7698275'))
```

[out]

    None
    <re.Match object; span=(0, 16), match='+7 (916) 7698275'>
    <re.Match object; span=(0, 14), match='+7(916)7698275'>



[in]

```python
email_pattern = re.compile('^[A-Za-z0-9\.\+_-]+@[A-Za-z0-9\._-]+\.[a-zA-Z]*$')

print(email_pattern.match('mel-lain@yandex.ru'))
print(email_pattern.match('mel&lain@yandex.ru'))
print(email_pattern.match('mel-lain@yandex'))
```

[out]

    <re.Match object; span=(0, 18), match='mel-lain@yandex.ru'>
    None
    None


## Регулярные выражения


[in]

```python
email_pattern = re.compile('[A-Za-z0-9\.\+_-]+@[A-Za-z0-9\._-]+\.[a-zA-Z]*')

print(email_pattern.match('mel-lain@yandex.ru mel-lain@yandex.ru'))
email_pattern.findall('mel-lain@yandex.ru mel-lain@yandex.ru')
```

[out]

    <re.Match object; span=(0, 18), match='mel-lain@yandex.ru'>





    ['mel-lain@yandex.ru', 'mel-lain@yandex.ru']



Вместо конкретных символов можно использовать общие обозначения:

- `\s` - один пробел
- `\S` - один не пробел
- `\w` - один alpha-numeric символ


[in]

```python
re.split('\w', '&а%б!7#в*')
```

[out]

    ['&', '%', '!', '#', '*']

