# django 게시판DB 만들기!



##### cloud9 -> new workspace -> template는 Blank로 설정 후 create workspace



#### 1.환경변수 설정

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc

source ~/.bashrc
# 환경변수 추가후 bashrc 실행 => 터미널 새로고침
# exec $SHELL => 이명령어를 실행해도 됨!!
```

- 파이썬 설치

```bash
pyenv install 3.6.1 # pyenv환경에서 python 3.6.1 버전 설치
pyenv global 3.6.1 #전역 버전으로 설정
# python -V 파이썬 버전 확인

```

#### 2.가상환경 설정

* 설치

  ```bash
  git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
  ```

- 환경변수 설정

  ```bash
  echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
  source ~/.bashrc
  ```

- 가상환경 만들기



   pyenv virtualenv <파이썬 버전> <설정할 가상환경 이름>

- 가상환경 활성화 #이 순서에서 활성화 할필요없음

  ```bash
  pyenv activate 가상환경이름
  #(가상환경이름):~/workspace $ 
  # 커맨드라인 앞에 가상환경 이름이 나와야 합니다.mc
  
  pyenv deactivate #비활성화
  pyenv uninstall 가상환경이름 # 삭제
  ```



#### 3. django 설정

- 장고설치

  - 전역에서 django-admin 이라는 명령어를 사용하기 위해서
  - `pip install django`

- django 프로젝트 생성

  django-admin startproject 프로젝트이름

  cd 프로젝트이름

- django 앱생성

  django-admin startapp 앱이름

- 프로젝트 폴더에 들어가서 로컬로 가상환경을 activate 해야함

  pyenv local today_1113

- django server 실행

  python manage.py runserver $IP:$PORT

  들어가서 접속하면 c9에서 부여한 `주소`를 allowed_hosts에 추가하라고함



- 프로젝트이름으로 된 폴더 아래 settings.py 를 확인 하여

​	`ALLOWED_HOSTS =['주소입력']`

​	화이트 리스트처리를 하기때문에 C9에서 부여하는 URL을 허용한다





!![1542016399072](C:\Users\student\AppData\Roaming\Typora\typora-user-images\1542016399072.png)

# 위 화면이 나오면 준비완료!