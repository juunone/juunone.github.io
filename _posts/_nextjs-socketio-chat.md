---
layout: post
title: "NextJS, SocketIO chat application"
date: 2019-10-11 12:00:00
image: "https://user-images.githubusercontent.com/35126809/67179847-aff26d80-f412-11e9-9b4c-0c3a3248cc0a.jpg"
description: Make chat application with NextJS and socketIO
category: "tutorial"
tags:
  - nextjs
  - socket-io
  - react
introduction: NextJS 와 socketIO 를 이용해 채팅 구현.
---

*참조* 
- [Redux-saga github](https://github.com/redux-saga/redux-saga)
- [Redux-saga tutorial](https://redux-saga.js.org/docs/introduction/BeginnerTutorial.html)

개인적으로 진행하던 익명 투표 시스템의 비동기 부분을 담당하던
redux-thunk를 redux-saga로 교체한 코드들에 대한 변경점을 공유하고자 한다.

### what is redux-middleware?
- 리덕스 미들웨어는 리덕스액션이 리듀서에 도착하기 전 가로채는 행동을 하는 코드이다.