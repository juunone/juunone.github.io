---
layout: post
title: "페이스북 픽셀 가이드"
date: 2017-11-16 21:00:00
image: "https://s3.ap-northeast-2.amazonaws.com/thugstorage/images/postcover/facebookpixelcover.jpg"
description: 태깅을 하기전 알아야 될 제일 기본적인 항목들.
category: "guide"
tags:
  - Facebook
  - Tagging
  - Pixel
  - Event
introduction: Facebook 픽셀은 회원님의 웹사이트에서 사람들이 취한 행동을 파악하여 광고의 성과를 측정할 수 있는 분석 도구입니다.
---

## 픽셀이란?

Facebook 픽셀은 회원님의 웹사이트에서 사람들이 취한 행동을 파악하여 광고의 성과를 측정할 수 있는 분석 도구입니다.<br />
픽셀 데이터를 사용하여 다음을 할 수 있습니다.

- 적절한 대상에게 광고 노출
  - 신규 고객, 웹사이트의 특정 페이지를 방문한 사람, 원하는 행동을 취한 사람 등 비즈니스에 적절한 타겟을 찾을수있고,<br />
    유사 타겟을 만들어 우수 고객과 유사한 타겟에 더 많이 도달하게 가능하다. [자세한내용](https://www.facebook.com/business/help/666509013483225?helpref=faq_content#)
- 광고 타겟 구축
  - 자동 입찰을 설정하여 제품 구매 등 중요한 행동을 취할 가능성이 높은 사람을 타게팅할 수 있다.
- 더 많은 Facebook 광고 도구 활용
  - 광고의 직접적인 성과를 확인하여 광고가 얼마나 성공적이었는지 파악 가능하며,<br />
    전환 및 매출과 같은 정보를 확인할 수 있습니다.[픽셀 대시보드](https://www.facebook.com/business/help/898185560232180?helpref=faq_content#)

---

## 표준이벤트와 맞춤이벤트의 차이

웹사이트에서 행동이 발생하면 Facebook 픽셀을 `이벤트`로 기록합니다. 이벤트를 사용하면 웹사이트에 알맞은 코드를 추가하여 전환을 추적하고, 전환에 맞게 광고를 최적화하고, 알맞은 타겟을 만들 수 있습니다.

이벤트는 **표준 이벤트**와 **맞춤 이벤트** 두 가지로 카테고리로 분류됩니다.

- 표준 이벤트
  - 광고 상품에 걸쳐 파악 및 지원되는 행동입니다.<br />
    예를 들어 카탈로그 판매 광고 및 Facebook 픽셀 웹사이트 클릭 광고에서 표준 이벤트를 활용할 수 있다.
- 맞춤 이벤트
  - 맞춤 이벤트는 표준 이벤트에서 벗어나는 행동이다. 표준이 아닌 행동을 추적하고자 할 때 맞춤 이벤트를 만들고 사용할 수 있다

---

## 표준 이벤트 모범 사례

### 표준이벤트 종류

![표준이벤트종류](https://s3.ap-northeast-2.amazonaws.com/thugstorage/images/post/%E1%84%91%E1%85%AD%E1%84%8C%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3.png)

### 표준 이벤트의 예

표준 이벤트가 설치된 웹사이트 코드의 형태는 아래의 예를 참조하세요.<br />
Facebook 픽셀 기본 코드: Facebook 픽셀 코드는 아래 그림과 같은 형태입니다. 단, 픽셀 ID는 *예시*입니다.

![표준이벤트예1](https://s3.ap-northeast-2.amazonaws.com/thugstorage/images/post/%E1%84%91%E1%85%AD%E1%84%8C%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%8B%E1%85%A8.jpg)

![표준이벤트예2](https://s3.ap-northeast-2.amazonaws.com/thugstorage/images/post/%E1%84%91%E1%85%AD%E1%84%8C%E1%85%AE%E1%86%AB%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%8B%E1%85%A82.jpg)

---

## 픽셀 지원 도구

Chrome 웹브라우저에 접속후 Chrome 웹스토어로 이동하여, Facebook Pixel Helper 를 검색합니다.

![픽셀지원1](https://s3.ap-northeast-2.amazonaws.com/thugstorage/images/post/%E1%84%91%E1%85%B5%E1%86%A8%E1%84%89%E1%85%A6%E1%86%AF%E1%84%8C%E1%85%B5%E1%84%8B%E1%85%AF%E1%86%AB1.png "픽셀지원1")

### 픽셀 확인

- 픽셀 지원 도구를 설치한 후 주소창의 픽셀 지원 도구를 클릭합니다.
- 팝업을 보고 해당 페이지에 픽셀이 있는지, 픽셀이 제대로 설정되었는지 확인합니다.

![픽셀지원2](https://s3.ap-northeast-2.amazonaws.com/thugstorage/images/post/%E1%84%91%E1%85%B5%E1%86%A8%E1%84%89%E1%85%A6%E1%86%AF%E1%84%8C%E1%85%B5%E1%84%8B%E1%85%AF%E1%86%AB2.png "픽셀지원2")