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

*Demo*
- [react-socket-chat](https://github.com/juunone/react-socket-chat)

*References* 
- [WebSocket Chat App with Socket.io and React](https://itnext.io/building-a-node-js-websocket-chat-app-with-socket-io-and-react-473a0686d1e1)
- [react-express-socketio](https://codeburst.io/isomorphic-web-app-react-js-express-socket-io-e2f03a469cd3)
- [Naver D2 socket-io](https://d2.naver.com/helloworld/1336)

NextJS + SocketIO 로 구성해본 리액트 채팅 어플리케이션 제작 경험을 공유하고자 한다.
SocketIO 를 처음접하고 채팅목록과 채팅화면까지 구현하기의 일련의 과정을 보여준다.
React는 기본적으로 이해하고 프로젝트 구성까지 가능한 이해수준을 가진 전제하에 포스팅을 작성했습니다.

### socket-io ?
리액트