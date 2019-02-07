---
layout: post
title: "CSS 디버깅 절약을 위한 규칙"
date: 2018-10-11 21:00:00
image: "https://user-images.githubusercontent.com/35126809/52401126-50626500-2b04-11e9-8e1c-15a2bbf3ca4a.png"
description: CSS Architecture 의 한종류인 BEM 명명 규칙.
category: "css"
tags:
  - CSS
  - BEM
  - Architecture
introduction: 미세먼지팁::CSS BEM 방법론
---

웹은 정말 빠른 속도로 발전하고 있습니다.  
CSS는 훌륭한 "언어"라고는 할수 없지만 빠르게 진화했습니다.

대규모 어플리케이션이 많아지고 그에따라 CSS 활용 범위도 넓어져가는데,  
(잘못 작성된 CSS는 디버깅하는데 헬파티를 열어준다.)  
설계에 의미를 두지 않았던 CSS에도 다양한 방법론 생겨났습니다.

CSS방법론(BEM, SMACSS, OOCSS 등 더 많을수도..?) 존재하지만
이번 포스팅에서는 BEM에 관해서 적어볼까 합니다.

CSS 방법론은 아래와 같은 목표를 갖고 있습니다.

- 쉬운 유지보수
- 코드의 재사용성
- 확장성
- 클래스만으로 의미 추론

---

## CSS 명명규칙을 통해서 무엇을 해결하고자 하는가?

- selector의 이름만 보고 role을 알 수 있다.
- selector를 보기만 해도 어디에 사용할 수 있는지 알 수 있다.
- 클래스간의 관계는 클래스명만으로도 유추가 가능하다.

## BEM (Block, Element, Modifier) 정의

- [BEM](http://getbem.com/)은 Block Element Modifier의 약자
- [OOP(Object Oriented Programming)](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object-oriented_JS)와 유사한 형태를 띈다.
- 반드시 class명만 사용할 수 있다

### Block

> 곰돌이푸 베어브릭 가지고 쉽게 설명해보겠습니다.

- Block은 구성 요소(component)를 나타냅니다. (element 포함하고있는 컨테이너 요소)
- ex) content, navigation, header, footer

![곰돌이푸](https://user-images.githubusercontent.com/35126809/52403067-311a0680-2b09-11e9-9ac5-eb0ae401ad98.jpg "곰돌이푸베어브릭")

- 아래와 같이 component 스타일이 명명될 수 있습니다.

```css
.pooh {
}

//or

.pooh-brick {
}
```
