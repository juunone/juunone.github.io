---
layout: post
title: "what is Redux-rematch?"
date: 2019-11-05 14:00:00
image: "https://user-images.githubusercontent.com/35126809/67179847-aff26d80-f412-11e9-9b4c-0c3a3248cc0a.jpg"
description: redux state management with redux-rematch
category: "tutorial"
tags:
  - redux
  - redux-rematch
  - rematch
introduction: redux-rematch 라이브러리를 이용한 redux 상태관리를 설명한다.
---

*References* 
- [redux-rematch github repo](https://github.com/rematch/rematch)
- [redux-rematch docs](https://rematch.github.io/rematch/#/)

## redux-rematch ?
리덕스의 복잡한 configuations를 조금더 간편하고,  
손쉽게 도와주는 redux-rematch 에 대해서 설명하고자 한다.  
action type에 대한 정의도 필요없고, 상태관리 함수 추가에 대한 공수를 줄일 수 있다.

## init
비즈니스 모델이 여러개 필요한경우 생성해서 스토어에 결합 시킬 수 있다.

```js
import { init } from '@rematch/core'
import * as models from './models'

const store = init({
    models,
})

export default store
```