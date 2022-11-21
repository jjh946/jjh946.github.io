---
layout: post
title: "Welcome to Jekyll!"
date: 2018-02-05 15:13:18 +0200
image: 12.jpg
tags: [jekyll, docs]
categories: jekyll
---
# Python Django Web Framework 9~11

# 이번 강의에서는 무엇을 구현 할것인가?

- create 링크 클릭

![Untitled](Python%20Django%20Web%20Framework%209~11%208b3e0b4f576c44c993e278fe9026b575/Untitled.png)

- title과 body text를 입력하고 제출할 수 있는 칸이 나옴

![Untitled](Python%20Django%20Web%20Framework%209~11%208b3e0b4f576c44c993e278fe9026b575/Untitled%201.png)

- 글을 작성하고 제출하면 추가 페이지가 생성되면서 내용 보임

![Untitled](Python%20Django%20Web%20Framework%209~11%208b3e0b4f576c44c993e278fe9026b575/Untitled%202.png)

![Untitled](Python%20Django%20Web%20Framework%209~11%208b3e0b4f576c44c993e278fe9026b575/Untitled%203.png)

# method=GET,POST

여러개의 값을 뒤에 붙여서 보낼 수 있는 것을 쿼리 스트링이라고 한다. 

서버에게 질의를 하는 스트링.

첫번째 두번째 방식 둘다 GET 방식

url을 공유할때 쿼리스트링 방식으로 하게 되면 매 클릭마다 글이 추가되기 때문에 이와같이 하면 안된다.

이 때 POST 방식을 사용하면 된다. 이렇게 하면 url이 아닌 header에 정보들을 포함해서 눈에 보이지 않게 보낼 수 있다.

![Untitled](Python%20Django%20Web%20Framework%209~11%208b3e0b4f576c44c993e278fe9026b575/Untitled%204.png)

# request response object

![Untitled](Python%20Django%20Web%20Framework%209~11%208b3e0b4f576c44c993e278fe9026b575/Untitled%205.png)

첫번째 파라미터의 인자로 HttpRequest라고 하는 어떤 객체를 만드는데 사용자의 여라가지 정보가 패키징 되어 있다

위에 짠 코드를 이를 분석하게 되고

HttpResponse라는 객체를 응답해 주면 장고에 의해서(return) 사용자의 부라우저로 정보를 보내게 된다

```python
if request.method == 'GET':
    do_something()
elif request.method == 'POST':
    do_something_else()
```

request.method로 GET방식 또는 POST방식을 확인할 수 있다

F12→Network에서 확인을 해 보면 create 링크를 클릭할 때는 get방식으로, 텍스트를 입력할 때는 post방식으로 통신한 것을 알 수 있다

```python
def create(request):
	global nextId
	if request.method == 'GET':  #get방식과 post방식으로 들어왔을때의 처리를 다르게 해준다
		article = '''
			<form action="/create/" method="post"> #포스트 방식으로 바꿔준다
				<p><input type="text" name="title" placeholder="title"></p> <!--글을 입력할 수 있는 칸을 만들고 title로 이름, placeholder로 보이는 글자를 생성-->
				<p><textarea name="body" placeholder="body"></textarea></p> <!--text area로 여러 줄의 text를 입력-->
				<p><input type="submit"></p>
			</form>  <!--데이터를 원하는 패쓰로 보내주기위해서는 폼태그로 감싸줘야 한다-->
		'''
    return HttpResponse(HTMLTemplate(article))
	elif request.method == 'POST'
		title = request.POST['title'] #request.POST로 들어온 값에 이름을 붙여준다
		body = request.POST['body']
		newTopic = {"id":nextId, "title":title, "body":body #위쪽에 있는 토픽에다 추가해 줘야 한다 nextId
		topics.append(newTopic) #새로운 토픽을 기존의 톡픽들에 추가해준다
		url = '/read/'+str(nextId) #nextId 문자열로 바꿔줘야 잘 추가됨
		nextId = n
extId + 1  #계속 id가 4가 아닌 다음 수가 되게 해준다
		return redirect(url) #의미없는 값을 반환해 주는 것이 아닌 nextId가 갱신되기 이전의 url로 이동해 준다
```

```python
nextId = 4 #전역변수
```
[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
