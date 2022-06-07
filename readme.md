# 《專案指引》

## 建置專案

### (1) 建置專案目錄

```sh
❯ cd ~/workspace/django
❯ mkdir ex2002-01 && cd $_
```

### (2) 設定使用之 Python Interpreter

```sh
❯ pyenv versions
......
❯ pyenv local 3.10.0
```

### (3) 透過 pipenv 安裝 Django 套件

```sh
❯ pipenv install django
Creating a virtualenv for this project...
Pipfile: /Users/alanjui/workspace/django/ex-2022-01/Pipfile
Using /Users/alanjui/.pyenv/versions/3.10.0/bin/python3 (3.10.0) to create virtualenv...
⠋ Creating virtual environment...created virtual environment CPython3.10.0.final.0-64 in 665ms
  creator CPython3Posix(dest=/Users/alanjui/.local/share/virtualenvs/ex-2022-01-O0_oecUE, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/Users/alanjui/Library/Application Support/virtualenv)
    added seed packages: pip==22.0.4, setuptools==62.1.0, wheel==0.37.1
  activators BashActivator,CShellActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator

✔ Successfully created virtual environment!
Virtualenv location: /Users/alanjui/.local/share/virtualenvs/ex-2022-01-O0_oecUE
Creating a Pipfile for this project...
Installing django...
Adding django to Pipfile's [packages]...
✔ Installation Succeeded
Pipfile.lock not found, creating...
Locking [dev-packages] dependencies...
Locking [packages] dependencies...
Building requirements...
Resolving dependencies...
✔ Success!
Updated Pipfile.lock (79baf8)!
Installing dependencies from Pipfile.lock (79baf8)...
  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 0/0 — 00:00:00
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
```

### (4) 進入專案用 Python Virtual Environment

```sh
❯ pipenv shell
Launching subshell in virtual environment...
 . /Users/alanjui/.local/share/virtualenvs/ex-2022-01-O0_oecUE/bin/activate
❯  . /Users/alanjui/.local/share/virtualenvs/ex-2022-01-O0_oecUE/bin/activate
```

## 啟用專案

### (1) 建置 Django Project

```sh
❯ django-admin startproject web_project .

❯ la
total 40
-rw-r--r--  1 alanjui  staff     7B  6  5 13:26 .python-version
-rw-r--r--  1 alanjui  staff   152B  6  5 13:29 Pipfile
-rw-r--r--  1 alanjui  staff   1.4K  6  5 13:29 Pipfile.lock
-rwxr-xr-x  1 alanjui  staff   667B  6  5 13:45 manage.py
-rw-r--r--  1 alanjui  staff   2.1K  6  5 13:43 readme.md
drwxr-xr-x  7 alanjui  staff   224B  6  5 13:45 web_project

❯ tree web_project
web_project
├── __init__.py
├── asgi.py
├── settings.py
├── urls.py
└── wsgi.py

0 directories, 5 files
```

### (2) 對「專案資料庫」進行初始化

```sh
❯ ./manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying sessions.0001_initial... OK
```

### (3) 啟動專案 App 。

```sh
❯ ./manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
June 05, 2022 - 05:54:55
Django version 4.0.5, using settings 'web_project.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
[05/Jun/2022 05:56:25] "GET / HTTP/1.1" 200 10697
[05/Jun/2022 05:56:25] "GET /static/admin/css/fonts.css HTTP/1.1" 200 423
[05/Jun/2022 05:56:25] "GET /static/admin/fonts/Roboto-Bold-webfont.woff HTTP/1.1" 200 86184
[05/Jun/2022 05:56:25] "GET /static/admin/fonts/Roboto-Light-webfont.woff HTTP/1.1" 200 85692
[05/Jun/2022 05:56:25] "GET /static/admin/fonts/Roboto-Regular-webfont.woff HTTP/1.1" 200 85876
Not Found: /favicon.ico
[05/Jun/2022 05:56:25] "GET /favicon.ico HTTP/1.1" 404 2115
```

## 建立專案模組

建立名為 hello 之專案模組（Django Application）。

```sh
❯ ./manage.py startapp hello
❯ la
total 304
-rw-r--r--  1 alanjui  staff     7B  6  5 13:26 .python-version
-rw-r--r--  1 alanjui  staff   152B  6  5 13:29 Pipfile
-rw-r--r--  1 alanjui  staff   1.4K  6  5 13:29 Pipfile.lock
-rw-r--r--  1 alanjui  staff   128K  6  5 13:50 db.sqlite3
drwxr-xr-x  9 alanjui  staff   288B  6  5 13:57 hello
-rwxr-xr-x  1 alanjui  staff   667B  6  5 13:45 manage.py
-rw-r--r--  1 alanjui  staff   4.1K  6  5 13:56 readme.md
drwxr-xr-x  7 alanjui  staff   224B  6  5 13:45 web_project
❯ tree hello
hello
├── __init__.py
├── admin.py
├── apps.py
├── migrations
│   └── __init__.py
├── models.py
├── tests.py
└── views.py

1 directory, 7 files
```

## 除錯作業

### (1) 安裝 Python 套件

```sh
pipenv install debugpy
```
