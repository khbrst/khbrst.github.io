---
layout: post
title:  "GitHub Pages로 블로그 시작하기"
categories: Dev
tags: Git GitHub GitHubPages jekyll jekyll-now blog
---

공부 과정들을 정리하는 겸 블로그를 다시 시작하려고 한다. 네이버, 티스토리 등의 블로그 서비스를 사용했었으나 불편함이 있어 여러 서비스들을 찾아보았다.

## 왜 [GitHub Pages][github-pages]인가

고민 끝에 [GitHub Pages][github-pages]를 선택했다. 진입장벽이 있다고는 하나 매력적인 면(**심플함, 자유도, 편리함, ...**)들이 있었다.

[GitHub Pages][github-pages]는 저장소(무료 1GB)를 **{username}.github.io** 주소로 호스팅해주는 서비스다. html, css 등의 파일들을 직접 만들고 관리해야 한다는 소리다.

여기에 [jekyll][jekyll]이라는 정적 사이트 생성기를 연동하면 아주 편리해진다. [jekyll][jekyll]을 간단하게 설명하면, markdown 문법으로 포스팅을 작성하면 [jekyll][jekyll]에서 미리 설정한대로 웹 페이지 파일(html, css)을 생성해준다.

## 작업 환경

집에서 놀고 있던 노트북에 설정했다.

* OS: Windows 10

* git client: Git bash

## [GitHub Pages][github-pages] 저장소 설정

1. [GitHub][github] 계정이 없다면, 가입해야 한다. [GitHub Pages][github-pages]에서 호스팅해주는 주소가 이 계정이름을 사용함(**{username}.github.io**)을 참고한다.

1. [GitHub][github] 로그인 후, [저장소를 만든다][github-new].

1. 로컬(노트북) 환경에서 작업할 수 있도록 clone해서 로컬 저장소를 만든다.

```bash
git clone https://github.com/{username}/{username}.github.io
```

## [jekyll][jekyll] site 만들고 확인하기

Clone 해뒀던 저장소에 [jekyll][jekyll] site 설정을 하고, 리모트 저장소에 push하기 전에 로컬 웹서버를 돌려서 site preview를 확인할 수 있다.

```bash
# Install Jekyll and Bundler gems through RubyGems
gem install jekyll bundler

# Change into your local repository directory
cd {username}.github.io

# Create a new Jekyll site at ./
jekyll new .

# Build the site on the preview server
bundle exec jekyll serve
```

위와 같이 작업한 후, [localhost port 4000번 주소](http://localhost:4000)로 접속해볼 수 있다.

## [jekyll now][jekyll-now] theme 적용하기

[jekyll now 가이드][jekyll-now]를 따라해보았다.

저장소를 fork하는 방법이 아니라, clone한 후에 로컬에 덮어씌워서 적용시켰다.

### Trouble shooting

**Dependency Error**가 발생했다. 아래와 같이 해결하면 된다([출처][jekyll-now-bug]).

```bash
# For additional dependency
gem install github-pages
gem install jekyll-sitemap
```

```ruby
# Gemfile
...
gem 'jekyll-sitemap'
```

## Appendix. [VSCode][vscode] + git bash

에디터, 터미널 하나씩 띄워두고 작업해도 되지만 귀찮은걸 싫어하기 때문에 VSCode의 integrated terminal로 git bash를 연동해서 사용한 방법도 공유한다. VSCode 내에서 단축키 하나로 왔다갔다할 수 있는 이점이 있다!

VSCode > File > Preferences > User settings 화면에서 아래 한 줄을 추가한다.

```json
"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
```

[jekyll]:         https://jekyllrb.com
[jekyll-now]:     https://github.com/barryclark/jekyll-now
[jekyll-now-bug]: https://github.com/qwtel/hydejack/issues/8
[vscode]:         https://code.visualstudio.com/
[github]:         https://github.com
[github-new]:     https://github.com/new
[github-pages]:   https://pages.github.com