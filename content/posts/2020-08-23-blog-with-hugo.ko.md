+++
categories = ["blog"]
tags = ["hugo"]
title = "Hugo로 블로그 만들기"
permalink = "2020-08-23-blog-with-hugo"
date = 2020-08-23T05:20:06.624Z
description = "Hugo를 사용하여 블로그 만들어 봅시다."
i18n = "ko"

[[images]]
src = "/img/uploads/hugo-logo-wide.svg"
alt = "hugo image"
+++
Hugo를 사용하여 블로그를 만들어 보았습니다. Hugo를 설치하고 테마를 적용하는 것만으로도 바로 만들 수 있습니다.

# Hugo

## 설치

우선 Hugo를 설치해 주어야 합니다.

[Install Hugo](https://gohugo.io/getting-started/installing/)

Hugo는 기본 버전과 extended버전이 있습니다. extended버전은 SCSS/SASS를 지원하는 버전으로, SCSS/SASS를 만들어 사용하고자 하실 분은 extended버전으로 설치해야 한다네요.

> [And Now: Hugo Pipes!](https://gohugo.io/news/0.43-relnotes/#notes)
>
> Hugo is now released with two binary version: One with and one without SCSS/SASS support. At the time of writing, this is only available in the binaries on the GitHub release page. Brew, Snap builds etc. will come. But note that you **only need the extended version if you want to edit SCSS**. For your CI server, or if you don’t use SCSS, you will most likely want the non-extended version.

단순히 테마만 적용해서 사용할 생각이라서 기본 버전으로 설치해 주었습니다. 물론 extended버전도 상관없지만요.

### 패키지 매니저 설치

Windows환경에 설치할 생각이라 [chocolatey](https://chocolatey.org/)를 이용해서 설치해 주었습니다.

> [Installing Chocolatey](https://chocolatey.org/install)
>
> ```powershell
> Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
> ```

관리자 권한으로 Powershell에 해당 명령어를 실행시키면 됩니다. 보안 설정이 있을 수 있으니 Bypass 설정을 한다는 군요.

`choco`나 `choco -?`로 설치된 것을 확인하였으면, Hugo를 설치하면 됩니다.

### Hugo 설치

> [Install Hugo - Chocolatey (Windows)](https://gohugo.io/getting-started/installing/#chocolatey-windows)
>
> ```powershell
> choco install hugo -confirm
> ```

`hugo version`으로 설치된 것을 확인 할 수 있습니다. 0.74.3버전이 설치되었네요.

```powershell
Hugo Static Site Generator v0.74.3-DA0437B4 windows/amd64 BuildDate: 2020-07-23T16:23:30Z
```

# 블로그 생성