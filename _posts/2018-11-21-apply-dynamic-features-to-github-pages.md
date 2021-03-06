---
title: "GitHub Pages 블로그에 댓글, 통계 분석 기능 추가하기"
categories:
    - dev
tags:
    - github-pages
    - jekyll
    - disqus
    - google-analytics
toc: true
---

## Overview

GitHub Pages, jekyll을 사용해서 블로그를 처음 만들고 테마만 적용한다면 뭔가 허전할거다.

Jekyll은 **정적** 사이트 생성기라서 블로그 페이지는 별다른 설정없이 작성할 수 있다. 하지만 **동적** 기능인 댓글, 통계를 기본적으로 제공하지 않는다. 이 기능들을 사용하려면 별도의 서비스에 가입해서 jekyll과 연결해야 한다.

다행스럽게도 유명한 jekyll 테마들은 플러그인 형태로 댓글, 통계 기능을 쉽게 추가할 수 있도록 만들어 놓았다. 이 글에서는 내가 사용중인 [Minimal Mistake Jekyll 테마](https://mmistakes.github.io/minimal-mistakes/)에 댓글 기능([Disqus](https://disqus.com/))과 통계 기능([Google Analytics](https://analytics.google.com/))을 추가해보겠다.

## Adds Comments

Jekyll 테마마다 지원하는 댓글 서비스들이 다르다. 물론 직접 구현해서 추가하는 방법도 있지만 귀찮아서 싫다. [Minimal Mistake 환경설정 가이드](https://mmistakes.github.io/minimal-mistakes/docs/configuration/)를 보면 자세히 설명되어 있으니 천천히 따라가보자.

> 다른 테마를 사용중이라면 해당 테마 홈페이지에 가서 가이드 문서를 보거나, `_config.yml` 파일을 잘 살펴보면 comments 서비스를 선택할 수 있는 부분이 보일거다.

[Minimal Mistake Jekyll 테마](https://mmistakes.github.io/minimal-mistakes/)는 여러 댓글 시스템을 지원하는데, 구글링해보면 [Disqus](https://disqus.com/)가 대세로 보여 선택해보았다. 많이들 사용하는건 다 이유가 있더라.

[Disqus 홈페이지](https://disqus.com/)에 접속해서 가입하고 로그인해보자. 간단한 정보들만 입력해주면 로그인까지 성공한다. 어렵다면 구글링을 조금만 해보면 좋은 글들이 많으니 참고하자.

이후 `_config.yml` 파일에 설정할 [shortname을 만들어보자](https://help.disqus.com/installation/whats-a-shortname). 성공적으로 만들었다면 `_config.yml` 파일에 `shortname` 을 추가해보자. `"your-disqus-shortname"`부분에 내가 만든 `shortname`을 집어넣으면 된다.

```yml
comments:
  provider: "disqus"
  disqus:
    shortname: "your-disqus-shortname"
```

여기까지 끝냈다면 변경사항들을 commit하고 GitHub Pages에 push해서 댓글 기능이 활성화되었는지 확인해보자. 조금 시간이 걸릴 수도 있다.

바로 결과를 확인해보고 싶다면 [Jekyll을 로컬 서버로 실행해서 확인](http://jekyllrb-ko.github.io/docs/usage/)해볼 수도 있다.

## Adds Statistic Analytics

댓글과 마찬가지로 jekyll 테마마다 지원하는 통계 분석 서비스들이 다르다. [Minimal Mistake 환경설정 가이드](https://mmistakes.github.io/minimal-mistakes/docs/configuration/)를 보면 다행스럽게도 지원하는 서비스들이 많으니 한번 살펴보자.

> 다른 테마를 사용중이라면 해당 테마 홈페이지에 가서 가이드 문서를 보거나, `_config.yml` 파일을 잘 살펴보면 analytics 서비스를 선택할 수 있는 부분이 보일거다.

통계하면 구글이 떠오르는데, 역시나 [Google Analytics](https://analytics.google.com/)라는 통계 분석 서비스를 지원한다. [Google 웹로그 분석 모바일 앱](https://play.google.com/store/apps/details?id=com.google.android.apps.giant&hl=ko)으로도 볼 수 있으니 아주 편하다.

방문자 수뿐만 아니라 유입 경로, 접속 지역, 접속한 기기 등 여러가지 정보를 얻을 수 있다. 가입 후 Disqus와 유사하게 내 사이트 설정을 하고 나면 `tracking_id`를 얻을 수 있다. 댓글 기능 추가 때와 마찬가지로 `_config.yml` 파일을 아래와 같이 내 `tracking_id`와 같이 설정해주면 된다.

```yml
analytics:
  provider: "google"
  google:
    tracking_id: "UA-1234567-8"
    anonymize_ip: false # default
```

변경사항들을 commit하고 GitHub Pages에 push하자. 마지막으로 [Google Analytics](https://analytics.google.com/)에 접속해보면 된다!

## References

- [Jekyll](https://jekyllrb.com)
- [GitHub Pages](https://pages.github.com)
- [GitHub Pages Customizing Guide](https://help.github.com/categories/customizing-github-pages/)
- [Minimal Mistake Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/)
- [Disqus](https://disqus.com/)
- [Google Analytics](https://analytics.google.com)
