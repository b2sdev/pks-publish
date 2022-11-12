---
id: 99q7prq3t1a4apfogsjzjuq
title: Node.js
desc: ''
updated: 1668223808476
created: 1532060251000
---

https://nodejs.org/ko/about/

비동기 이벤트 주도 JavaScript 런타임

npm init ~ project 생성

npm install ~ save express multer ~ 패키지 설치

server.js 생성 + 라우터 설정 - index.html

$node server.js 서버 실행

$express-generator 설치
npm install express-generator -g

$express-generator로 express 프로젝트 생성

express [appname] --ejs
cd [appname]
npm install

$생성한 프로젝트 실행
npm start

$서버에 접속
http://localhost:3000/

$클라이언트 사이드
views/index.ejs 수정 - Ajax로 파일 전송

$서버 사이드
routes/server.js 생성 후 POST 처리
app.js에서 server.js router/use 설정