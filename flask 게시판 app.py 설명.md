# flask 게시판 app.py 설명

```python
app = Flask(__name__)
app.config["SQLALCHEMY_DATABASE_URI"] = 'postgresql:///ximzdb'
app.config["SQLALCHEMY_TRACK_MODIFICATION"] = False
db.init_app(app) #models.py 의 db를 init
migrate = Migrate(app,db) #걍 때려넣어 ;;

@app.route("/")
def index():
    posts = Post.query.order_by(Post.id.desc()).all() 
    #query메소드로 모두 불러오기, list 형태로 return
    return render_template('index.html',posts=posts) #posts 변수로 넘긴다
```

```html
<!--index.html-->
{% for post in posts %}
<h1>post.title    
</h1>
<h2>post.content
</h2>
<h3>post.created_at
</h3>
{% endfor %}

```

```python
#게시글을 새로작성하는것은 '작성' + '등록' 2가지 과정
# '작성'
@app.route('/posts/new') 
def new():
    return render_template('new.html')
```

```html
<!--new.html-->
{% extends 'base.html' %}
{% block body_block %}
	<!--post형식으로 /post/create로 보냄-->
	<form action='/post/create' method='post'>        
        <div class='form-group'>
            <label for='title'>제목</label>
            <input name='title' type='text' class='form-control' id='title' 
                   placeholder='제목을 입력해주세요!'>
        </div>        
    </form>
{% endblock %}
```

```python
@app.route('/posts/create', method=['POST'])
def create():
    #post형태에서 title,content를 가져와 Post에 추가하고 add,commit
    title = requests.form.get('title')
    content = requests.form.get('content')
    post = Post(title = title, content = content)
    db.session.add(post)
    db.session.commit()
    
    return redirect('/posts/{}'.format(post.id))

#READ
@app.route('/posts/<int:id>')
def read(id):
    post = Post.query.get(id)
    return render_template('read.html', post=post)


@app.route('/posts/<int:id>/delete')
def delete(id):
    post = Post.query.get(id) #입력받은 id를 가져온 뒤 post에 넣고
    db.session.delete(post) 
    db.session.commit() #지우고 커밋한다
    return redirect('/') #지운뒤 홈으로 리다이렉트

#EDIT
@app.route('/post<int:id>/edit')
def edit(id):
    post = Post.query.get(id) #해당 id를 가진 레코드를 가져온다
    return render_template('edit.html', post=post)

```

```html
<!---read.html-->
{% extends 'base.html' %}
{% block body_block %}
	<h1>{{post.id}}</h1>
	<h1>{{post.title}}</h1>
	<h1>{{post.content}}</h1>
	<h1>{{post.created_at}}</h1>
    <a href="/posts/{{post.id}}/delete">삭제</a>
    <a href="/posts/{{post.id}}/edit">수정</a>
{% endblock %}

```

```python
#UPDATE

@app.route('/posts/<int:id>/update', methods=['POST'])
def update(id):
    post = Post.query.get(id)
    post.title = request.form.get('title') #post받은 것중 title 갖고 다시 할당
    post.content = request.form.get('content') #마찬가지
    db.session.commit() 
    
    return redirect('/posts/{}'.formate(id))


    
```

