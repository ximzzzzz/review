# git_learn



### git process

![git processì ëí ì´ë¯¸ì§ ê²ìê²°ê³¼](http://pismute.github.io/whygitisbetter/images/local-remote.png)



### git은 hash 처리를 통해 변화를 감지하고 업데이트한다.



##### ` git config --global user.name 'ximzzzzz'`

글로벌 변수 user.name 에 'ximzzzz' 를 할당한다.



##### `git config --local user.email 'ximzzzzz@gmail.com'`

로컬변수 user.email에 할당한다.



##### `git status`

on branch master

untracked 되있을경우 업데이트를 체크하지 않음



##### `git add index.html`

명령어를 통해 트랙할 수 있게 등록



##### `git commit -m 'add index.html' `

##### `git log`

hash 변환코드와 기록 확인 가능



##### `git log --graph`

변화내용을 그래프(branch별로) 확인가능



##### `echo "# git_learn" >> README.md`

오른쪽 스트링을 README.md에 추가



### 외부주소로 보내기



##### `git remote add origin https://github.com/ximzzzzz/git_learn.git`

외부저장소를 origin으로 저장

##### `git remote`

##### `git remote --v`



##### `git push -u origin master`

### 

### ignore는 무엇인가

##### `이상한파일을 올리지 않기 위함이다`

`touch .gitignore`



### branch는 무엇인가

`git checkout -b 'about'`

checkout master로 가보면 'about'때 변경사항이 반영되있지 않다.

about에서 완료가 되면 master에 병합시킬 수 있다(merge)



`(master) git merge about`

master 상태에서 about의 변경사항을 흡수한다



### 팀플하기

팀원은 `git clone https://github.com/ximzzzzz/git-team.git` 을통해 가져올 수 있다

이후, `git pull` 을 통해 내용을 가져올 수 있다.



#### 팀장, 팀원이 서로 다른 코드를 작성할 경우







