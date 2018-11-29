# oauth



### 

### oauth 설치

#### https://django-allauth.readthedocs.io/en/latest/installation.html 접속

### authentication backends -> settings.py에 복사

### installed apps 에 복사 

```
SITE_ID = 1 써놓기(순서상관 x)
```

#### urls.py 내용 urls.py -> path 아래에다가 붙여넣기



#### migrate

```python
python manage.py migrate
```

#### admin으로 접속한 뒤 socialapp -> add 



#### facebook developers 기본설정에서 앱id, 시크릿코드



#### 공홈에서 provieders -> facebook 클릭



#### to initiate a login 3line copy -> accounts/templaates/accounts/login.html

첫줄은 base 밑에다가, 나머지 두줄은 </form> 밑에다가



#### 페이스북디벨로퍼에 도메인등록하기



#### https://로 접속해보기