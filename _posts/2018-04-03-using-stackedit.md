---
title: "StackEdit 사용하기"
categories:
    - dev
tags:
    - github
    - markdown
    - stackedit
    - blog
    - jekyll
toc: true
---

## What is StackEdit

![image](https://user-images.githubusercontent.com/4952571/38148090-eb4ff8fa-348f-11e8-90e3-8b585a1c31ab.png)

StackEdit은 markdown 문법으로 문서 작성이 가능한 웹 기반 에디터다. 브라우저로 접속해서 사용할 수 있고, 구글 계정 로그인을 통한 동기화도 지원한다.

Markdown 문법에 대해서는 별도의 포스팅을 작성할 계획이다.

## Why use

GitHub Pages + jekyll 조합으로 블로깅을 시작하려니 내 마음에 드는 markdown 에디터가 필요했다. StackEdit, Visual Studio Code, Typora 등의 markdown 에디터를 찾아보았지만 모든 조건들을 만족하는건 StackEdit 뿐이었다. 심지어 브라우저 캐시를 사용해 오프라인에서도 실행할 수 있으니 정말 마음에 들었다.

Markdown 문법 자체의 장점을 제외한 StackEdit 자체의 장점은:

1. PC, 태블릿, 폰에서 실행하고 구글 계정 로그인으로 동기화가 가능하다.

    브라우저만 실행할 수 있으면 되니 Windows, iOS, Android 등 실행 환경을 가리지 않는다.
    현재 이 문서도 Windows PC, Android 태블릿, Android 모바일로 StackEdit을 접속해서 작성하고 있다.

2. UI가 직관적이고 깔끔하며 preview 기능이 있다.

    아래는 처음 StackEdit을 실행하면 볼 수 있는 Welcome file 화면이다.
    Markdown 문법을 모르더라도 익숙해지는데 오랜 시간이 걸리지 않는다.
    ![image](https://user-images.githubusercontent.com/4952571/38202316-3f6408da-36d6-11e8-802f-008fece7a2dc.png)
    심지어 오른 쪽 상단의 ![image](https://user-images.githubusercontent.com/4952571/38202505-e7cd6336-36d6-11e8-8c85-26421d78acef.png) 버튼을 눌러 Markdown cheat sheet를 볼 수도 있다. 친절하다.
    ![image](https://user-images.githubusercontent.com/4952571/38202554-15c3f836-36d7-11e8-8331-4f1e4545fb7b.png)

3. 가볍고 빠르다.

    사용해보기 전엔 동기화, 문서 작성, preview 반영 속도가 느리지 않을까 걱정했지만, 전혀 답답함을 느낄 수 없었다.

4. **무료다.**

    StackEdit은 [GitHub 오픈소스](https://github.com/benweet/stackedit)다.

## Considerations

무료 오픈소스라는건 좋으면서도 걱정스러운 부분이다. 걱정인 부분은 안정성이다.

실제로 이 포스팅을 작성하기 위해 다시 한번 구글링했을 때, 부정적인 글들을 보았다. 브라우저 캐시를 삭제했다가 포스팅을 모두 잃었다거나, 제작자([Benoit Schweblin](https://github.com/benweet))가 새로운 에디터 제작에 몰두하고 있다는 글이었다.

### Data loss prevention

먼저, 데이터를 잃는 사고를 경험해보지 않았지만, 이러한 클라우드 서비스를 이용하는데 있어 이런 사고가 단 한번이라도 일어나서는 안된다. 매우 두려운 일이지 않나? 사고 이후로 얼마나 안정화되었는지는 모르겠지만, 이런 사고를 방지할 수 있는 기능이 있긴 하다.

Google Drive나 CouchDB workspace를 추가한다. 오른 쪽 상단의 ![image](https://user-images.githubusercontent.com/4952571/38202505-e7cd6336-36d6-11e8-8c85-26421d78acef.png) 버튼을 눌러 Workspaces 메뉴에서 workspace를 추가하여 연동하는 방법이다. 내 경우는 Google Drive를 사용했는데, Google Drive에 접속하여 새로 만들기 메뉴를 통해 Google Drive의 파일과 실시간으로 연동되는 StackEdit 문서를 만들 수 있었다.

![image](https://user-images.githubusercontent.com/4952571/38204370-a9852c42-36dd-11e8-98f3-8828f28f754b.png)

이렇게 만들어진 문서는 위와 같이 Google Drive 아이콘![image](https://user-images.githubusercontent.com/4952571/38204411-d5cfeb3e-36dd-11e8-957c-3589bde274f3.png) 이 붙는다.

### Ensure continuous updates

제작자가 새로운 에디터 개발에 열중하고 있다는 이야기는 [GitHub Profile](https://github.com/benweet)에 들어가보기만 해도 루머라는걸 알 수 있었다.

![image](https://user-images.githubusercontent.com/4952571/38204254-2a1eb0d6-36dd-11e8-95e4-c09e99316f83.png)

심지어 최근 webserver에 설치해서 사용할 수 있는 [StackEdit.js](https://benweet.github.io/stackedit.js/)도 내놓고 있는걸 보면, 당분간 업데이트가 끊어질 걱정은 안든다.

### Markdown compatibility

StackEdit의 문제라기보단 markdown의 특징으로 볼 수 있다. Markdown의 기본 문법은 매우 간단한데, 명확한 표준이 없다. 그래서 markdown을 사용하는 곳(GitHub, markdown 에디터들)마다 조금씩 다른 확장 문법들이 있다.

StackEdit도 예외는 아닌데, Welcome file의 UML diagram이 좋은 예다. StackEdit 전용 문법을 사용하여 문서를 작성했다고 해서 다른 markdown 지원 서비스에서도 똑같이 표시될거라고 기대해선 안된다.

하지만, markdown 기본 문법으로도 블로그 포스팅을 작성하는데 무리는 없다.

## Conclusion

지금 바로 접속해서 잘 써보자!

## References

[StackEdit.io](https://stackedit.io/app)

[StackEdit GitHub repository](https://github.com/benweet/stackedit)

[StackEdit.js GitHub repository](https://github.com/benweet/stackedit.js)

[Benoit Schweblin GitHub Profile](https://github.com/benweet)
