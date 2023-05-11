# Poetry

### Создать новое окружение

Переходим в дирректорию с версией модели.

```commandline
poetry init
```

Далее заполняем мета информацию и указываем какую версию Python
использовать. В проектах используем `Python 3.9`.

На вопросы:

Would you like to define your main dependencies interactively?

Would you like to define your development dependencies interactively?

пишем `no`.

После заполнения, создастся файл `pyproject.toml` файл, в котором будут хранится
все зависимости и технический файл `poetry.lock`.

### Работа с окружением

Зайти в оболочку окружения. Переходим в дирректорию с версией
модели, там находится файл `pyproject.toml`.

```commandline
poetry shell
```

Добавить библиотеку в окружение.

```commandline
poetry add <library>==<version>
```

### Удалить окружение

Посмотреть какие окружения установлены.

```
ls /home/jovyan/.cache/pypoetry/virtualenvs/
```

Посмотреть сколько окружение занимает места.

```
du -sh /home/jovyan/.cache/pypoetry/virtualenvs/<dir_name>
```

Вначале необходимо удалить ядро для ноутбука, чтобы оно больше не отображалось в интерфейсе Jupyter Lab. Смотрим список из имеющихся ядер.

```
jupyter kernelspec list
```

Удалить ненужное ядро.

```
jupyter kernelspec uninstall <name kernel>
```

Посмотреть имеющиеся окружения.

```
ls /home/jovyan/.cache/pypoetry/virtualenvs/
```

Удалить ненужное окружение.

```
sudo rm -rf /home/jovyan/.cache/pypoetry/virtualenvs/<dir_name>
```


