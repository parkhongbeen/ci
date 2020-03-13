[![codecov](https://codecov.io/gh/parkhongbeen/ci/branch/master/graph/badge.svg)](https://codecov.io/gh/parkhongbeen/ci)

## CI

> 채우기

### Django기본 테스트

```
python manage.py test
```

### coverage

> 코드에서 테스트가 얼마나 충족되었나?

````
coverage run --source='.'  app/manage.py test #실행시킴
coverage report -m #실행결과를 알려줌
````

```python
coverage에서 제외시키는법
.coverage파일을 app밖에 생성 후 내용 적어주기 / iniconfig파일로 생성

[run]
source =
    app

omit =
    app/manage.py
    app/config/asgi.py
    app/config/wsgi.py

# __str__함수는 converage report에서 제
[report]
exclude_lines =
    def __str__
```

### pytest, pytest-django

>  Django기본 테스트 대신,pytest를 사용

``` 
poetry add pytest pytest-django
```

```python
pytest.ini파일생성 후 내용작성

[pytest]
python_files = tests.py test_*.py *_tests.py
DJANGO_SETTINGS_MODULE = config.settings
addopts = --nomigrations --reuse-db
```

### codecov

> codeecov.io에 테스트 리포트를 쉽게 업로드할 수 있도록 도와주는 라이브러리

### pytest-cov

> pytest를 사용해서 codecov.io에 업로드 할 리포트를 만들어주는 라이브러리

```
poetry add codecov pytest-cov
pytest --cov app
CODECOV_TOKEN=<codecov.io Token> codecov
CODECOV_TOKEN=9546cc9c-3c3a-49fe-8d0b-c4d77f076e37 codecov
```

