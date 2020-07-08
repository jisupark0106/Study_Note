# node.js

## 동기 vs 비동기

### 동기 함수

일반적인 프로그래밍 (JAVA, python)은 일을 하는 순서대로 작동을 한다.
우선적인 일이 끝나야 다음 일을 한다.

`10분 -> 1시간 -> 5분 -> 2시간`

### 비동기 함수

비동기방식은 인간의 효율적인 일처리 방식을 닮아있다.
worker들에게 동시에 때려서 먼저 끝나는 worker부터 처리

일들의 순서가 눈으로 보는 것처럼 이루어지지 않음

```javascript
var fs = require("fs");
//비동기
fs.readFile();
//동기
fs.readFileSync();
```

실행해보면 readFile이 오래걸리기 때문에 순서의 변경이 있음을 알 수 있다. 하지만, readFileSync는 순서대로 나오는 것을 알 수 있다
-> 하드 디스크의 접속이 오래걸림

## Callback Function

나중에 할 일을 callback함수에 넣었구나


```javascript
afunc(function(){
    bfunc(function(){
        cfnuc(function(){
            dfunc(funcion(){
                //hell...유지보수에 문제
            })
        })
    })
})

```

## tips

터미널 , bash -- command line
초기화될때 프로그램이 어디에 설치되어있는지 가져온다

---

# Web Application

### 브라우저에 naver.com 접속 시 일어나는 일

- https://www.naver.com 클릭

- client가 server에 `request` 날림

- server 해당 `request` 확인 후 `response` 날림

- client는 `response` 받아서 브라우저에 따라 화면 띄운다.

https://developer.mozilla.org/ko/docs/Web/HTTP/Messages

프로토콜 header부분에 정보가 포함되어있다.

# http 기본 서버 구축하기

```javascript
var http = require("http");
console.log(`server is starting...`);
http
  .createServer(function (req, res) {
    var body = "hello Server";
    res.setHeader("Content-Type", "text/plain;charset=utf-8");
    res.end(body);
  })
  .listen(3000);
```

`req` 사용자의 요청
`res` 사용자에게 응답

다양한 페이지가 존재하기 때문에 http 단일 서버만 이용하기에 무리가 있다. 다른 방법 필요~~

# npm

https://www.npmjs.com/
library 검색할 수 있는 웹사이트

#### multer 파일 업로드

https://www.npmjs.com/package/multer

#### request package

https://www.npmjs.com/package/request

`npm init` -- package.json 파일 생김
npm i request

```json
 "dependencies": {
    "request": "^2.88.2"
  }
```

package json request 의존성 생김

## 공공 데이터 활용

https://www.data.go.kr/index.do

- 내가 원하는 데이터 선택한 후 xml, json 등 데이터 형식을 파악한다
- 데이터 url을 request 모듈을 통해 body 받아올 수 있도록
- npm 모듈을 통해서 적절하게 parsing 도와주니까 모듈 찾아보기

#### json {"key: value"}

## ✨공공데이터 받아오는 연습하기

# Database [mysql]

mysql에서 connection 해주고 npm 모듈 다운 받을 것
`npm install mysql`
https://www.npmjs.com/package/mysql

- 내가 접근 가능한 사용자인지 connection 정보를 통해 서버 접속할 수 있도록
- 엑셀처럼 데이터 저장된다.

## 🎈 데이터베이스 스키마 만드는 방법 공부하기

# Express 사용해보기

- Java - Spring
- node.js - express

### Framework

개발자 업무의 영역에서 반복되어지는 핵심 기능들을

이미 구현해서 개발자가 편하게 사용할 수 있도록 한다.

### express 사용해보기

https://expressjs.com/ko/starter/installing.html

=> `npm install express`

서버 동작 확인해보기 sample 코드

```javascript
const express = require("express");
const app = express();

app.get("/", function (req, res) {
  res.send("Hello World");
});

app.listen(3000);
```

## 기본 라우팅

```javascript
app.method('/path',function (req, res)){
  res.send('Hello World!');
}
```

#### method

- get
- post
- put
- delete

# Front end (ejs)

`npm install ejs`

- view 엔진으로 사용한다. 선언해주기

```javascript
//아래 경로로 view를 가져다 쓸 것 입니다. __dirname 현재 경로
app.set("views", __dirname + "/views");
//ejs 말고도 다른 엔진도 있음
app.set("view engine", "ejs");
```

같은 공유기 서버구동 확인방법
cmd> ipconfig
ip주소 확인 후 localhost 자리에 넣어준다.
같은 공유기에 연결되어 있다면 다른 기기에서 확인 가능

#### jquery 사용방법

https://code.jquery.com/

최근에는 react 로 사용하는 경우도 있지만
금융권 같은 경우들은 사용하지 않는 경우들이 많음

jquery도 공부해보고 react도 해보는 경험 가져보시오

# Ajax 통신

server <--- data

ajax 통신 : request, response를 날린다.

- jquery에서 ajax

```javascript
$.ajax({
  url: "",
  type: "POST",
  data: {},
  success: function (data) {},
});
```

- request 모듈이랑 비슷함
- url -- 어디에?
- type -- http methos
- data -- request data

```javascript
//서버 데이터 설정 허용
app.use(express.json());
app.use(express.urlencoded({ extended: false }));
```

# Asset 저장하기

#### layout 테마 사이트 
https://themeforest.net/

express에 기능 사용하는 거 알려줘야함

```javascript
const path = require("path");
app.use(express.static(path.join(__dirname, "public"))); //to use static asset
```

그리고 public 폴더 추가해주기

그 안에 디자인, 폰트 등 asset들 넣어줌

### 정리

- public/css,js,font asset 파일들 존재
- views/layout.ejs 파일들 존재
- expressServer.js에 라우팅 , res.render("layout.ejs")

#### .gitignore
https://www.toptal.com/developers/gitignore
