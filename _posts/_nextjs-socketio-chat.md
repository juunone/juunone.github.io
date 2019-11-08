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
NextJS를 사용하지 않는다면 CRA를 이용해 react-router 보일러플레이트를 설치하는 방법도 있다.

### server.js

express를 이용해 서버를 구축하고, socket.io 에 연결시켰다.  
db는 따로 만들지 않고, mockup 데이터를 사용하였다.

```js
const express = require('express')
const http = require('http')
const socketIO = require('socket.io')
const port = 3001;
const app = express()
const server = http.createServer(app)
const io = socketIO(server)

io.on('connection', socket => {
  // console.log('connected!');

  socket.on('send message', (user, target, msg, isPicture) => {
    const copyData = [...data];
    const newDate = + new Date();

    copyData.forEach(v => {
      if(v.id === user){
        v.contents.forEach(key => {
          if(key.name === target){
            key.endedAt = newDate;
            key.messages.push({
              user: user,
              message: isPicture === true ? '' : msg,
              picture: isPicture === true ? msg : '',
              isRead: true
            })
          }
        });
      } else if (v.id === target) {
        v.contents.forEach(key => {
          if(key.name === user){
            key.endedAt = newDate;
            key.messages.push({
              user: user,
              message: isPicture === true ? '' : msg,
              picture: isPicture === true ? msg : '',
              isRead: false
            })
          }
        });
      }
    })

    const targetData = copyData.filter(v => v.id === user)[0];
    const targetMessages = targetData ? targetData.contents.filter(value => value.name === target)[0].messages : [];
    io.sockets.emit('receive message', targetMessages);

    const reduceTargetData = copyData.filter(v => v.id === target)[0];
    socket.broadcast.emit('receive data', reduceTargetData);
  })

  socket.on('receive data', (user) => {
    const newData = data.filter(v => v.id === user)[0];
    io.sockets.to(socket.id).emit('receive data', newData);
  });

  socket.on('receive message', (user, target) => {
    const targetData = data.filter(v => v.id === user)[0];
    const targetMessages = targetData ? targetData.contents.filter(value => value.name === target)[0].messages : [];
    io.sockets.emit('receive message', targetMessages);
  });

  socket.on('read message', (user, target) => {
    const copyData = [...data];
    const userIdx = copyData.findIndex(v => v.id === user);
    if(userIdx !== -1){
      const mappingData = copyData[userIdx].contents.map(key => {
        if(key.name === target){
          key.messages.forEach(value => {
            if(value.user === target) value.isRead = true;
          }) 
        }
        return key
      });
      copyData[userIdx].contents = mappingData;
    }

    const newData = copyData.filter(v => v.id === user)[0];
    io.sockets.to(socket.id).emit('receive data', newData);
  });

  socket.on('disconnect', () => {
    console.log('user disconnected!')
  })
})

server.listen(port, () => console.log(`Listening on port ${port}`))
```

`io.sockets()` 괄호안에 들어가는 문자는 클라이언트와 서버사이드가 주고받는 메소드명이다.  
`emit` 은 메소드를 실행시키고, `on` 은 클라이언트에서 해당 메소드가 `emit`되면 서버사이드에서 실행되는 메소드다.  
`io.sockets.to(socket.id).emit('receive data', newData)` 는 현재 연결된 id에만 'receive data'를 실행한다.  
`socket.broadcast.emit('receive data', reduceTargetData)` 는 현재 연결된 id를 제외한 다른 모든 id들에 'receive data'를 실행한다.


## socket-context.js

context-api 를 이용해서 접속시 한번씩만 클라이언트에 소켓을 연결해준다.
아래와 같이 3001번 서버와 `socketIOClient` 메소드를 통해 연결된다.

```js
import React from 'react'
import socketIOClient from "socket.io-client";

const socket = socketIOClient('localhost:3001');

export const SocketContext = React.createContext(socket);
```