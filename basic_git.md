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

Вернуть файлы к состоянию последнего коммита.

```commandline
git checkout .
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

### Создать новую ветку

Посмотрим какие ветки существуют.

```commandline
git branch -a
```

Создадим новую ветку.

```commandline
git branch <name_new_branch>
```

Переключимся на новую ветку.

```commandline
git checkout <name_new_branch>
```

Отправим ветку на сервер. После этого можно отправлять коммиты как обычно, просто вводя команду `git push`.

```commandline
git push -u origin <name_new_branch>
```

### Merge

1. Заходим в репозиторий на сайте.

2. Переходим в список веток `n branch`.

3. Переходим в раздел `Active`.

4. Напратив названия ветки нажимаем на кнопку `New pull request` и делаем merge.

5. После merge удаляем ветку (смотрим в том же меню, где делали merge).

6. Переходим в локальный репозиторий и обновляем изменения 

```commandline
git pull
```

Почистим ветки в локальном репозитории.

7. Переключимся на основную ветку.

```commandline
git checkout main
```

8. Удалить удаленное отслеживание, если ветки нет на удаленном репо.

```commandline
git remote prune origin
```

9. Удаляем локальные ветки, они двух видов `<name_branch>` и `remotes/origin/<name_branch>`.

```commandline
git branch -D <name_branch>
```

```commandline
git branch -D remotes/origin/<name_branch>
```

10. Обновляем локальную версию.

```commandline
git pull
```