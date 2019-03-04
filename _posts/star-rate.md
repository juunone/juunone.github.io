---
layout: post
title: "별점 평가 컴포넌트"
date: 2019-02-28 10:00:00
image: "https://user-images.githubusercontent.com/35126809/53712500-7de3c980-3e8a-11e9-8358-23cd94011aeb.png"
description: 별점 평가 컴포넌트 작성
category: "project"
tags:
  - browser
  - reflow
  - repaint
  - layout
introduction: 별점 한개도 주기 아까울때.
---

[별점 평가 컴포넌트](https://github.com/juunone/star-rate)에 가면 데모버전 확인 가능합니다.

---

## 목적

- 영화를 본 후 평점 별점 반개도 주기 아까울때.
- 웹 & 모바일 모두 사용 가능해야 한다.

위 두가지 목적을 가지고 제작된 컴포넌트 입니다.

**시간적 제한을 가지고 제작되어서, 코드내 잡음 주의!**

##

생성된 노드의 레이아웃 수치(너비, 높이, 위치 등) 변경 시 영향 받은 모든 노드의(자신, 자식, 부모, 조상) 수치를 다시 계산하고(Recalculate),
렌더 트리를 재생성하게된다.

```javascript
function reflow() {
  document.getElementById("header").style.width = "400px";
  return false;
}
```

![reflow](https://user-images.githubusercontent.com/35126809/52552170-a431be80-2e22-11e9-8094-37c75609017b.png)

> 블로그 포스팅 넓이 변경시

1. 이벤트 발생
2. Recalcurate(스타일 수치 계산)
3. Reflow
4. Repaint

## Repaint 발생예시

노드의 background-color, color, visibility 등의 스타일 변경 시에는 레이아웃 수치가 변경되지 않아서 Reflow 과정이 생략된 후 Repaint 과정만 일어나게 된다.

```javascript
function repaint() {
  document.getElementById("post").style.backgroundColor = "black";
  return false;
}
```

![repaint](https://user-images.githubusercontent.com/35126809/52552669-63d34000-2e24-11e9-995f-40fdc1073902.png)

> 블로그 포스팅 배경색 변경시

1. 이벤트 발생
2. Recalcurate(스타일 수치 계산)
3. Repaint (Reflow 생략)

## Reflow & Repaint triggers

- 노드의 추가 또는 제거
- 노드의 위치 이동 및 애니메이션
- 스타일 속성의 약간의 변화를 위해 스타일 시트 추가
- 요소의 크기 변경.(예시 : margin, padding, border, width, height, 등..)
- 윈도우 리사이징 및 폰트 크기 변경, 그리고 스크롤 등 사용자 액션
- display: none(리플로우와 리페인트) 또는 visibility: hidden(리페인트) 등과 같은 노드 숨김처리

## Reflow 최적화

- 인라인 스타일 배제
- 클래스에 따른 스타일 변화시 DOM 의 제일 하위 자식에게 할당
- position:absolute:fixed 활용
  - absolute,fixed 사용시 전체 노드안에서 해당 노드가 분리되 독립적으로 reflow & repaint가 발생한다.
- table-layout 최소 사용, 모두 로드되고 계산된후에야 적용되는 속성. table-layout:fixed 추천.
- style 객체 속성 cssText 사용 권장.

```javascript
//비추천
function calc() {
  var el = document.getElementById("post");
  el.style.backgroundColor = "black";
  el.style.width = "50px";
  el.style.height = "50px";
  return false;
}

//추천
function calc() {
  var el = document.getElementById("post");
  el.style.cssText = "background:black;width:50px;height:50px;";
  return false;
}
```

reflow & repaint 는 렌더링의 필수 과정이다.<br />
그 과정속에서 일어나는 변화를 감지하고 개선하는 노력이 필요하다.
사용자 경험에 도움이 될 수 있다.
