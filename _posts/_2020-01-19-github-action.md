---
layout: post
title: "Deploy with github-action"
date: 2020-01-19 13:00:00
image: "https://user-images.githubusercontent.com/58495926/72698520-e5c8fe80-3b87-11ea-833a-07a177f049f3.png"
description: github action을 통한 클라이언트 배포
category: "webdev"
tags:
  - github
  - github action
  - deploy
introduction: deplot client side by aws amplify CLI with github action
---

## github-action?
기존에 존재하는 CI/CD 서비스들이 많이 존재하는데 예를들어,  
travisCI, circleCI 등 써드파티앱등을 깃헙내에 연동해서 사용할수 있었다.
그 서비스들을 이용해서 테스트,빌드 등을 배포하거나 테스트할수 있는 환경을 (e.g. aws, gcp)
Github이 `action`이라는 이름으로 서비스를 제공하는것이다.
프로젝트 repo안에 action 탭을 확인가능하다.

## what to do
깃헙액션을 사용한 경험에 대해 작성해보고자 한다.  
일단 `aws amplify` 로 기존에 프론트를 배포하고있었다.  
amplify CLI를 통해서 수동배포를 하고있었는데 이 부분을
깃헙액션을 통해 CI/CD 를 구축해보고자 한다.

[amplify-cli-action](https://github.com/marketplace/actions/amplify-cli-action) 이라는
깃헙 액션 워크플로우 템플릿을 base로 yml을 작성했다.

깃헙액션 탭에 들어가면 기본적으로 많이쓰이는 템플릿을 제공하는데 그외에도 [github-action marketplace](https://github.com/marketplace/actions/) 에 가면 유저들이 만들어 놓은 많은 템플릿도 제공하고있다. 이중 자신이 필요한 CI/CD 베이스를 가져와 사용할 수 있다.

