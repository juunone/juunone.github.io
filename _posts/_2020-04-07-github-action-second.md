---
layout: post
title: "AWS amplify deploy with github-actions(2)"
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

## Github-action

깃헙액션을 사용한 경험에 대해 추가로 작성해보고자 한다.  
[지난 깃헙액션 첫번째 글](https://juunone.github.io/github-action/)  

지난번 github-actions의 yml 설정에 한계에 부딪혀 배포자동화를 못하고 있던중,  
추가 수정과 삽질을 통해 드디어 github-actions를 통해 CI/CD 가 완성됐다.

**AS-IS**: `sh`을 통한 `AWS amplify CLI` 배포.  
**TO-BE**: github-actions를 통한 `push` 트리거시 `AWS amplify CLI github-actions`를 통해 배포.

결론적으로 수정된 파일을 단 2개, `workflow yml` 과 `package.json`  
