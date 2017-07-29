---
layout: post
title:  "Git 활용"
categories: Dev
tags: git git-client tig bash-git-prompt smart-git git-blame vscode meld
---

* content
{:toc}

좋다고 생각되는 [Git][git] 사용 방법들을 공유해본다. 여러 가지 툴이나 방법들을 찾아보았고, 사용 목적에 따라 바꾸거나 섞어 쓰는 편이다. 아래 나열한 항목들은 모두 내가 직접 사용해봤고, 느낀 점들도 같이 정리해보았다.

## 일반적인 작업들을 할 때

### Git

![git-logo][git-logo]

    Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

* Platforms: Windows, Mac, Linux
* Price: Free

공식 [Git][git]으로, command line, GUI 모두 제공한다. GUI 기반으로 사용하려면 [SmartGit][smart-git]이나 [GitKraken][git-kraken]이 더 좋았다. GUI Client를 열심히 찾아볼 때가 있었으나, command line 환경에 익숙해지니 **빠르고 간편하게 사용**할 수 있어 주력으로 사용하고 있다. 하지만 작업에 따라 부족하다 싶을 때가 있어 그럴 때는 다른 툴들을 섞어서 사용한다.

<!--more-->

### tig

![tig-main-diff-view][tig-main-diff-view]

    Tig is an ncurses-based text-mode interface for git.

* Platforms: Windows, Mac, Linux
* Price: Free

[tig][tig]는 

### SmartGit

![smart-git-preview][smart-git-preview]

    Get your commit done.
    SmartGit is a Git client with support for GitHub Pull Requests+Comments and SVN.
    It runs on Mac OS X, Windows and Linux.

* Platforms: Windows, Mac, Linux
* Price: $79/user / Free for non-commercial use

[SmartGit][smart-git]이라는 Git GUI Client다.

### GitKraken

![git-kraken-preview][git-kraken-preview]

    The most popular Git GUI for Windows, Mac AND Linux

* Platforms: Windows, Mac, Linux
* Price: Free for non-commercial use

[GitKraken][git-kraken]

## 환경설정

### bash-git-prompt

[bash-git-prompt][bash-git-prompt]

## 누가 고친건지 추적할 때

`git blame` 기능으로 마지막에 누가 고친건지 추적할 수 있는데, 

### tig

![tig-blame-view][tig-blame-view]

    Tig is an ncurses-based text-mode interface for git.

* Platforms: Windows, Mac, Linux
* Price: Free

[tig][tig]

### GitLens

![git-lens][git-lens-preview]

    GitLens supercharges the built-in Visual Studio Code Git capabilities.

* Platforms: VSCode (Windows, Mac, Linux)
* Price: Free

[GitLens][git-lens]는 [VSCode][vscode]의 extension이다.

## 차이점을 이쁘게 보고 싶다.

### SmartGit

![smart-git-diff][smart-git-diff]

    Get your commit done.
    SmartGit is a Git client with support for GitHub Pull Requests+Comments and SVN.
    It runs on Mac OS X, Windows and Linux.

* Platforms: Windows, Mac, Linux
* Price: $79/user / Free for non-commercial use

[SmartGit][smart-git]

### Git difftool + meld

![meld-preview][meld-preview]

    Meld is a visual diff and merge tool targeted at developers.

[meld][meld]

## 그래도, 공부하고 사용하자.

[Collections](/collection/#git)

[git]:                https://git-scm.com/
[git-logo]:           https://git-scm.com/images/logo@2x.png
[tig]:                https://jonas.github.io/tig/
[tig-main-diff-view]: https://farm4.staticflickr.com/3427/3316427624_91ae9169e7.jpg
[tig-blame-view]:     https://farm4.staticflickr.com/3537/3316428506_26c75859cf.jpg
[smart-git]:          http://www.syntevo.com/smartgit/
[smart-git-preview]:  http://www.syntevo.com/smartgit/version-17/dark-theme.png
[smart-git-diff]:     http://www.syntevo.com/smartgit/version-6/compare-whitespaces.png
[git-kraken]:         https://www.gitkraken.com
[git-kraken-preview]: https://git-scm.com/images/guis/git-kraken@2x.png
[bash-git-prompt]:    https://github.com/magicmonty/bash-git-prompt
[vscode]:             https://code.visualstudio.com/
[git-lens]:           https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens
[git-lens-preview]:   https://raw.githubusercontent.com/eamodio/vscode-gitlens/master/images/gitlens-preview.gif
[meld]:               http://meldmerge.org/
[meld-preview]:       http://meldmerge.org/images/meld-mary.png