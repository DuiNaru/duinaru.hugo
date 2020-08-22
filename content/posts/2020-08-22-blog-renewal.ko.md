+++
categories = ["blog"]
tags = ["hugo", "netlify", "netlify cms"]
title = "블로그를 리뉴얼 하였습니다"
permalink = "2020-08-22-blog-renewal"
date = 2020-08-22T11:44:26.085Z
description = "Github Pages + Jekyll 에서 Netlify + Hugo + Netlify CMS 로 블로그를 리뉴얼 하였습니다."
i18n = "ko"

[[images]]
src = "/img/uploads/netlify.webp"
alt = "netlify logo"
+++
기존에는 Jekyll로 만들어서 Github Pages에 배포하였지만, Jekyll의 다국어 지원에 불만이 있어서 고민하던 중에 Hugo 로 바꾸어 쓰기로 하였습니다. 그러면서 Netlify + Netlify CMS 을 넣어보기로 하고요.

이 글에서는 리뉴얼 후기 및 과정에 대해 적어볼까 합니다.

# [Hugo](https://gohugo.io/about/what-is-hugo/)

Hugo는 go 언어로 작성된 정적 사이트 생성기 입니다. 일반적인 동적 사이트 처럼 서버에서 웹 페이지를 만들어서 보여주는 것과 다르게 단순히 만들어져 있는 웹 페이지를 보여주게 되죠. 서버 자원을 절약할 수 있다는 점이 매력적인 부분입니다.

Jekyll 역시 정적 사이트 생성기 이지만, 비교적 최신이기도 하고 다국어 지원에서의 편리함도 있어서 바꾸기로 하였습니다.

## 다국어 지원 - Jekyll vs Hugo

### Jekyll

Jekyll에서의 다국어 지원은 plugin을 통해서 지원합니다. 

[개발과 경험이 함께 하는 블로그 - 만들기](/posts/2019-10-23-blog-with-development-and-experience/#만들기)

[](/posts/2019-10-23-blog-with-development-and-experience/#만들기)[](2019-10-23-blog-with-development-and-experience/#만들기)polyglot 이나 jekyll-multiple-languages-plugin 이 대표적이지만, 둘다 플러그인 이기에 다른 플러그인과 함께 쓰거나 관리에 있어 불편함이 생기기 마련이죠.

아니면 플러그인을 사용하지 않고 Jekyll 의 코드를 직접 작성해서 만들어도 되지만, 불편함은 여전하죠.

### Hugo

그에 반해 Hugo 는 다국어를 지원합니다.

[Hugo - Multilingual Mode](https://gohugo.io/content-management/multilingual/)

기본적으로 지원하고 있기에, 편리할 것으로 보여서 사용하기로 하였습니다.

# [Netlify](https://www.netlify.com/)

CI/CD 도구 중에 하나입니다. Git repository에서 배포까지 자동화 할 수 있게 되죠.

Netlify CMS에서 글을 작성하게 되면, Git repository에 추가 되는데, 즉시 Hugo를 사용하여 빌드를 하고, 웹에서 볼 수 있게 할 수 있습니다. 글 작성할 마다 수동으로 빌드해주고 배포할 필요가 없어지게 되죠.

# [Netlify CMS](https://www.netlifycms.org/)

[](https://www.netlifycms.org/)기존에는 jekyll-admin 플러그인으로 글을 관리 했었으나, hugo로 바꾸면서 다른 방법을 찾아야 했습니다.

[Frontend Interfaces with Hugo](https://gohugo.io/tools/frontends/)

그 중에 Netlify랑 같이 쓰기 좋아보이는 Netlify CMS 를 넣어봤습니다.

글 작성이나 수정, 삭제를 Git으로 관리 할 수 있어서, Git의 장점을 같이 누릴 수 있게 되는 장점이 있습니다. 작성한 글들의 목록을 확인하거나, 작성하면서 미리보기 등의 기능도 편리하지요.

# Theme

여러가지의 테마 중에 Hugo Future Imperfect Slim 를 사용하였습니다.

[Hugo Future Imperfect Slim](https://github.com/pacollins/hugo-future-imperfect-slim)

깔끔하니 좋은 듯 합니다. 게다가 계속 업데이트가 이루어 지고 있으니, 문제가 생기더라도 대처가 빠를 듯 하네요.

# 완성

<https://duinaru.netlify.app/>

도메인은 따로 설정해 주지는 않고, netlify에서 기본 설정된 도메인을 사용하고 있습니다.

나중에 도메인을 구매해서 변경하게 되더라도, 도메인 추가 설정만 해주면 되기에 천천히 생각해 보려고 합니다.

다음에는 만드는 과정이나 고민한 것에 대해서 글을 작성해볼까 합니다.