+++
categories = ["aws"]
tags = ["aws", "event"]
title = "AWS summit online japan 2021 2일차 후기"
permalink = "2021-05-17-aws-summit-online-day2"
date = 2021-05-17T14:52:17.254Z
description = "2021년 5월 11일 부터 2일간 개최된 AWS summit online japan에 참가해보았습니다."
i18n = "ko"

[[images]]
src = "/img/uploads/aws-summit-online-2021.png"
alt = "aws summit online japan"
+++
매년 열리는 AWS summit,  작년부터 COVID-19로 인해 온라인으로 진행되고 있습니다.

올해는 5월 12일 부터 13일까지 양일간에 걸쳐 라이브로 진행되고 31일 까지 개최됩니다.

[aws summit online japan](https://aws.amazon.com/jp/events/summits/online/japan/)

필자는 라이브로 진행되는 양일간에 걸쳐 참가하였으며, 각 내용을 정리해 볼까 합니다.

# 2일차

2일차에는 개발이나 서버리스 등 실제로 만들어 보는 내용에 관련된 세션 주로 참가하였습니다.

마지막 날 인만큼, 특별강연까지 기나긴 하루였습니다.

## 기조강연

전날과는 다르게 영어로 대부분이 진행되며, 일본어 자막이 지원되었습니다. AWS의 신념에 대해 말하기 시작해 다양한 서비스를 소개하고 AWS 커스텀 실리콘에 대해 이야기를 하면서 중간중간 관계회사분들의 이야기를 들을 수 있었습니다.

1일차에 purpose-built databases에 대해 인상깊었는데, 이번에는 기조강연에서 언급하면서 데이터의 중요성을 강조한 것도 인상깊었습니다.

## 세션

총 9개의 세션에 참가, 점심먹기도 힘들었던 기억이 나네요.

### 웹, 모바일어플리케이션 개발을 가속시키는 AWS Amplify

제목 그대로의 AWS Amplify 소개 세션

이전에 GraphQL이 궁금해서 찾아보던중 알게된 서비스, 인프라의 대부분을 간략화시켜서 설정하고, 백엔드와 프론드엔드단의 코드를 생성해 주기도 하는 등 어플리케이션의 개발을 편리하게 해주는 서비스입니다.

이번에 Admin UI가 생겼다고도 하네요.

### AWS Amplify와 AWS AppSync를 사용한 풀스택 어플리케이션 개발

이전의 AWS Amplify에 이어서 AWS AppSync를 이용한 구체적인 개발 사례 소개 세션입니다.

AWS Amplify와 AWS AppSync를 사용한 아키텍쳐를 바탕으로 인증방법, Graph API 작성 방법, 리액트 코드 자동 생성 등 비디오 채팅 어플리케이션 개발을 예제로 설명합니다.

이건 한번 만들어 보고 싶어지는 군요.

### AWS에서의 네트워크 & 어플리케이션 보호의 단계

이번 세션에서는 시큐리티 위주의 설명이 주로 되었습니다.

SYN floods나 SQL인젝션, 크롤러 등 보안에 위험이 될 수 있는 요소를 AWS에서는 AWS Network Firewall, AWS WAF, AWS Shield Advanced로 보호할 수 있다고 합니다.

각 서비스를 이용한 구성과 설명이 있는 세션이였습니다.

### AWS로 시작하는 Infrastructure as Code

제목을 부터 AWS CloudFormation이 느껴지는 세션이였습니다. 역시나 AWS CloudFormation의 설명이 있더군요.

AWS 환경을 코드로 관리하는 것에 대한 설명, 필요성, 목적 등에 대해 이야기 한 다음에 CloudFormation의 설명과 예제로 이어졌습니다.

다만, yml로 알고 있던 CloudFormation을 Cloud Develop Kit을 이용하여 프로그래밍 언어로 작성 할 수 있다고 하는 점이 신선했습니다.

변수 같이 프로그래밍 쪽 요소를 넣어서 구성하기에 편해보였습니다.

### 이노베이션을 가속하는 서버리스 어플리케이션의 이벤트 구동형 아키텍쳐

어제도 보았던 서버리스! 지나칠 수 없지요.

AWS Lambda에 대한 설명을 포함해, 서버리스 어플리케이션의 필요성 그리고 이벤트 구동형 아키텍쳐에 대한 설명이 있었습니다.

이벤트 구동형 아키텍쳐에 대한 내용을 처음 들어서 생소하였지만, 흥미로웠네요.

그리고 Lambda와 관련 서비스에 대한 설명도 있었습니다.

### AWS에서의 컨테이너 워크로드에 대해, 다양한 빌딩블록의 선택지

컨테이너의 필요성과 이점에 대해 궁금한 부분이 있어서 참석해보았습니다.

AWS의 컨테이너 관련 서비스인 AWS Fargate, EKS, ECS, ECR 등에 대한 설명과 ECS/EKS의 비교에 대한 이야기도 있었습니다.

그리고, AWS CodePipeline등을 이용한 자동화 방법에 대한 설명도 있었네요.

### 컨테이너, 서버리스를 사용하면 모던 어플리케이션이 되는가?

제목부터 범상치 않은 기운이 느껴질 듯 한 세션, 설계의 중요성을 깨닫는 세션이였습니다.

예제 어플리케이션의 문제점을 하나하나 집어가면서 관련 서비스를 소개하고 해결해 나가는 방식으로 이해를 돕는 진행방식이 인상적 이였습니다.

제목과 같이 생각하고 있던 분들이라면 추천하고 싶은 세션입니다.

### 내일부터 시작할 수 있다!! Chaos Engineering의 시작 가이드

Chaos Engineering?? 뭘까요? 참가!!

> 시스템이 서비스 환경에서 불안정한 상태를 버틸 수 있게 하는 것

위의 내용의 근거를 마련하는 것이 Chaos Engineering라고 합니다.

아무리 철저히 테스트를 하더라도 서비스중에는 터지기 마련이고, 그에 대한 준비가 필요하다는 것은 엔지니어라면 느끼고 계시겠지요.

이를 실제로 해 보는 것이 Chaos Engineering! 간단하게 말하면 서비스 중인 인스턴스를 정지시켜서 어떤 변화가 생기는지 살펴보는 방법이라고 합니다.

현재의 시스템이 Well-Architected 되어있고, Observabilty가 되어있는 상태에서 도입해야 가치가 있다고 하는 군요.

> Without observability,\
> you don't have chaos engineering.\
> You just have Chaos.\
> \
> Charity Majors\
> Cofounder/CTO honeycomb.io

세션의 일부를 인용해봤습니다. Chaos Engineering를 해보겠다고 Chaos를 해서는 안되겠지요.

제목처럼 내일부터 시작할 수 있을지는 잘 모르겠지만, 흥미로운 세션이였습니다.

### Open-source observability at AWS - 가관측성을 지탱하는 OSS와 AWS의 "지금"을 알자

2일차 마지막 세션이자, 바로 전 세션에서 들은 observability 에 대한 세션입니다.

엔지니어라면 디버그에서의 스택 트레이스, 에러 로그 분석 등 무언가 문제가 발생하면 원인을 찾기위해 이것저것 살펴보고는 하지요.

그들은 문자라는 것을 읽어야 이해가 되며, 전체를 보기 위해서는 많은 시간을 필요로 합니다.

이것을 한 눈에 알아볼 수 있게 할수 있다면, 많은 시간을 절약할 수 있겠지요.

이를 도와주는 AWS의 서비스와 OSS, 그리고 이 둘을 합친 서비스를 소개하는 세션이였습니다.

OSS인 Fluentd, Fluentd Bit, Prometheus, Cortex, OpenTelemetry과 AWS X-Ray. FireLens for ECS/EKS, Amazon Managed Service for Prometheus/Grafana , AWS Distro for OpenTelemetry 등 가관측성을 도와주는 서비스에 관심을 가지시고 계신다면, 한번쯤 참가해볼만 세션이라고 생각되었습니다.

## 특별강연

AWS summit online의 막을 내리는 시간, 미래는 어떻게 바뀌고 바뀌어 나갈건지 등에 대해 관계자들이 나와서 서로 이야기를 주고받는 방식으로 진행되었습니다.

# 2일차 후기

흥미로운 주제가 많아서 이것저것 듣다보니 2일이 지났습니다.

알고 있던 것도 새로운 부분을 알게 되고, 모르는 것은 더욱 더 알아가게 되는 시간이였습니다. 고민거리에 대한 답을 생각해보기도 하고, 재미있어 보이는 것들도 있었네요.

COVID-19로 인해, 현장에서 직접 듣거나 파트너 부스를 돌아다니며 오프라인 활동을 못 하게 된 점은 어쩔 수 없다고 생각되며, 다음에는 오프라인에서 만나 볼 수 있었으면 하고 바랍니다.