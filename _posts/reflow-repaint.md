---
layout: post
title: "reflow & repaint"
date: 2019-02-07 18:00:00
image: "https://user-images.githubusercontent.com/35126809/52481282-6863e280-2bf1-11e9-9a0b-2caa30b8841f.png"
description: 브라우저 동작 원리와 함꼐 reflow & repaint 알아보기.
category: "webdev"
tags:
  - browser
  - reflow
  - repaint
introduction: 브라우저 동작 원리와 함께 reflow & repaint 알아보기.
---

웹사이트는 어떻게 보여줄까?
웹개발자들 이라면 한번쯤 들어봤을 브라우저 렌더링 과정과<br />reflow & repaint에 대해서
좀더 자세히 다뤄보고자 여러 문서들을 기반으로 포스팅을 작성하게됐다.

---

## 브라우저의 렌더링 과정

렌더링은 화면에 컨텐츠를 그리는 과정으로, 브라우저들은 각자의 렌더링 엔진으로 이를 구현했다.
크롬과 사파리는 "Webkit 엔진"을 사용하고, 파이어폭스는 "Gecko 엔진"을 사용한다.

**브라우저 렌더링 과정**<br />
![브라우저렌더링](http://www.phpied.com/files/reflow/render.png)

출처 : [http://www.phpied.com/rendering-repaint-reflowrelayout-restyle/](http://www.phpied.com/rendering-repaint-reflowrelayout-restyle/)

1. 불러오기(Load)<br />
   로더(Loader)가 서버로부터 전달 받는 리소스 스트림을 읽는 과정.
   읽으면서 어떤 파일인지, 데이터인지 파일을 다운로드할 것인지 등을 결정한다.

2. 파싱 (Parsing)<br />
   렌더링 엔진은 HTML/XML 문서를 파싱하고 "콘텐츠 트리" 내부에서 태그를 DOM 노드로 변환하고,<br />
   외부 CSS 파일을 포함하여 스타일 요소도 파싱한다.

3. 렌더링 트리 만들기<br />
   DOM 트리는 내용을 저장하는 트리로 자바스크립트에서 접근가능한 DOM객체를 쓸 때 이용하고,<br />
   파싱해서 얻은 스타일 정보와 HTML 표시 규칙은 ['렌더 트리'](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/)라고 부르는 또 다른 트리를 생성한다.<br />
   ['렌더 트리'](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/)는 색상과 면적 같은 시각적 속성 정보를 가지고 있다.<br />
   (렌더 트리 생성시 필요없는 head, title, body태그등이 없고 display:none 처럼 DOM에 있지만 여과가 필요한 부분들을 제외해준다)

4. Layout:렌더 트리 배치(Reflow)<br />
   생성된 렌더 트리에서는 크기 위치등이 없기 때문에 각 노드가 화면에 정확한 위치에 표시되도록 배치하고 과정이다.<br />
   _Webkit : layout , Gecko : reflow 라고 부른다_

5. Paint:그리기(Repaint)<br />
   배치된 노드들을 visibility, outline, background-color, color와 같이 시각적 속성에 해당하는 형상을 만들어 내는 그리기 과정이다.

- 렌더링 엔진은 순차적으로 수행하지 않고 점진적으로 수행한다. 기다리는 동시에 받은 내용의 일부를 먼저 화면에 표시하는 것이다.<br />
- TABLE의 경우는 기본적으로 점진적 렌더링이 적용되지 않는다. (table-layout:fixed일 경우에만 점진적 렌더링이 적용)<br />
- 그래서 table-layout:auto 보다 table-layout:fixed가 성능에 더 좋다.

**[Webkit 엔진 동작과정]**
![webkit](https://d2.naver.com/content/images/2015/06/helloworld-59361-3.png)

**[Gecko 엔진 동작과정]**
![gecko](https://d2.naver.com/content/images/2015/06/helloworld-59361-4.png)

출처 : [https://d2.naver.com/helloworld/59361](https://d2.naver.com/helloworld/59361)
