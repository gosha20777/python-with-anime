# Инструменты командной строки python

`Декодированое сообщение от L: 04.hex`

Тут я расскажу тебе о некоторых командных инструментах python которые помогут тебе при разработке 🐍

## Python

Проверить версию python можно командой

```bash
python -V
```

Зайти в интерпретатор можно просто набрав
```bash
python
```

Запустить файл на исполнение можно с помощью
```bash
python my-script.py
```

Также можно запустить отделённую команду питона
```
python -c 'print("Я учу питон (◠‿◠)")'
```

Или несколько команд...
```
python -c 'i_am = "Я";print(f"{i_am} учу питон (◠‿◠)")'
```

Можно запустить отдельный модуль
```
python -m pip -h
```

Полную справку по аргуменам python можно получить выполнив
```
python -h
```

## Pip

Pip это менеждер пакетов python. Он берет пакеты из https://pypi.org/. Тут можно найти все (◠‿◠)

У питона самая большая база пакетов - в этом его преимущество.

![pip](../img/pip.jpeg)

Проверить версию python можно командой

```bash
pip -V
```

Установить пакет можно используя

```
pip install <package name>

pip install <package name>==<version>
```

или

```
pip install -r requirements.txt
```

Также можно удалить пакет

```
pip uninstall <package name>
```

найти пакет по названию можно так

```
pip search <package name>
```

`freeze` - удобная команда, чтобы вывезти все пакеты и их версии.

```
pip freeze
```


Лайвхак от G. С помощью этой команды можно легко формировать requirements.txt

```
pip freeze > requirements.txt
```

Запросить справку можно так

```
pip -h
pip install -h
```

## Virtualenv

В корне своем, главная задача виртуальной среды Python – создание изолированной среды для проектов Python.

Это значит, что:

Каждый проект может иметь свои собственные зависимости, вне зависимости от того, какие зависимости у другого проекта.

И так, в нашем небольшом примере вверху, нам просто нужно создать раздельную виртуальную среду для проектов А и Б. Каждая среда, в свою очередь, сможет зависеть от любой версии проекта В, независимо друг от друга.

Это хорошо тем, что у нас нет ограничений на то, в скольких экземплярах будет наша виртуальная среда, так как они являются обычными каталогами, в которых содержится несколько скриптов. Плюс, их очень легко создать при помощи инструментов командной строки virtualenv

Создать окружение можно с помошью 

```
virtualenv env
```

По умолчанию, это не включает в себя ни один из существующих сторонних пакетов.

Как выглядит внутри?
Это просто каталог под названием «env», структура каталога которого схожа со следующей:

```
├── bin
│   ├── activate
│   ├── activate.csh
│   ├── activate.fish
│   ├── easy_install
│   ├── easy_install-3.7
│   ├── pip
│   ├── pip3
│   ├── pip3.7
│   ├── python -> python3.7
│   ├── python3 -> python3.7
│   └── python3.5 -> /Library/Frameworks/Python.framework/Versions/3.7/bin/python3.7
├── include
├── lib
│   └── python3.7
│       └── site-packages
└── pyvenv.cfg
```

Что находится в этих папках?

- bin – файлы, которые взаимодействуют с виртуальной средой;
- include – С-заголовки, компилирующие пакеты Python;
- lib – копия версии Python вместе с папкой «site-packages», в которой установлена каждая зависимость.

Более интересные сейчас – скрипты activate в папке bin. Эти скрипты используются для настройки твоей оболочки для использования исполняемого файла среды Python и его сайтовых пакетов по умолчанию.

для активации этого скила использу команду

```
source env/bin/activate
```

В терминале кое - что поменялось. Появилась приставка `(env)`. Это значит что скилл активирован и ты в виртуально окружении.

Теперь можно устанавливать внутрь окружения пакеты. Поставим bcrypt для шифрования.

```bash
(env) $ pip install bcrypt
(env) $ python -c 'import bcrypt;text="Sasha the best";print(f"{text} -> {bcrypt.hashpw(text.encode('utf-8'), bcrypt.gensalt())}")'
Sasha the best -> $2b$12$vWa/VSvxxyQ9d.WGgVTdrell515Ctux36LCga8nM5QTW0.4w8TXXi
```

Для возвращения в обратное состояние используй команду

```
(env) $ deactivate
```

выполним тоже самое:

```
$ python -c 'import bcrypt;text="Sasha the best";print(f"{text} -> {bcrypt.hashpw(text.encode('utf-8'), bcrypt.gensalt())}")'

ImportError: No module named 'bcrypt'
```

В этом прелесть virtualenv