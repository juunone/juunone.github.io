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

## Actions

먼저 [github actions marketplace](https://github.com/marketplace/actions) 에서 2개의 액션들을 사용했다.

첫번째
- (AWS amplify actions)[https://github.com/marketplace/actions/amplify-cli-action]   

기존에 사용하고있던 `aws amplify`를 그대로 계승해서 사용하길 원했고, S3 및 Cloudfront 까지 배포를 해주기 때문에
매우 편리한 서비스다.  
`amplify CLI`를 사용할수 있는 액션이 마켓에 존재했고, 해당 모듈을 사용해서 액션을 만들수 있었다.
여기서 한가지 문제점이 있었는데, 

`amplify-cli-action@0.2.0` 버전에서는 arguments 옵션이 지원되지 않아
Cloudfront까지 배포가 안된다는 점이였다. ㅠㅠ

다른 모듈은 마땅히 사용할만한게 존재하지 않았고, 결국 해당 repo에 feature request로 issue를 생성했다.  
개발자가 대응이 빨라 `amplify-cli-action@0.2.1`에서 바로 사용 가능하게 배포됐다.