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

### Socket-io ?
JavaScript NodeJS 프레임워크 기반의 실시간 웹을 구현할 수 있는 기술이다.

<img alt="스크린샷 2019-10-24 15 46 11" src="https://user-images.githubusercontent.com/35126809/67460229-6c4b6e00-f675-11e9-8268-6e10a745e57c.png">

> 브라우저 지원범위 (2019.10.24 기준)  
> 출처 : https://github.com/socketio/socket.io

### NextJS ? 

[NextJS](https://nextjs.org/)는 SSR(Server Side Rendering) 서버에서 렌더링을
진행하는 웹 프레임워크이다.
SPA 환경을 좀 더 간편하게 구축하기위해 NextJS를 사용해 프로젝트를 구축했다.