# Structure

```
project
│    
└───README.md
│
└───cv
│   │
│   └───task (e.g. classification)
│       │   
│       └───subtask (e.g. binary)
│           │
|           └───name_model (e.g. bath)
|           |   |
|           |   └───version_model_1 (e.g. baseline)
|           |   |   |
|           |   |   └───data
|           |   |   └───notebooks
|           |   |   |   |
|           |   |   |   └───experiments
|           |   |   |   |   |
|           |   |   |   |   └───experiments1.ipynb
|           |   |   |   |   └───...
|           |   |   |   |   └───experimentsk.ipynb
|           |   |   |   |
|           |   |   |   └───notebooks1.ipynb
|           |   |   |   └───...
|           |   |   |   └───notebooksk.ipynb
|           |   |   |   └───README.md
|           |   |   |   └───pyproject.toml
|           |   |   |    
|           |   |   └───reports
|           |   |   |   |
│           |   |   |   └───experiment1
│           |   |   │   │    │
│           |   |   │   │    └───report1
│           |   |   │   │    └───...
│           |   |   │   │    └───reportk
│           |   |   |   │
│           |   |   |   └───...
|           |   |   |   └───experimentk    
|           |   |   |
|           |   |   └───logs
|           |   |   |   |
│           |   |   |   └───experiment1
|           |   |   |   └───...
|           |   |   |   └───experimentk
|           |   |   |
|           |   |   └───weights
|           |   |   └───download.py
|           |   |
|           |   └───...
|           |   └───version_model_k
|           |   
|           └───...
|           └───name_modelk
│   
└───nlp
│   │
│   └───task
│       │   
│       └───subtask
│           │
|           └───name_model
|               |
|               └───likewise cv

```

# Облако Yandex

В директории `datasets` сохраняются готовые датасеты на которых обучалась модель. Сырые данные из которых формировался датасет, могут находиться в различных источниках, на различных устройствах. Структура директорий в папке `datasets` полностью идентична структуре формирования проекта. Датасеты связанный с проектом, лежат по тому же пути в папке `datasets`. 

Облако Yandex: [datasets](https://disk.yandex.ru/client/disk/datasets)

# Подготовка сервера

Доустановим необходимые утилиты.

```commandline
sudo apt-get update
```

```commandline
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl nano
```

### Установить pyenv

Управляем версиями Python утилитой `pyenv`. 

```commandline
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
```

Открываем файл `~/.profile`.

```commandline
sudo nano ~/.profile
```

В конец файла вставляем и сохраняем.

```commandline
# pyenv
export PYENV_ROOT="$HOME/.pyenv"

export PATH="$PYENV_ROOT/bin:$PATH"

eval "$(pyenv init --path)"
```

Закрываем и открываем терминал.

Проверяем, установилась ли утилита `pyenv`. Должна открыться меню `pyenv`.

```commandline
pyenv
```

Добавить в `pyenv` нужную версию Python.

```commandline
pyenv install 3.9.15
```

# Git

Репозиторий закрыт, предварительно нужно создать токен в GitHub и потом
клонировать.

### Create token GitHub

1. Переходим на сайт GitHub.

2. Нажимаем на иконку профиля в правом верхнем углу.

3. Из выпадающего списка выбираем `settings`.

4. В меню слева выбираем `Developer settings`.

5. В меню слева выбираем `Personal access tokens > Tokens (classic)`.

6. Справа нажимаем на кнопку `Generate new token > Generate new token (classic)`

7. В поле `Node` пишем произвольное название токена.

8. Проставляем везде галочки и внизу нажимаем на кнопку `Generate token`.

9. В новом окне появится сгенерированный токен, копируем и сохраняем.


### Clone private repository

```commandline
git clone https://<account_name>:<account_token>@github.com/<account_name>/<repo_name>.git -b <name_branch>
```

`<account_name>`: имя вашего аккаунта Github.

`<account_token>`: токен вашего аккаунта Github.

`<repo_name>`: название клонируемого репозитория.

`<name_branch>`: название ветки, которую хотим клонировать,
можно без ключа `-b <name_branch>`, тогда будет склонирована основная ветка.

Подписать автора комитов.

```commandline
git config --global user.name "name"
```

```commandline
git config --global user.email "email@example.com"
```

Переходим в дирректорию проекта.

```commandline
cd <repo_name>
```

Устанавливаем в проекте необходимую версию Python

```commandline
pyenv local 3.9.15
```

# Poetry

В проекте используется менеджер пакетов `poetry`.

### Install

Скачать и установить [poetry](https://python-poetry.org/docs/#installing-with-the-official-installer).

```commandline
curl -sSL https://install.python-poetry.org | python -
```

Добавить путь к `poetry`.

```commandline
export PATH="/home/jovyan/.local/bin:$PATH"
```

### Установить окружение

Мы либо используем уже созданное окружение, либо создаем новое. Два сценария
описано ниже.

### Создать новое окружение

Переходим в дирректорию с проектом.

Создаем новый файл окружения `pyproject.toml`.

```commandline
poetry init
```

После создания заходим в окружение

```commandline
poetry shell
```

Добавляем нужные библиотеки.

```commandline
poetry add <name_library>
```

### Установить существующее окружение

Переходим в дирректорию с версией модели, там
находится файл `pyproject.toml`.

Заходим в оболочку окружения.

```commandline
poetry shell
```

Устанавливаем окружение.

```commandline
poetry install
```

**Возможные ошибки и исправления**

Ошибка

```
Current Python version (3.8.10) is not allowed by the project (^3.9.10).
Please change python executable via the "env use" command.
```

Исправление

Удалить и заново поставить окружение. Вне окружения необходимо выполнить команды.

Посмотреть название окружения.

```commandline
poetry env info
```

Удалить окружение.

```commandline
poetry env remove <name_env>
```
`<name_env>`: название окружения, пример названия `layer-7iBn6U-py3.9`.

# Create kernel

После создания окружения, его нужно подключить к jupyter notebook.
Для этого необходимо создать `kernel` с окружением.

Заходим в оболочку окружения.

```commandline
poetry shell
```

Добавляем в окружение библиотеку. Ключ `-D` означает, что добавляем
в `dev` окружение. Тогда будет понимание, какие билиотеки нам не
нужны будут при разработке сервиса в прод.

```commandline
poetry add -D ipykernel
```

Создадим `kernel`.

```commandline
ipython kernel install --user --name <name_kernel> --display-name="name_kernel"
```

После создания `kernel` в `Jupyter Lab` в `Launcher` в разделе `Notebook`
появится ноутбук с созданным `kernel`. Открыв его, откроется ноутбук
в котором будет нужный `kernel` с нужным окружением.