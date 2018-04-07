---
title: "Markdown에 관하여"
categories:
    - dev
tags:
    - github
    - vscode
    - markdown
    - stackedit
    - blog
    - jekyll
toc: true
---

[Markdown](https://en.wikipedia.org/wiki/Markdown)은 [markup language](https://en.wikipedia.org/wiki/Markup_language)의 일종이다. 파일 확장자로는 `.md`, `.markdown`을 사용한다.

[John Gruber](https://en.wikipedia.org/wiki/John_Gruber)와 [Aaron Swartz](https://en.wikipedia.org/wiki/Aaron_Swartz)가 만들었는데, John Gruber의 [Daring Fireball](https://daringfireball.net) 사이트에서는 markdown을 아래와 같이 소개하고 있다.

> Markdown is a text-to-HTML conversion tool for web writers. Markdown allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML). ...

## Why use

**Markdown은 읽고 쓰기 쉬운 plain text 문법으로, HTML로 손쉽게 변환할 수 있다.** 간단한 아이디어지만 엄청나게 유용하다. Plain text 포맷은 *어떤 에디터라도 지원*하고, 변환 도구만 있다면 내 마음에 드는 예쁜 스타일의 HTML로 변환시켜서 블로깅이나 기술 문서 작성에 활용할 수 있기 때문이다.

![image](https://user-images.githubusercontent.com/4952571/38452729-e4f0ae5a-3a84-11e8-8027-13aec571c432.png)

[StackEdit](https://stackedit.io/app)으로 현재 문서를 작성중이다:

![image](https://user-images.githubusercontent.com/4952571/38452773-eaf93d0c-3a85-11e8-881f-af9647440407.png)


### Disadvantages of  web WYSIWYG editor

국내 블로그 사이트들은 대부분 자체 웹 위지윅 에디터만 지원한다. 이러한 에디터는 편리하게 문서를 작성할 수 있지만, 단점이 있다.

1. 제작사마다 UI와 기능이 다르다.

    사용하고 있는 웹 위지윅 에디터의 UI가 깔끔하고 기능이 많으며 업데이트를 꾸준히 해준다면 걱정은 없다. 하지만 UI가 깔끔하지 않다면? 기능이 제한적이라면? 언제 개선할지 알 수 없다면?
    Markdown을 사용한다면 마음에 드는 에디터를 아무거나 골라서 사용하면 된다. 하지만 적어도 [StackEdit](https://stackedit.io/app) 같이 markdown preview 기능이 있는 에디터를 추천한다.

2. 문서 스타일을 일관성있게 관리하기 힘들다.

   블로그를 하다보면 지금까지 작성한 문서들의 스타일(본문의 폰트, 글자 크기, ...)을 바꾸고 싶은 때가 있다. 웹 위지윅 에디터를 서비스하는 곳에서 해당 기능을 지원하지 않는다면 일일히 다 변환해야 한다.
   Markdown은 변환 도구의 스타일만 변경하면 된다.

### Considerations

Markdown의 단점도 있으니 꼭 참고하자.

1. 표준이 없다.

    표준이 없으니 변환 도구에 따라서 지원하는 markdown의 확장 문법이나, 결과물의 모습이 완전히 달라진다. 이로 인해 변환 도구마다 이식성이 떨어진다는 문제가 발생한다.
    이식성을 위해선 [기본 문법](https://daringfireball.net/projects/markdown/syntax)만 사용해서 문서를 작성하자.

2. 지원 문법이 제한적이다.

    Markdown 문법만으로는 HTML을 100% 대체할 수 없다. 특히나 이식성을 위해서 확장 문법을 사용하지 않고 기본 문법만 사용한다면 더 제한적이다.
    웹 위지윅 에디터는 이식성이 떨어지더라도 제작사에 따라 markdown보다 더 다양한 기능을 제공할 수 있다.

## Conclusion

이러한 단점에도 불구하고 사람들이 기술 문서 작성을 위해 많이 사용하고 있다는 것은 그만큼 편하기 때문이지 않을까? 한번쯤 사용해보길 추천한다.

## References

[Markdown Wikipedia](https://en.wikipedia.org/wiki/Markdown)

[Markdown Syntax Documentation - Daring Fireball](https://daringfireball.net/projects/markdown/syntax)
