+++
categories = ["blog"]
tags = ["netlify", "netlify cms"]
title = "Netlify CMS + Netlifyでブログサイト管理とデプロイを自動化"
permalink = "2020-09-02-make-blog-with-netlifycms-netlify"
date = 2020-09-02T16:00:24.529Z
i18n = "ja"

[[images]]
src = "/img/uploads/netlifycms.png"
alt = "netlifycms+netlify"
+++
静的サイトジェネレータで構築したブログはmarkdown形式で管理され、投稿の度にビルドとデプロイをしなければなりません。これをしやすくするためにNetlify CMSとNetlifyを入れました。

# [Netlify CMS](https://www.netlifycms.org/)

Netlify CMSやForestry.ioのように静的サイトジェネレータのcmsは色々あります。

[Frontend Interfaces with Hugo](https://gohugo.io/tools/frontends/)

どのサービスでも管理の良さは同じと思いますが、Netlifyと併せて使いやすそうなNetlify CMSを入れました。

## 特徴

[netlify cms - overview](https://www.netlifycms.org/docs/intro/)

ウェブベース、多くの静的サイトジェネレータのサポートなどの特徴があります。

特にGitベースで管理することがいいと思います。投稿するとcommitされ、投稿完了にpull request、修正で新しくcommitされることですが、プログラミングを似ていますね。投稿の完了するまでbranchを別に作って管理することもできます。

## インストール

### テンプレートから始める

[netlify cms - Start with a Template](https://www.netlifycms.org/docs/start-with-a-template/)

最も早く始める方法です。予めサイトを作成しておく必要がなく、全ての設定が終わっているテンプレートから始めることです。

新しく始めようとする方や早く見てみたいと思う方にお勧めです。

### 既存のサイトに追加

[netlify cms - Add to Your Site](https://www.netlifycms.org/docs/add-to-your-site/)

創ってあったブログサイトがある方や初めから設定していきたい方は直接インストールすることもできます。

#### ファイル作成

管理ページと設定ファイルを作ります。ファイルの格納場所が以下になります。

> | These generators ...                       | store static files in |
> | ------------------------------------------ | --------------------- |
> | Jekyll, GitBook                            | / (project root)      |
> | Hugo, Gatsby, Nuxt, Gridsome, Zola, Sapper | /static               |
> | Next                                       | /public               |
> | Hexo, Middleman, Jigsaw                    | /source               |
> | Spike                                      | /views                |
> | Wyam                                       | /input                |
> | Pelican                                    | /content              |
> | VuePress                                   | /.vuepress/public     |
> | Elmstatic                                  | /_site                |
> | 11ty                                       | /_site                |
> | preact-cli                                 | /src/static           |
>
> https://www.netlifycms.org/docs/add-to-your-site/#app-file-structure

静的サイトジェネレータ別にstaticなウェブページがデプロイされる場所です。hugoで構築したブログですので、staticのフォルダーに格納すればいいです。

上記のフォルダーにadminというフォルダーを作成し、次の二つのファイルを作成します。

> index.html
>
> ```html
> <!doctype html>
> <html>
> <head>
>   <meta charset="utf-8" />
>   <meta name="viewport" content="width=device-width, initial-scale=1.0" />
>   <title>Content Manager</title>
> </head>
> <body>
>   <!-- Include the script that builds the page and powers Netlify CMS -->
>   <script src="https://unpkg.com/netlify-cms@^2.0.0/dist/netlify-cms.js"></script>
>   <script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
>   <script>
>   if (window.netlifyIdentity) {
>     window.netlifyIdentity.on("init", user => {
>       if (!user) {
>         window.netlifyIdentity.on("login", () => {
>           document.location.href = "/admin/";
>         });
>       }
>     });
>   }
> </script>
> </body>
> </html>
> ```
>
> config.yml
>
> ```yaml
> backend:
>   name: git-gateway
>   branch: master # Branch to update (optional; defaults to master)
>
> # This line should *not* be indented
> publish_mode: editorial_workflow
>
> # These lines should *not* be indented
> media_folder: "/static/img/uploads" # Media files will be stored in the repo under static/images/uploads
> public_folder: "/img/uploads" # The src attribute for uploaded media will begin with /images/uploads
>
> collections:
>   - name: "blog" # Used in routes, e.g., /admin/collections/blog
>     label: "Blog" # Used in the UI
>     folder: "_posts/blog" # The path to the folder where the documents are stored
>     create: true # Allow users to create new documents in this collection
>     slug: "{{year}}-{{month}}-{{day}}-{{slug}}" # Filename template, e.g., YYYY-MM-DD-title.md
>     fields: # The fields for each document, usually in front matter
>       - {label: "Layout", name: "layout", widget: "hidden", default: "blog"}
>       - {label: "Title", name: "title", widget: "string"}
>       - {label: "Publish Date", name: "date", widget: "datetime"}
>       - {label: "Featured Image", name: "thumbnail", widget: "image"}
>       - {label: "Rating (scale of 1-5)", name: "rating", widget: "number"}
>       - {label: "Body", name: "body", widget: "markdown"}
> ```
>
> https://www.netlifycms.org/docs/add-to-your-site/#configuration

index.htmlはNetlfiy CMSにアクセスするためのページで、config.ymlは設定ファイルです。

設定項目は色々ありますので、[公式ホームページ](https://www.netlifycms.org/docs/add-to-your-site/#configuration)から確認できます。

#### 確認

netlfiy cmsのページを確認します。

ローカルから`hugo -serve`で駆動し、http://localhost:1313/adminにアクセスするとログイン画面が表示されます。

![netlfy cms login page](https://duinaru.netlify.app/1b34d952-263b-4cee-8ea3-f5d8b84a9fb2)

#### Netlifyの設定ファイルの作成

Netlifyにデプロイするための設定ファイルと作成します。ブログサイトのルートにnetlify.tomlのファイルを作成します。該当のファイルにNetlifyの設定ができ、ビルドコマンドや環境変数などを指定することができます。

```toml
#/my-blog/netlify.toml

[build]
publish = "public"
command = "hugo --gc --minify"

[context.production.environment]
HUGO_VERSION = "0.74.3"
HUGO_ENV = "production"
HUGO_ENABLEGITINFO = "true"

[context.split1]
command = "hugo --gc --minify --enableGitInfo"

[context.split1.environment]
HUGO_VERSION = "0.74.3"
HUGO_ENV = "production"

[context.deploy-preview]
command = "hugo --gc --minify --buildFuture -b $DEPLOY_PRIME_URL"

[context.deploy-preview.environment]
HUGO_VERSION = "0.74.3"

[context.branch-deploy]
command = "hugo --gc --minify -b $DEPLOY_PRIME_URL"

[context.branch-deploy.environment]
HUGO_VERSION = "0.74.3"

[context.next.environment]
HUGO_ENABLEGITINFO = "true"
```

#### Repository作成

Netlifyは[GitHub](https://github.com/)、[GitLab](https://about.gitlab.com/)、[Bitbucket ](https://bitbucket.org/)のRepositoryからデプロイすることができます。今まで創ったブログサイトをRepositoryにPushしましょう。

# Netlify

## Netlifyデプロイ

### ﻿ログイン

Netlifyにアクセスし、ログインします。

<https://www.netlify.com/>

New site from Gitのボタンで新規サイトを作成します。初めてアカウントを作成した場合は作成後、新規サイト作成画面が表示される場合もあります。

![New site from Git](https://duinaru.netlify.app/f4b5a5ce-bddd-48f0-ba75-9e8e052940ad)

### サイト作成

ブログRepositoryがあるGitを設定します。

![create a new site](https://duinaru.netlify.app/8435fdfb-608e-40d8-89e1-7eaea5e0dbf2)

GitのボタンをクリックするとRepositoryを選択する画面が表示されますので、ブログサイトのRepositoryを選びます。

![choose repository](https://duinaru.netlify.app/f6478c53-12be-41b6-936b-8bba56585359)

次はBranchやビルドコマンドを設定します。デフォルトで設定されていますのでこのまま進みましょう。

![deploy site](https://duinaru.netlify.app/75c6d7a9-22f3-46b5-8eb0-33c1be370a5a)

Deploy siteボタンをクリックし、Siteを作成します。

### 作成確認

筆者の場合はHugo Future Imperfect Slimをcloneで入れまして、画像のようにFailedと失敗しました。submoduleで入れた場合は成功すると思います。

![create site fail](https://duinaru.netlify.app/fb065094-b280-4082-b196-1673cb50f71b)

Submodule Pathがないというエラーで、.gitmodulesのファイルをブログサイトのルートに作成し、Pushしました。

> .gitmodules
>
> ```
> [submodule "hugo-future-imperfect-slim"]
>     path = themes/hugo-future-imperfect-slim
>     url = https://github.com/pacollins/hugo-future-imperfect-slim.git
> ```

成功すると以下のようにPublishedが確認できます。

![create site success](https://duinaru.netlify.app/14fa5dec-b0f1-4a0e-befa-e8b27e09c34a)

## サイト確認

画面に表示されたURLにアクセスすればブログサイトが確認できます。

![main page](https://duinaru.netlify.app/908f4ee6-ae68-4c56-a41a-15633e8a1127)

## Netlify設定

Netlify CMSの使用のため、Netlifyでログイン関連の設定をします。

### Identity

メニューからIdentityをEnableします。この機能を使用することによって、会員登録などの認証機能が使えるようになります。

![enable identity](https://duinaru.netlify.app/5652e7d0-0368-4c43-9368-d641a0840f73)

### Enable Git Gateway

Netlify CMSでGitを処理するためにGit GatewayをEnableします。Settings - Identityで、Services - Git GatewayにあるEnable Git Gatewayのボタンをクリックします。

![enable git gateway](https://duinaru.netlify.app/719a14a4-a135-498b-9638-5c1897d6cb67)

### 招待専用に設定

Settings - Identity - RegistrationからEditボタンをクリックし、Invite onlyを選びます。この設定で管理者の招待のみでアカウントを登録することになります。

![registration invite only](https://duinaru.netlify.app/cd2f980c-0432-48c0-abf2-06d6b863e6da)

### アカウント登録

アカウントを登録します。

Invite usersをクリックし、e-mailを記入してSendボタンをクリックします。

![invite_users](https://duinaru.netlify.app/f331e6a8-b589-4280-8e37-9074997f2753)

記入したe-mailに認証メールが届きます。メールのAccept the inviteをクリックするとブログサイトに遷移されます。

クリックしたURLは以下と似ていますが、adminを入れて修正し、CMSページになるようにします。

変更前

```
https://trusting-curran-e13b73.netlify.app/#invite_token=-W5a_7Eao-GCIMVEpr97Vw
```

変更後

```
https://trusting-curran-e13b73.netlify.app/admin#invite_token=-W5a_7Eao-GCIMVEpr97Vw
```

そうしたらパスワードを設定する画面が出ます。

![sign up](https://duinaru.netlify.app/7a2bbe95-190f-465c-964f-9d86979372d9)

# 確認

パスワードを設定した後、自動的にログインされてNetlify CMSのメイン画面が表示されます。

![img](https://duinaru.netlify.app/fcbf6cba-2239-418f-82ee-40d813865261)

New Blogで投稿するなどのNetlify CMSの機能を使用できるようになりました。

# 感想

終わりました。Netlify CMSを設定しておけば、ウェブで直接投稿できて便利です。

しかし、日本語や韓国語のタイピングがたまに無視されることがあります。英語は問題ないことでCMSが英語に合わせて作られているかもしれません。

画像アップロードも便利でいいですが、タイピングは工夫の必要がありそうです。