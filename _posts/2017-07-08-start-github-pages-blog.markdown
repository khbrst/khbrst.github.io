---
layout: post
title:  "GitHub Pages로 블로그 시작하기"
date:   2017-07-08 20:33:28 +0900
---

# 왜 [GitHub Pages][github-pages]인가

공부 과정들을 정리하는 겸 블로그를 다시 시작하려고 한다. 네이버, 티스토리 등의 블로그 서비스를 사용했었으나 불편함이 있어 여러 서비스들을 찾아보았다.

고민 끝에 [GitHub Pages][github-pages]를 선택했다. 진입장벽(*최소 간단한 웹, git 지식. 난 개발자니까 상관없다!*)이 있다고는 하나 매력적인 면(**심플함, 자유도, 편리함, ...**)들이 있었다.

# 진입장벽

[GitHub Pages][github-pages]는 저장소(무료 1GB)를 **{username}.github.io** 주소로 호스팅해주는 서비스다. html, css 등의 파일들을 직접 만들고 관리해야 한다는 소리다.

여기에 [jekyll][jekyll]이라는 정적 사이트 생성기를 연동하면 아주 편리해진다. [jekyll][jekyll]을 간단하게 설명하면, markdown 문법으로 포스팅을 작성하면 [jekyll][jekyll]에서 미리 설정한대로 웹 페이지 파일(html, css)을 생성해준다.

# 환경

집에서 놀고 있던 노트북에 설정했다.

* OS: Windows 10

* git client: Git bash

* Editor: [VSCode][vscode]

# [GitHub Pages][github-pages] 저장소 설정

[GitHub][github] 계정이 없다면, 가입해야 한다.

참고: [GitHub Pages][github-pages]에서 호스팅해주는 주소는 **{username}.github.io** 형식이다.

## [저장소 만들기][github-new]

저장소 이름은 **"{username}.github.io"** 형식이어야 한다.

## 로컬 저장소 만들기

로컬(노트북) 환경에서 작업할 수 있도록 로컬 저장소를 만든다.

```bash
git clone https://github.com/{username}/{username}.github.io
```

# [jekyll][jekyll] site 만들고 확인하기

Clone 해뒀던 저장소에 [jekyll][jekyll] site 설정을 하고, 리모트 저장소에 push하기 전에 로컬 서버를 돌려서 site preview를 확인한다.

```bash
# Install Jekyll and Bundler gems through RubyGems
gem install jekyll bundler

# Change into your local repository directory
cd {username}.github.io

# Create a new Jekyll site at ./
jekyll new .

# Build the site on the preview server
bundle exec jekyll serve

# Now browse to http://localhost:4000
```

# VSCode integrated terminal로 git bash 사용

에디터, 터미널 하나씩 띄워두고 작업해도 되지만 귀찮은걸 싫어하기 때문에 VSCode의 integrated terminal로 git bash를 연동해서 사용하려고 한다. VSCode 내에서 단축키 하나로 왔다갔다할 수 있는 이점이 있다!

VSCode > File > Prefrences > User settings 화면에서 아래 한 줄을 추가한다.

```json
"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
```

[jekyll]:       https://jekyllrb.com
[vscode]:       https://code.visualstudio.com/
[github]:       https://github.com
[github-new]:   https://github.com/new
[github-pages]: https://pages.github.com