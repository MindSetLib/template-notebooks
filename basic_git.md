# Basic git commands

Подписать автора коммитов.

```commandline
git config --global user.name "name"
```

```commandline
git config --global user.email "email@example.com"
```

Посмотреть состояния файлов в git.

```commandline
git status
```

Добавить файлы в индекс, которые пойдут в комит.

```commandline
git add <file_name>
```

Добавить дирректорию в индекс. В дирректории
должны быть файлы, если она пустая, то git ничего не добавит.

```commandline
git add <dir_name>/
```

Удалить все файлы из индекса, которые были добавлены командой `git add`.

```commandline
git reset
```

Удалить определенный файл из индекса.

```commandline
git reset <file_name>
```

Добавить комит.

```commandline
git commit -m "Name commit"
```

Переименовать последний комит.

```commandline
git commit --amend -m "New name commit"
```

Отменить последний комит.

```commandline
git revert <hash_commit>
```

Посмотреть какие комиты не были отправлены на сервер.

```commandline
git diff origin/main..HEAD
```

Отправить комиты на сервер.

```commandline
git push
```

Получить изменения с сервера.

```commandline
git pull
```

Посмотреть историю комитов.

```commandline
git log
```

Удалить определенный файл из репозитория.

```commandline
git rm <file_name>
```

Восстановить удаленный файл в исходное состояние.
Происходит в два этапа, вначале необходимо убрать файл из индекса,
следом вернуть в исходное состояние.

```commandline
# убрать файл из индекса
git restore --staged <file_name>
```

```commandline
# вернуть в исходное состояние
git restore <file_name>
```