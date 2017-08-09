---
layout: post
title: "GitHub Pages 설정하기"
categories: dev
tags: git github github-pages jekyll jekyll-plugins blog
---

* content
{:toc}

GitHub Pages, jekyll을 사용해서 블로그를 만들었지만 허전한 부분들이 많이 보인다.

Web은 생소한 분야라 필요한 기능들을 천천히 추가하면서 공부 중이다. 역시 새로운 분야는 재밌다!

## Comments system

![disqus-logo][disqus-logo]

Jekyll은 **정적** 사이트 생성기라서, **동적** 기능인 댓글을 사용하려면 별도의 서비스를 추가해야 한다.

구글링헤보니 대세로 보이는 Disqus를 선택해서 설치했다. Disqus에 로그인하고 `GET STARTED`를 눌러 간단한 정보들만 입력해주면 된다.

<!--more-->

![disqus-create][disqus-create]

Website Name 항목이 중요한데, `shortname.disqus.com` 형식으로 Disqus Site가 만들어진다(`shortname`이 `Disqus Site ID`가 된다.).

Disqus 설정을 끝내면 Jekyll에 설치한다.

미리 설치했던 jekyll 테마에서 disqus 추가 지원 여부에 따라 설치 방법이 갈라진다.

* [내가 설치한 테마][cool-concise-jekyll-theme]는 `_config.yml` 파일에 `disqus_shortname` 항목이 있어 여기 내 `disqus shortname`을 입력하면 바로 적용된다.
* 만약, 위와 같은 기능을 사용할 수 없으면 직접 설치해야 한다. [여기][disqus-install]의 스크립트를 복사해서 표시하고 싶은 위치에 붙여넣으면 된다.

## Statistic analytics

GitHub Pages는 단순히 호스팅만 하기 때문에, 통계 자료를 보기 위해서는 서비스 추가가 필요하다.

Google Analytics는 아주 간단하게 설정하고 다양한 정보들을 볼 수 있는 서비스다.

## Support robots

네이버 웹마스터도구

robots.txt

## Jekyll plugins

[jekyll]:                          https://jekyllrb.com
[github]:                          https://github.com
[github-pages]:                    https://pages.github.com
[github-pages-customizing-guide]:  https://help.github.com/categories/customizing-github-pages/
[cool-concise-jekyll-theme]:       https://github.com/Gaohaoyang/gaohaoyang.github.io
[disqus]:                          https://disqus.com/
[disqus-install]:                  https://disqus.com/admin/settings/universalcode/
[google-analytics]:                https://analytics.google.com
[naver-webmastertool]:             http://webmastertool.naver.com/

[disqus-logo]:
[disqus-create]: