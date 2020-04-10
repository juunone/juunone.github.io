---
layout: post
title: "AWS amplify deploy with github-actions"
date: 2020-04-07 15:00:00
image: "https://user-images.githubusercontent.com/58495926/72698520-e5c8fe80-3b87-11ea-833a-07a177f049f3.png"
description: github actions를 통해 aws amplifty CLI로 배포하기
category: "webdev"
tags:
  - github
  - github action
  - deploy
  - aws
  - amplify
introduction: aws amplify CLI deploy with github-actions and post message to slack
---

## github-action?
기존에 존재하는 CI/CD 서비스들이 많이 존재하는데 예를들어,  
travisCI, circleCI 등 써드파티앱등을 깃헙내에 연동해서 사용할수 있었다.
그 서비스들을 이용해서 테스트,빌드 등을 배포하거나 테스트할수 있는 환경을 (e.g. aws, gcp)
Github이 `action`이라는 이름으로 서비스를 제공하는것이다.
프로젝트 repo안에 action 탭을 확인가능하다.
