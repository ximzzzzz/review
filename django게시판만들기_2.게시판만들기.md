# django 게시판DB 만들기!

#### 1. 기본구조

​	`urls.py` : 주소를 입력받을 수 있는 라우터를 열어준다(app.py 에서 @app.route()와 같은역할)

​	`views.py` : 라우터에대한 상세한 method 를 정의하는곳!

​	만들었던 app폴더 안에 templates 폴더를 만들고 `html문서`를 저장한다



#### 1.5 (app 내에) models.py

```python
class Post(models.Model):
  	 title = models.CharField(max_length=50) #컬럼 두개 추가
   	 content = models.CharField(max_length=100)
    
def __str__(self): #오브젝트 출력할때 타이틀로 출력하도록 재설정
        return self.title
```

​	

#### 2. urls.py 

- app 내의 views 설정하기

  ```python
  from django_intro import views
  ```

- urlpatterns =[ ] 내에 path를 추가한다

  ```python
  urlpatterns =[
      path('whoami', views.whoami), #쉼표에 주의한다 ㅅㅂ
  ]
  ```



#### 2.5 DB와 model 사이에 sql로 변환할 수 있또록 migration 해줘야함

```python
python manage.py makemigrations #설계도 작성
python manage.py migrate #실제로 번역하기
```



#### 2.6 (app내의) admin.py 에서 만들었던 model을 등록하기

```python
from .models import Post #현재 폴더에 있는 models.py 에서 Post 클래스 추가
admin.site.register(Post)

```

#### 2.7 admin페이지에서 확인을 위해 superuser 생성

```bash
python manage.py createsuperuser
```



#### 3.views.py

- 메소드 정의하기

  ```python
  def whoami(request):
      return render(request, 'whoami.html')
  ```

#### 4.settings.py

- templates 위치 지정해주기 : TEMPLATES 안에 경로를 추가해준다
- INSTALLED_APPS 안에 APP 이름을 추가해준다

```python
'DIRS' :[os.path.join(BASE_DIR,'templates')] #app을 돌며 templates 폴더인식
    #기본적으로 install 한 순서대로 templates를 인식한다
    #(나중에 만든 templates폴더는 구분이 필요함)
    
INSTALLED_APPS = ['django_intro',]
```

