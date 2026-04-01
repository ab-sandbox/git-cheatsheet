# Git Cheatsheet

Небольшая шпаргалка по базовым командам Git.

---

## Инициализация репозитория

```bash
git init
```

Связать с удаленным репозиторием:

```bash
git remote add origin git@github.com:USERNAME/REPO.git
```

## Клонирование

```bash
git clone git@github.com:USERNAME/REPO.git
```

## Работа с файлами

```bash
git status
git add filename.txt
git add .
```

## Коммиты

```bash
git commit -m "Описание изменений"
```

Если вызвать commit без -m, откроется редактор:
```bash
git commit
```

### Редактор nano

По умолчанию часто открывается nano:

- написать сообщение
- сохранить: Ctrl + O → Enter
- выход: Ctrl + X

### Редактор vi / vim

Если открылся vi / vim:

- нажать i (режим вставки)
- написать сообщение
- нажать Esc
- ввести :wq и нажать Enter (сохранить и выйти)

### Изменить последний коммит:

```bash
git commit --amend
```

### Изменить автора коммита:

```bash
git commit --amend --author="ab-sandbox <devmachine@yandex.ru>"
git push --force
```

> ⚠️ Только если коммит еще не используется другими разработчиками (до merge, в feature-ветке / MR / PR). 
> В общих репозиториях переписывать историю не рекомендуется.


## Отправка на GitHub

Переименовать текущую ветку в main:

```bash
git branch -M main
```
Первый пуш с привязкой к origin:

```bash
git push -u origin main
```

Обычный пуш:
```bash
git push
```

## Обновление проекта

```bash
git pull
```

## Ветки

```bash
git branch feature
git checkout feature
git checkout -b feature
```

## Fork

Fork — это копия чужого репозитория.

```bash
git clone git@github.com:YOUR_USERNAME/REPO.git
```

## Remote

```bash
git remote -v
git remote set-url origin git@github.com:USERNAME/REPO.git
```

## Настройка пользователя (креды)

Глобально:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Локально (для конкретного проекта):

```bash
git config user.name "ab-sandbox"
git config user.email "devmachine@yandex.ru"
```

Проверка:

```bash
git config --list
```

## Работа с SSH-ключами

Сгенерировать ключ:

```bash
ssh-keygen -t ed25519 -C "your@email.com"
```

## Несколько SSH-ключей

Пример файла `~/.ssh/config`:

```bash
Host github-sandbox
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_sandbox

Host github-work
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_work
```

Использование:

```bash
git remote set-url origin git@github-sandbox:USERNAME/REPO.git
```

## Полезно помнить

* git add — подготовка
* git commit — сохранение
* git push — отправка
* git pull — получение
