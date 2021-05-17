+++
categories = ["aws"]
tags = ["aws", "event"]
title = "AWS summit online japan 2021 2日目"
permalink = "2021-05-17-aws-summit-online-day2"
date = 2021-05-17T15:09:39.914Z
description = "2021年5月11日から2日間、AWS summit online japanに参加しました。"
i18n = "ja"

[[images]]
src = "/img/uploads/aws-summit-online-2021.png"
alt = "aws summit online japan"
+++
毎年開かれるAWS summit、去年からはCOVID-19でオンライン配信されている状況です。

今年は5月12日から13日まで両日の間にライブ配信され、31日まで開催されます。

[aws summit online japan](https://aws.amazon.com/jp/events/summits/online/japan/)

筆者はライブで開催される両日に参加し、各内容をまとめたいと思います。

# 2日目

2日目には開発やサーバーレスなど、実際に創ってみる内容に関するセッションに参加しました。

最後の日であって、特別講演まで長い一日でした。

## 基調講演

1日目とは異なり、ほとんどが英語で進めて日本語の字幕がサポートされました。AWSのテネットについて話し始め、多様なサービスを紹介し、AWSのカスタムシリコンについて語りながら、関係会社の方々の話を聞くことができました。

前日のpurpose-built databasesが印象的でありましたが、今回は基調講演で話されて、データの重要性を強調したことも印象深かったです。

## セッション

9つのセッションに参加、お昼も厳しかった覚えがあります。

### Web・モバイルアプリ開発を加速させる AWS Amplify

タイトルのままのAWS Amplify紹介セッション

以前、GraphQLが気になって探したら見つけたサービスでもあります。インフラの大半を簡略化して設定し、バックエンドとフロントエンドのコードを自動的に生成するなど、アプリケーションの開発をしやすくするサービスです。

今回はAdmin UIができたという話もありました。

### AWS Amplify と AWS AppSync を使ったフルスタックアプリケーションの開発

AWS Amplifyに続き、AWS AppSyncを使った具体的な開発事例の紹介セッションです。

AWS AmplifyとAWS AppSyncを利用したアーキテクチャをもとに、認証方法、Graph APIの作成方法、reactコードの自動生成などについてビデオチャットアプリケーションの開発サンプルを見せながら説明されました。

これは創ってみたくなりますね。

### AWS におけるネットワーク＆アプリケーション保護のすすめ

今回のセッションでは主にセキュリティーの説明でした。

SYN floodsやSQL injection、クローラーなど、セキュリティーを害する要素をAWSではAWS Network Firewall、AWS WAF、AWS Shield Advancedでアプリケーションを保護することができるようです。

### AWS で始める Infrastructure as Code

タイトルからAWS CloudFormationが思いつくセッションで参加、思った通りにAWS CloudFormationの説明がありました。

AWSの環境をコードで管理することについて説明と必要性、目的などを話し、CloudFormationの紹介とサンプルが続きました。

ただ、ymlで知っていたCloudFormationが、Cloud Develop Kitを利用してプログラミング言語で作成できるということも新しかったです。

変数などプログラミングの考え方で構築しやすく見えましたね。

### イノベーションを加速するサーバーレスアプリケーションのイベント駆動アーキテクチャ

1日目でも見たサーバーレス！見過ごせません。

AWS Lambdaについて説明し、サーバーレスアプリケーションの必要性、そしてイベント駆動アーキテクチャの説明がありました。

イベント駆動アーキテクチャについては初めて聞きましたが、興味深い内容でした。

そして、Lambdaと関わるサービスの話もありました。

### AWS でのコンテナワークロードにおける多様なビルディングブロックの選択肢

普段、コンテナの必要性と利点について疑問をもっていましたので、参加しました。

AWSのコンテナサービスであるAWS Fargate、EKS、ECS、ECRなどについての説明とECS/EKSを比較した話もありました。

AWS CodePipelineを利用し、自動化する方法の説明もあったセッションです。

### コンテナ・サーバーレスを使えばモダンアプリケーションになりますか？

タイトルから迫力が感じられそうなセッション、設計の重要性を気づかせるセッションでした。

サンプルアプリケーションについて問題点を話しながら、関連サービスを紹介し、解決していくプレゼンテーションの進め方で理解しやすかったです。

タイトルのように考えた方にはお勧めです。

### 明日から始める!! Chaos Engineering 始め方ガイド

Chaos Engineering？？なんでしょう。参加！

> システムが本番環境での不安定な状況を耐えることができる

上記の内容に自信を構築するため実施する実験がChaos Engineeringというらしいです。

徹底的にテストを行っても、サービス中にはなにかの問題が起こりえます。対策の必要性はエンジニアなら感じているでしょう。

これを実際にやってみることがChaos Engineering！簡単に言うとサービス中のインスタンスを落としてどうなるか確認する実験です。

現在のシステムがWell-ArchitectedになっていてObservabiltyがある状況で実行してこそ価値があると言われます。

> Without observability,\
> you don't have chaos engineering.\
> You just have Chaos.\
> \
> Charity Majors\
> Cofounder/CTO honeycomb.io

セッションの一部を引用しました。Chaos EngineeringであってChaosになってはならないでしょう。

タイトルのように明日から始めるかは疑問ですが、興味深いセッションでした。

### Open-source observability at AWS − 可観測性を支える OSS と AWS の『いま』を知る

2日目の最後のセッションで、observabilityについてのセッションです。

エンジニアならデバッグでスタックトレース、エラーログ分析など、何かの不具合対応で原因調査で調べたりするでしょう。

それらは文字ということを読み、全体を理解するまでは多くの時間を必要とします。

一目で理解できれば、多くの時間を節約することもできるでしょう。

これを手伝ってくれるAWSのサービスとOSSが紹介されたセッションです。

OSSのFluentd、Fluentd Bit、Prometheus、Cortex、OpenTelemetryとAWS X-Ray、FireLens for ECS/EKS、Amazon Managed Service for Prometheus/Grafana、AWS Distro for OpenTelemetryなど、可観測性を支えるサービスの興味を持っていたら、参加してみる価値はあると考えられました。

## 特別講演

AWS summit onlineの幕を閉じる時間です。未来はどう変わり、どう変えていくのかについて関係者の議論の形で進みました。

# 2日目感想

興味深いテーマを多く、あっという間に2日が過ぎました。

知っていることでも新しい面を知り、知らなかったことは知っていく時間でした。悩みについて答えを考えたり面白そうなことも多くありました。

COVID-19で現場で聞いたらパートナーブースを周ることはできなく仕方なく思います。願わくは次はオフラインで会えしょう。