---
layout: post
title: "reflow & repaint"
date: 2019-02-10 12:00:00
image: "https://user-images.githubusercontent.com/35126809/52481282-6863e280-2bf1-11e9-9a0b-2caa30b8841f.png"
description: 브라우저 동작 원리와 함꼐 reflow & repaint 알아보기.
category: "webdev"
tags:
  - browser
  - reflow
  - repaint
  - layout
introduction: reflow & repaint 알아보기.
---

[브라우저 동작원리](https://juunone.github.io/browser/)을 보신후 이 포스팅을 보길 권장합니다.<br />
웹이 렌더링 되는 과정중 reflow & repaint 에 대해 자세히 다루고자 한다.

---

## Reflow and Repaints

페이지를 한번 표시할때 리플로우가 발생한다. 그 후,<br />
렌더링 트리를 구성하는데 사용된 정보의 변화는 다음중 하나 또는 두개의 결과를 일으킨다.

- 렌더링 트리 일부(또는 전부)는 재 설정된 노드의 폭,높이 등이 다시 계산된다. <br />
  - 위 과정을 **Reflow** 또는 **Layout** 이라고 한다. (Webkit : layout , Gecko : reflow 라고 부른다)
  - 첫 페이지는 반드시 한 번 이상 리플로우가 일어난다.
- 레이아웃 수치에 영향을 주지 않는, (예:색상, 아웃라인, 배경 등)은 Reflow 과정이 생략된 **Repaint** 과정 이라고 부른다.

**리플로우와 리페인트는 부하가 높기 때문에, 사용자 경험(UX)에 부정적인 반응을 불러오고 UI의 반응이 느려지는 원인이 된다**


## Reflow 발생예시
생성된 노드의 레이아웃 수치(너비, 높이, 위치 등) 변경 시 영향 받은 모든 노드의(자신, 자식, 부모, 조상) 수치를 다시 계산하고(Recalculate), 
렌더 트리를 재생성하게된다.

```javascript
function reflow() { 
    document.getElementById('header').style.width = '400px'; 
    return false;   
}

```

![reflow](https://user-images.githubusercontent.com/35126809/52552170-a431be80-2e22-11e9-8094-37c75609017b.png)

1. 이벤트 발생
2. Recalcurate(스타일 수치 계산) 
3. Reflow
4. Repaint

## Repaint 발생예시
노드의 background-color, color, visibility 등의 스타일 변경 시에는 레이아웃 수치가 변경되지 않아서 Reflow 과정이 생략된 후 Repaint 과정만 일어나게 된다.


