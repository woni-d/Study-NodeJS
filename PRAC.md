server_test ~ 정리
=====
  
### path 모듈
url을 이용할 때엔 무조건 path 모듈을 이용함  
운영체제에 따라 다른 url을 신경쓸 필요 없음  
  
### app.listen 메소드
http.listen과 같이 포트에서 요청을 대기  
  
익스프레스의 장점
-----
  
### 1. 미들웨어
요청에 대한 응답 과정 중간에 껴서 어떠한 동작을 해주는 프로그램  
익스프레스가 응답을 보내기 전, 미들웨어가 지정한 동작을 수행  
  
#### 미들웨어의 종류
__*express.static*__ : 정적 파일의 기본 경로를 정함  
__*Morgan*__ : 익스프레스 프레임워크가 동작하면서 나오는 메시지들을 콘솔에 표시  
__*Compression*__ : 이름처럼 페이지를 압축해서 전송  
__*Session*__  
__*Body-parser*__ : 폼에서 전송되는 POST 값 사용  
__*Cookie-parser*__  
__*Method-override*__ : REST API에서 PUT과 DELETE 메소드를 사용할 수 있도록 함  
__*Cors*__ : 크로스오리진(다른 도메인 간의 AJAX 요청) 가능케 함  
__*Multer*__ : 파일업로드를 할 때 주로 쓰임  
  
### 2. 라우팅
클라이언트에서 보내는 주소에 따라 다른 처리를 하는 것  
__*REST API*__  
  
사용법 : `app[REST메소드]('주소', 콜백함수)`  
`app.get`, `app.post`, `app.put`, `app.delete` 메소드를 사용  
  
#### 주소 작성법
1. 정규 표현식
2. :(콜론)을 사용한 와일드카드

예를 들어 app.get('/post/:id')인 경우 /post/a도 적용되고, /post/b도 적용됨  
  
*와일드카드*를 사용할 때는 *순서*가 중요  

```javascript
app.get('/post/:id', () => {});
app.get('/post/a', () => {});
```
=> /post/a에 요청이 왔을 때 두 번째 라우터에 걸릴거라고 생각하지만,  
/post/:id에 먼저 걸리고 /post/a의 콜백 함수는 실행되지 않는다.  
따라서 와일드카드 라우터는 항상 다른 라우터들보다 뒤에 적어주는 것이 좋다.  
  
이렇게 app에 계속 이벤트 리스너처럼 연결하면 되는데,  
라우팅은 반복되는 부분이 많기 때문에 주로 모듈로 분리해서 사용함  
  