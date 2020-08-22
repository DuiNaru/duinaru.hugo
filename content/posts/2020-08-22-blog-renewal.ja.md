+++
categories = ["blog"]
tags = ["hugo", "netlify", "netlify cms"]
title = "ブログをリニューアルしました"
permalink = "2020-08-22-blog-renewal"
date = 2020-08-22T13:19:47.589Z
description = "Github Pages + Jekyll から Netlify + Hugo + Netlify CMS にブログをリニューアルしました。"
i18n = "ja"

[[images]]
src = "/img/uploads/renewal.png"
alt = "post image"
+++
既存のブログはJekyllで作成し、Github Pagesでサービスしていましたが、Jekyllの多言語対応が不便でHugoに変えることにしました。合わせてNetlify + Netlify CMS も入れました。

この記事ではリニューアルの時に考えたことについて書こうと思います。

# [Hugo](https://gohugo.io/about/what-is-hugo/)

Hugoはgo言語で作成された静的サイトジェネレータです。一般的な動的サイトのようにサーバーからウェブページを作って見せることとは異なり、予め作成されたウェブページを見せることになります。サーバーのリソースを節約できることが魅力的です。

Jekyllも静的サイトジェネレータではありますが、Hugoは比較的に最新で、多言語対応も便利で選びました。

## 多言語対応 - Jekyll vs Hugo

### Jekyll

Jekyllで多言語対応は主にpluginでサポートされます。 

[開発と経験があるブログ- 作る](../2019-10-23-blog-with-development-and-experience/#作る)

polyglotやJekyll Multiple Languages Pluginなどがありますが、どちらもプラグインですので、他のプラグインと互換性を考えるなど、気を付けなければならないところがあります。

また、プラグインを使用しなく、Jekyllのコードを書いて作ってもいいですが、不便ということは変わらなさそうでした。

### Hugo

Hugoの場合は多言語がサポートされています。

[Hugo - Multilingual Mode](https://gohugo.io/content-management/multilingual/)

もともとサポートされているので、便利そうですね。

# [Netlify](https://www.netlify.com/)

NetlifyはCI/CDツールなのでデプロイまで自動化することができます。

Netlify CMSで投稿すると、Git repositoryにコミットされます。その直後にNetlifyでビルドされ、ウェブで見ることができるようになります。投稿するたびに手作業ビルドとデプロイ作業をしなくてもよくなります。

# [Netlify CMS](https://www.netlifycms.org/)

前はjekyll-adminのプラグインで管理してきましたが、hugoに変えることで他の方法を探さなければなりませんでした。

[Frontend Interfaces with Hugo](https://gohugo.io/tools/frontends/)

その中でNetlifyと併せて使いやすく見えるNetlify CMSを選びました。

投稿や修正、削除がGitで管理され、Gitのメリットも得られるようになります。投稿リストの確認や作成中のプレビューなどもあって便利です。

# Theme

テーマは色々ありますが、Hugo Future Imperfect Slimを入れてみました。

[Hugo Future Imperfect Slim](https://github.com/pacollins/hugo-future-imperfect-slim)

きれいでいいですし、アップデートも続いているので問題があっても対応が早そうです。

# ドメイン

<https://duinaru.netlify.app/>

ドメイン名はカスタムしなく、Netlifyデフォルトで設定しておきました。ドメインをカスタムすることになってもNetlifyにドメイン追加設定をすればいいですので、運営しながら考えてみようと思います。

次は、リニューアルの過程や悩みなどについて投稿してみます。