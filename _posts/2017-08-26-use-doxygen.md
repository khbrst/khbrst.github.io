---
layout: post
title: "Doxygen으로 문서화하기"
categories: dev
tags: doxygen graphviz help documentation
---

* content
{:toc}

프로젝트의 전반적인 내용을 공유하기 위해서는 문서화가 중요하다. 특히나 프로젝트가 커지면 커질수록 더 중요해지는데, 거대한 규모의 코드를 보는데 관련 문서가 부실할 때는 너무나 암담하다.

[Doxygen][2]은 프로젝트의 소스코드, 주석을 통해 문서를 자동으로 생성해주는 문서화 도구 중의 하나다. 아래와 같이 지원하는 프로그래밍 언어 종류는 다양하다.

> Doxygen is the de facto standard tool for generating documentation from annotated **C++** sources, but it also supports other popular programming languages such as **C, Objective-C, C#, PHP, Java, Python, IDL (Corba, Microsoft, and UNO/OpenOffice flavors), Fortran, VHDL, Tcl, and to some extent D**.

본문에서는 Ubuntu 16.04 LTS 환경에서 [googletest][5] 프로젝트를 HTML 문서로 만드는 예제를 설명하겠다.

> [원문][1]에서는 학부생 시절 Windows 7 환경에서 [MFC][3] 프로젝트를 문서([chm 파일][4])로 만드는 예제를 설명했다.

<!--more-->

## 작업 환경

아래 환경에서 `doxywizard` 프로그램을 통해 GUI 환경에서 문서를 생성하는 과정을 가이드한다.

> OS: Ubuntu 16.04 LTS
>
> Project: [googletest][5]

## 설치

### Doxygen

문서화 도구 프로그램이다. [여기][6]에서 자신의 OS에 맞는 가이드를 보고 다운로드, 설치하면 된다. Ubuntu에서는 package manager를 통해 간단히 설치할 수도 있다.

`doxygen-ui`는 Doxygen을 GUI 환경에서 사용할 수 있게 해주는 `doxywizard` 프로그램을 위해 같이 설치해준다.

```bash
sudo apt-get install doxygen doxygen-ui
```

### Graphviz

문서에 다양한 다이어그램들도 추가하고 싶다면 [여기][7]를 참고해서 설치한다. [Doxygen][2]과 마찬가지로 Ubuntu 환경이라면 package manager로 설치 가능하다.

```bash
sudo apt-get install graphviz
```

## 문서 만들기

Doxygen을 command line으로 실행할건지, GUI로 실행할건지에 따라 환경 설정하는 방법이 달라진다.

1. GUI frontend 도구를 사용하면 GUI 환경에서 설정이 가능하다.
    - Ubuntu에서는 추가로 `doxygen-ui` 설치가 필요하다.
    - Windows에서는 doxygen 설치시에 `doxywizard`라는 프로그램이 같이 설치된다.
1. Command line 환경에서 실행한다. [Doxygen manual][8]을 참고해서 설정 파일을 만들어 사용할 수 있다.

Ubuntu `doxygen-ui`를 설치했다면 `doxywizard` 프로그램을 사용할 수 있다. 실행시켜서 간단한 환경 설정 이후 문서를 만들어 보자.

### Wizard 탭 설정

![doxywizard-main](https://user-images.githubusercontent.com/4952571/29741189-a14cf574-8aa2-11e7-861c-b46b4568c172.png)

실행하면 위와 같은 화면을 볼 수 있다.

- Step 1

    Doxygen이 작업하기 위한 임시 path다. Ubuntu니까 `/tmp/` path를 설정한다.

- Project name

    결과 문서가 만들어졌을 때 사용할 프로젝트 이름이다.

- Source code directory

    소스 파일이 있는 프로젝트 directory path다. 아래의 `Scan recursively`를 선택해서 하위 directory도 검색해서 포함시키도록 하자.

- Destination directory

    문서화한 결과 파일들을 넣을 path다.

![doxywizard-wizard-project](https://user-images.githubusercontent.com/4952571/29741306-d09e505a-8aa4-11e7-80ec-f565d44ebfe8.png)

설정을 마치면 위와 같은 화면이 나온다. 이제, `Step 2 > Wizard > Mode`를 눌러보자.

![doxywizard-wizard-mode](https://user-images.githubusercontent.com/4952571/29741332-454f96ac-8aa5-11e7-9e04-f0235a61cae0.png)

- Select the desired extraction mode

    `Include cross-referenced source code in the output`는 각 함수마다 사용한 함수 코드로 바로 Jump할 수 있는 링크를 생성해준다.

- Select programming language to optimize the results for

    사용 언어에 맞게 선택한다.

![doxywizard-wizard-output](https://user-images.githubusercontent.com/4952571/29741355-cb50aeee-8aa5-11e7-82a7-59bc693ef666.png)

출력하고자 하는 형식을 선택한다.

![doxywizard-wizard-diagrams](https://user-images.githubusercontent.com/4952571/29741367-0dff7162-8aa6-11e7-94cc-49efcff7226e.png)

다양한 그래프, 다이어그램들을 그리기 위해선 앞에서 설명한 GraphViz가 필요하다.

### Expert 탭 설정

![doxywizard-expert-dot](https://user-images.githubusercontent.com/4952571/29741381-56aa86f4-8aa6-11e7-9d63-22c860cdeccb.png)

생성하고 싶은 그래프, 다이어그램을 선택한다.

### Run doxygen

![doxywizard-run-finished](https://user-images.githubusercontent.com/4952571/29741417-965e97bc-8aa7-11e7-8ed7-d4715f2bafb3.png)

Run 탭에서 `Run doxygen` 버튼을 눌러 문서를 만들고, 위와 같이 완료되면 `Show HTML output`으로 결과를 확인하자.

![doxywizard-output](https://user-images.githubusercontent.com/4952571/29741416-96567712-8aa7-11e7-8219-9e19af10ea84.png)

## Appendix. 한글이 깨지는 경우

한글 주석은 좋은 습관이 아니지만, 한글을 포함시켜서 문서를 만드려면 인코딩 문제로 한글이 깨진 문서가 만들어진다. 이 때는, Expert 탭에서 아래와 같이 추가 작업이 필요하다.

![doxywizard-expert-project](https://user-images.githubusercontent.com/4952571/29741379-56a778d8-8aa6-11e7-95ba-f73283eed98c.png)

- DOXYFILE_ENCODING: `cp949`
- OUTPUT_LANGUAGE: `Korean-en`

![doxywizard-expert-input](https://user-images.githubusercontent.com/4952571/29741380-56aa3e88-8aa6-11e7-8fa9-89750537b244.png)

- INPUT_ENCODING: `cp949`

[1]: http://blog.naver.com/khbrst/50112236741
[2]: http://www.stack.nl/~dimitri/doxygen/
[3]: https://en.wikipedia.org/wiki/Microsoft_Foundation_Class_Library
[4]: https://en.wikipedia.org/wiki/Microsoft_Compiled_HTML_Help
[5]: https://github.com/google/googletest
[6]: http://www.stack.nl/~dimitri/doxygen/download.html
[7]: http://www.graphviz.org/Download.php
[8]: http://www.stack.nl/~dimitri/doxygen/manual/starting.html#step1