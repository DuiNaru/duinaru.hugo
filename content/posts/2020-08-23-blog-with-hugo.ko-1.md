+++
categories = ["blog"]
tags = ["hugo"]
title = "Hugoでブログサイト立ち上げ"
permalink = "2020-08-23-blog-with-hugo"
date = 2020-08-23T09:34:31.309Z
i18n = "ko"

[[images]]
src = "/img/uploads/hugo-logo-wide.svg"
alt = "hugo image"
+++
Hugoでブログサイトを立ち上げてみました。Hugoをインストールし、テーマを入れることですぐに創れます。

# Hugo

## インストール

まずは、Hugoをインストールします。

[Install Hugo](https://gohugo.io/getting-started/installing/)

Hugoはベーシックバージョンとextendedバージョンの二つがあります。extendedバージョンはSCSS/SASSをサポートし、SCSS/SASSを使おうとしたらextendedバージョンのインストールが必要のようです。

> [And Now: Hugo Pipes!](https://gohugo.io/news/0.43-relnotes/#notes)
>
> Hugo is now released with two binary version: One with and one without SCSS/SASS support. At the time of writing, this is only available in the binaries on the GitHub release page. Brew, Snap builds etc. will come. But note that you **only need the extended version if you want to edit SCSS**. For your CI server, or if you don’t use SCSS, you will most likely want the non-extended version.

今回で入れるテーマがSCSSを使っているようで、extendedバージョンをインストールします。

### パッケージマネージャーインストール

Windows環境でインストールしまして、[chocolatey](https://chocolatey.org/)を利用し、インストールしました。別の環境でのインストールは[Install Hugo](https://gohugo.io/getting-started/installing/)を参考してください。

> [Installing Chocolatey](https://chocolatey.org/install)
>
> ```powershell
> Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
> ```

管理者権限でPowershellに上記のコマンドーを実行させます。セキュリティー設定があるかということでBypassを設定してインストールするらしいです。

`choco`や`choco -?`でインストールされたことを確認したら、Hugoをインストールします。

### Hugoのインストール

### [Install Hugo - Chocolatey (Windows)](https://gohugo.io/getting-started/installing/#chocolatey-windows)

> ```powershell
> choco install hugo-extended -confirm
> ```

`hugo version`でインストールされたことを確認できます。0.74.3バージョンがインストールされましたね。

```powershell
Hugo Static Site Generator v0.74.3/extended windows/amd64
```

# ブログサイト作成

ブログサイトを作成するディレクトリで、次のコマンドーを実行すれば作成完了です。`new-site-name`はブログサイトが格納されるフォルダー名で変更できます。

```powershell
hugo new site new-site-name
```

指定したフォルダーが作成され、hugoのストラクチャーでできていることが確認できます。

## ビルド

ブログサイトのフォルダーで`hugo`コマンドを実行するとpublicというフォルダーにビルドされたファイルが格納されます。このフォルダーが実際のブログサイトになります。

```powershell
hugo

                   | EN
-------------------+-----
  Pages            |  3
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0
```

## 確認

そして、`hugo serve` でローカル環境でもブログサイトが確認できます。

```powershell
hugo serve

                   | EN
-------------------+-----
  Pages            |  3
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  0
  Sitemaps         |  1
  Cleaned          |  0

Built in 6 ms
Watching for changes in C:\Hugo\Sites\my-blog\{archetypes,content,data,layouts,static}
Watching for config changes in C:\Hugo\Sites\my-blog\config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

上記のコマンドーを実行し、<http://localhost:1313/> にアクセスすれば、白い画面が表示されることが確認できます。

# テーマのインストール

何もない画面から創り上げてもいいですが、公開されている様々なテーマがありますので、使いましょう。

[Hugo Themes](https://themes.gohugo.io/)

一つ選んでインストールしてみます。

## ダウンロード

[Hugo Future Imperfect Slim](https://themes.gohugo.io/hugo-future-imperfect-slim/)

Hugo Future Imperfect Slimというテーマをダウンロードしました。テーマはブログサイトディレクトリのthemesフォルダーに入れます。

```powershell
cd C:\Hugo\Sites\my-blog\themes
git clone https://github.com/pacollins/hugo-future-imperfect-slim.git
```

他のテーマであっても、themesのフォルダーに入れればいいです。

あとは、テーマの設定をすれば完成です。

# 設定

テーマの設定はテーマごとに異なりますが、全ての設定はブログサイトディレクトリの下、config.tomlのファイルに設定します。該当ファイルはhugoの設定ファイルで、ブログサイトのタイトルや使用するテーマの設定などを指定できます。

筆者の場合は[Hugo Future Imperfect Slim](https://themes.gohugo.io/hugo-future-imperfect-slim/) を入れましたので、下記のように設定しました。

> [Hugo Future Imperfect Slim - config.toml](https://github.com/pacollins/hugo-future-imperfect-slim/wiki/config.toml)
>
> ```toml
> baseurl                 = "example.com"
> DefaultContentLanguage  = "en"
> title                   = "Hugo Future Imperfect Slim"
> theme                   = "hugo-future-imperfect-slim"
> paginate                = 3
> disqusShortname         = ""
> googleAnalytics         = ""
> pluralizeListTitles     = false
> disableLanguages        = []
>
> [markup.goldmark.renderer]
>   unsafe                = true
>
> [outputs]
>   home                  = ["html", "json"]
>   
> [params]
>   enableCDN             = false
>   cssFiles              = ["default"]
>   jsFiles               = ["default"]
>   highlightjs           = true
>   highlightjsTheme      = "default"
>   highlightjsLang       = []
>   viewMorePostsLink     = "/blog/"
>   readingTime           = true
>   imageStrech           = ""
>   socialShare           = ["twitter", "facebook", "reddit", "linkedin", "pinterest", "email"]
>   
> [params.meta]
> 	description         = "A theme by HTML5 UP, ported by Julio Pescador. Slimmed and enhanced by Patrick Collins. Multilingual by StatnMap. Powered by Hugo."
> 	author              = "HTML5UP and Hugo"
> 	favicon             = false
> 	svg                 = true
> 	faviconVersion      = "1"
> 	msColor             = "#ffffff"
> 	iOSColor            = "#ffffff"
>     
> [params.header]
> 	navbarTitle         = "Future Imperfect"
> 	dynamicTitles       = true
> 	searchMenu          = true
> 	shareMenu           = true
> 	languageMenu        = true
>
> [params.intro]
> 	header                = "Hugo Future Imperfect Slim"
> 	paragraph             = "Another fine, responsive site template by <a href='http://html5up.net'>HTML5 UP</a>."
> 	rssIntro              = true
> 	socialIntro           = true
> 	hideWhenSingleColumn  = false
> 	alwaysOnHomepage      = false
>
> 	[params.intro.pic]
> 		src                 = "/img/main/logo.jpg"
> 		shape               = "circle"
> 		width               = ""
> 		alt                 = "Hugo Future Imperfect Slim"
>         
> [params.sidebar]
>   about               = "This theme was developed for Hugo static site generator."
>   postAmount          = 5
>   categories          = true
>   categoriesByCount   = true
>  
> [params.footer]
>   rssFooter           = true
>   socialFooter        = true
>   
> [params.staticman]
>   enabled             = false
>   api                 = ""  # No Trailing Slash
>   gitProvider         = "github"
>   username            = ""
>   repo                = ""
>   branch              = ""
>
>   [params.staticman.recaptcha]
>     siteKey           = ""
>     encryptedKey      = ""
>     
> [menu]
>
> 	[[menu.main]]
> 		name              = "Home"
> 		identifier        = "home"
> 		url               = "/"
> 		pre               = "<i class='fa fa-home'></i>"
> 		weight            = 1
>
> 	[[menu.main]]
> 		name              = "About"
> 		identifier        = "about"
> 		url               = "/about/"
> 		pre               = "<i class='far fa-id-card'></i>"
> 		weight            = 2
>         
> [Languages]
>
> 	[Languages.en]
> 		LanguageCode        = "en"
> 		LanguageName        = "English"
> 		weight              = 1
>
> 	[Languages.fr]
> 		LanguageCode        = "fr"
> 		LanguageName        = "Français"
> 		title               = "Hugo Future Imperfect Slim en français"
> 		description         = "Un thème par HTML5 UP, porté par Julio Pescador. Simplifié et amélioré par Patrick Collins. Multilingue par StatnMap. Propulsé par Hugo."
> 		weight              = 2
>
> 		[[Languages.fr.menu.main]]
> 		name              = "Accueil"
> 		identifier        = "home"
> 		url               = "/"
> 		pre               = "<i class='fas fa-home'></i>"
> 		weight            = 1
>         
> [social]
> 	# Coding Communities
> 	github                = "pacollins/hugo-future-imperfect-slim"
> 	gitlab                = ""
> 	stackoverflow         = "" # User Number
> 	bitbucket             = ""
> ```

## 確認

必要な設定をした後、`hugo serve`を実行して<http://localhost:1313/>にアクセスしてみましょう。

![hugo-future-imperfect-slim main](/img/uploads/hugo-future-imperfect-slim.png)

テーマが適用慣れていることが確認できます。しかし、投稿がないので一つ作成してみましょう。

# 投稿

下記のようにコマンドを実行します。投稿で作るファイルはmarkdown形式で、ファイル一つがポスト一つになります。

```powershell
hugo new posts/new-post.md
```

content/postsの下にnew-post.mdというファイルが作成されていることを確認できます。投稿は`hugo new` のコマンドでしてもいいですし、.mdファイルを直接作成してもいいです。コマンドで作成する場合はdraftをtrueに設定して作られますので、次のコマンドでブログサイトを起動しましょう。

```powershell
hugo serve -D
```

<http://localhost:1313/> にアクセスすれば投稿されていることが確認できます。

![new post](/img/uploads/hugo-future-imperfect-slim_new-post.png)

投稿はそのファイルに内容を書くことでできます。

しかし、ファイルを一個づつ修正したり管理することは不便さがつきものです。そこで、CMSを入れれば、投稿や管理がしやすくなるので、次はそれについて投稿しようと思います。