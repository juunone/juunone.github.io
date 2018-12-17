---
layout: post
title: "CMS 에디터툴 Dynamic contents editor : DCE 제품정의"
date: 2018-02-08 14:00:00
image: "https://s3.ap-northeast-2.amazonaws.com/thugstorage/images/postcover/dcecover2.jpg"
description: DCE(Dynamic contents editor) 랜딩페이지 제작을 목적으로 개발된 CMS 툴입니다.
category: "project"
tags:
  - CMS
  - CRM
  - Landing
  - Editor
introduction: DCE(Dynamic contents editor) 프로젝트를 진행하면서 생각해본 제품정의를 공유하고자 합니다.
---

# DCE(Dynamic contents editor) 제품정의

## **들어가며**

본 문서는 인수인계 목적이 아닌
개발이 완료된 제품에 대한 이해를 돕기위해 제작된 개발 정의서입니다.<br />
부디 도움이 되길 바랄 뿐입니다. 그럼 스타뜨!

## **배경**

---

처음 문제는 **_Targetbook_** 으로부터 시작되었습니다.<br />
문제의 배경은 광고를 집행하고 운영하는 AE 분들에 의해서 발의되었습니다.<br />
이번 사례의 경우, 아래와 같이 배경이 정리 될 수 있다.

- 페이스북과 동일한 [캔버스](https://www.facebook.com/business/learn/facebook-create-ad-canvas-ads) 기능을 사용할 수 있을것
- 랜딩페이지 유입을 높이는 것
- ~~재밌겠다~~

## **문제정의**

---

효과적으로 빠르게 광고 랜딩페이지 제작 목적을 띄고있는 페이스북의 [캔버스](https://www.facebook.com/business/learn/facebook-create-ad-canvas-ads)<br />
기능이 타겟북 어드민내에 존재하지 않는다.

- 페이스북 캔버스 Dependency
- 기존 타겟북 랜딩페이지와의 차별성을 가지고 insight 도출

## **예상 및 해결**

---

예상 설정은 상황에 따라 생략할 수 있는 부분이며<br />
오히려 탐색의 범위를 좁히는 결과를 낳기도 하기 때문에 목적 설정 과정에 비해 중요도가 높지 않다고 생각된다.(주관적)<br />
어쨌든 랜딩 페이지 목적을 띈 CMS를 개발해야 되는 입장으로서
페이스북에 종속되어있는 캔버스 기능을 한땀한땀 개발하기에는 시간 및 유지보수에
큰 문제점을 느끼고 **Targetbook+iMs** 모두에서 사용할 수 있는 이른바<br />
~~DbodyCMS~~(초기명칭) = **DCE** 제품이 개발된다.

## **Use case diagram**

![다이어그램](https://s3.ap-northeast-2.amazonaws.com/thugstorage/images/post/DCE_FE.png)

## **마치며**

제품을 개발하며 제일 주안점을 두었던 부분은 **_속도, 편의성, 확장성_** 이였다.

- 웹사이트 랜딩페이지의 속도는 무조건적으로 빨라야한다.
- HTML,CSS 를 모르는 사람도 사용할 수 있어야한다.
- 자사의 여러 서비스들에 적용이 가능해야한다.
