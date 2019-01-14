---
layout: post
title: "Django 설치 후 애플리케이션 첫 배포해보기"
description: ""
date: 2019-01-14
tags: [python,Django,TIL,OS X]
comments: true
---

### 0. mylenv 가상환경 실행하기.

먼저 가상환경을 실행해 줍니다.

```command-line

$ source myvenv/bin/activate

```
위 커맨드를 실행하면 커맨드 앞에 (myvenv)가 나타날 것입니다. 이러한 환경에서 다음 작업을 진행해 주세요.

### 1  Django-admin.py 실행하기

`django-admin.py` 는 스크립트로 디렉토리와 파일들을 생성한다 스크립트 실행 후에는 다음과 같은 디렉토리 구조를 생성한다.

 ``` command-line

 djangogirls
 ├───manage.py
 └───mysite
         settings.py
         urls.py
         wsgi.py
         __init__.py

 ```

### 2 setting.py 를 수정하기기.

`mysite/settings.py` 를 수정하여 한국에 맞는 설정을 해 보겠다.

* TIME_ZONE 변경

`mysite/settings.py` 에서 `TIME ZONE` 이 있는 라인을 찾아, 해당 시간대로 변경한다.

```python3

TIME_ZONE = 'Asia/Seoul'

```
* 정적 파일 경로 추가

그 다음은, 정적 파일 경로를 추가한다. `STATIC_URL` 라인 아래에 `STATIC_ROOT` 를 추가한다.

```Python3

STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')

```

* ALLOWED_HOSTS 설정 변경

`DEBUG` 가 `TRUE` 이고 `ALLOWED_HOSTS` 가 비어 있으면, 호스트는 `['localhost', '127.0.0.1', '[::1]']` 에 대해서만 유요하다. 따라서 애플리케이션 배포 시, PythonAnywhere 의 설정을 변경해 줘야 한다

```command-line

ALLOWED_HOSTS = ['127.0.0.1', '.pythonanywhere.com']

```

### 2 데이터베이스 설정하기

사이트 내에는 다양한 데이터가 저장되고, 이를 저장할 데이터 베이스를 설정하고 관리하는 여러 소프트웨어들이 존재한다. 우리는 이미 `settings.py` 안에 설치되어 있는 `sqlite3` 를 사용할 것이다.

블로그에 데이터베이스를 생성하기 위해서 `manage.py` 가 존재하는 디렉토리로 이동한 후 콘솔 창에서 다음과 같이 입력한다.

```command-line

$ python manage.py migrate

```

다음과 같은 내용이 나온다면, 성공한 것이다.

```command-line

(myvenv) ~/djangogirls$ python manage.py migrate
Operations to perform:
  Apply all migrations: auth, admin, contenttypes, sessions
Running migrations:
  Rendering model states... DONE
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying sessions.0001_initial... OK

```

### 3. 웹 서버를 시작해서 웹 사이트가 잘 작동하는지 확인해 보기

다시 `mange.py`가 있는 디렉토리로 이동한다. 그 다음, 콘솔에서 `runserver`을 입력해 , 웹 서버를 바로 시작할 수 있다.

```command-line

(myvenv) $ python manage.py runserver


```

웹 사이트가 잘 작동하는지 확인해 본다. 사용하는 브라우저를 열어 주소를 입력한다.

```browser

http://127.0.0.1:8000/

```
성공한다면 다음과 같은 화면이 나올 것이다.

웹 서버를 중지하려면, CTRL + C 를 터미널에 입력하면 된다.

![It_Woreked](https://tutorial.djangogirls.org/ko/django_start_project/images/it_worked2.png)
