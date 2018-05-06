---
title: "Rust에 관하여"
categories:
    - dev
tags:
    - rust
    - programming-language
    - stackoverflow
    - cargo
    - mozila
toc: true
---

## What is Rust

일하다가 우연히 알게 된 프로그래밍 언어인데, 공부할수록 재미있고 나 혼자 알고 있기 아까워서 얕게 훑어보는 글을 작성해보았다.

![image](https://www.rust-lang.org/logos/rust-logo-blk.svg)

[Rust 공식 사이트](https://www.rust-lang.org)에서는 "*매우 빠르며, 세그폴트를 방지하고, 스레드 안전성을 보장하는 시스템 프로그래밍 언어*"로, [Rust GitHub 저장소](https://github.com/rust-lang/rust)에서는 "*A safe, concurrent, practical language.:안전하고, 병렬적이며, 실용적인 언어*"로 소개하고 있다.

소개만 보면 시스템 프로그래밍 영역에서 성능을 희생하지 않으면서 골치아픈 부분들을 해결해주는 매우 좋은 언어다. 하지만 요즘 사기꾼들이 많아서 검증은 필요하다. 진실인지 거짓인지 살펴보자.

먼저 [Wikipedia](https://en.wikipedia.org/wiki/Rust_(programming_language))에서 짤막한 역사를 보면:

- 2006년 개발자 그레이든 호아레의 개인 프로젝트로 시작
- 2009년 호아레의 고용주 [모질라](https://www.mozilla.org)가 개발에 참여
- 2010년 처음 일반에 공개
- 2012년 첫 알파 버전 발표
- ...
- 2015년 1.0 버전 발표
- ...

이처럼 최근에 시작된 프로젝트지만 다양한 곳에서 사용하고 있다.

## Who use

[Friends of Rust](https://www.rust-lang.org/friends.html)에서 Rust를 사용하는 단체들을 볼 수 있다. **Mozila, LINE, NPM, Dropbox, SmartThings** 같은 유명한 곳들이 눈에 띈다.

[Wikipedia의 Projects using Rust 섹션](https://en.wikipedia.org/wiki/Rust_(programming_language)#Projects_using_Rust)을 보면 web engine, game engine, editor, OS(!) 등의 분야들에서 사용하고 있다. 이 분야들의 공통점은 고성능을 위해 오랫동안 C, C++ 언어가 강세였단거다. Rust가 시스템 프로그래밍 언어며 출시 초기에 Firefox 브라우저의 [웹 엔진](https://servo.org/) 개발에 쓰인 사실을 고려하면 C, C++에서 Rust로의 이동이 자연스러운 흐름으로 느껴진다.

## Why use

앞서 살펴본 여러 단체들이 왜 사용할까? 단체가 아닌 개인 개발자들도 만족하며 사용하고 있는걸까?

개발 관련 질의응답 사이트로 유명한 [Stack Overflow의 설문 결과](https://insights.stackoverflow.com/survey)를 보면 개발자가 가장 좋아하는(`Most Loved`) 언어 부문 2015년 3위, 2016~2018년 1위를 차지하고 있다. 2010년 일반에 공개된 언어인데다, 근소한 차이지만 `Kotlin`, `Python`, `TypeScript` 등 잘 나가는 언어들을 이겼기 때문에 더 흥미로운 결과다.

아래 이미지는 2018년 설문 결과다.

![image](https://user-images.githubusercontent.com/4952571/39203695-82e6be2a-4830-11e8-89cb-6b4f6c7e2b30.png)

이쯤되면 더 궁금해지지 않는가?

개발자들이 가장 좋아한다고 해서 현업에서도 많이 사용한다는 의미는 아니다. 하지만 요즘같이 새로운 언어들(Google의 `Kotlin`, Microsoft의 `TypeScript`, Apple의 `Swift`)이 거대 기업들의 공식 지원을 받으며 나오는 혼란스러운 시대에 개발자에게 다른 언어들에 꿀리지 않고 꾸준히 어필할 수 있는 매력을 가지고 있다는 사실이 신기하다. Rust가 개인 프로젝트로 시작되었음을 생각해보자.

Rust의 장점은 무엇이길래 인기가 있을까? Rust 언어가 소개했던 특징들을 하나하나 확인해 보자.

### Blazingly fast

Google에 `rust benchmark`, `rust performance`만 검색해봐도 많은 결과들이 나온다.

![image](https://user-images.githubusercontent.com/4952571/39201824-30811874-482b-11e8-806f-85b614f4e3e6.png)

시험 환경에 따라서 많이 달라질 수 있지만, 일반적으로 C, C++과 비슷한 수준이라는 것을 알 수 있다. [공식 사이트 FaQ](https://www.rust-lang.org/en-US/faq.html)에서는 대놓고 *C, C++에 경쟁력있을 정도로 빠르다*고 적어놨다. [Benchmarks Game](https://benchmarksgame.alioth.debian.org/u64q/compare.php?lang=rust&lang2=gpp)이나 [기타 이것 저것](https://github.com/kostya/benchmarks) 링크가 있으니 참고하자.

### Prevents segfaults and Thread safety

Rust 언어는 garbage collector가 없지만 메모리, 스레드 문제를 컴파일 시간에 잡아낸다. Rust는 언어 자체의 규칙과 특징으로 이 어려운 목표를 이루어냈다. 규칙들을 간단하게 묶어서 적어보겠다. 아래에서 말하는 값은 힙 메모리를 할당하는 값들을 말한다.

1. 한번에 하나의 이름(변수)으로만 값의 소유권(Ownership)을 가질 수 있다.
2. 소유권은 넘겨받거나 빌릴 수 있다(References & Borrowing).
3. 메모리를 변경 불가능한 참조(immutable reference)로는 여러 곳에서 동시에 접근 가능하다.

![rust](https://user-images.githubusercontent.com/4952571/39671521-d1af33de-5154-11e8-9796-564c254e0a85.jpg)

용어 설명없이 다짜고짜 규칙부터 말해서 이해가 어려울 수 있다. 핵심을 요약하면 **"메모리를 한번에 한 곳에서만 수정할 수 있게 강제한다**"이다. 이 규칙을 어기면 컴파일 시간에 추적해서 에러를 발생시킨다. Multi-thread 환경에서 발생하는 대부분의 문제들은 **공유 자원을 여러 곳에서 동시에 수정**하려고 할 때 발생한다. Rust는 이 문제에 대해 공유를 막는 방법으로 접근하고 있다는 말이다.

깐깐하다고 생각할 수도 있다. 하지만 C, C++로 만들어진 거대한 프로젝트에서 메모리나 스레드 문제가 실행 시간에 발생해서 원인을 찾아본 적이 있는가? 컴파일 시간에 일어나는 문제를 디버깅하는 쪽이 훨씬 더 쉽고 편하다. 그러니 안전을 위한 대가로는 적절한 규칙이다.

이제 Mutability, Ownership도 간단하게 짚고 넘어가보자. 더 자세한 내용은 범위를 넘어서니 다루지 않겠다.

#### Mutability

Rust의 변수는 기본적으로 변경불가능하고, 변경가능하게 만드려면 `mut` 키워드를 사용해야 한다. 다른 언어는 기본적으로 변경가능하고, 변경불가능하게 만드려면 `const`, `final` 같은 키워드를 사용해야 하는 것과는 대조적이다.

다른 언어에서도 안전한 프로그래밍을 위해 가능하다면 `const`, `final` 사용을 개발자에게 권장하고 있다. 그러니 불편하더라도 기본적으로 변경불가능한 변수를 만들도록 하는 방향이 더 좋다. 이렇게 개발자의 실수를 줄여주고, 앞서 말한 규칙들을 컴파일 시간에 지키기 쉽도록 유도한다.

#### Ownership

소유권은 Rust 언어 고유의 특징이다. 소유권을 이용해 메모리를 관리하는 개념은 [C++의 RAII 패턴](http://en.cppreference.com/w/cpp/language/raii)과 비슷하니 알고 있었다면 쉽게 이해된다.

먼저 변수의 범위(Variable Scope)를 알아야 한다. 변수의 이름은 범위 내에서만 유효하다는 규칙이다. 즉, 변수가 선언된 `{}` 내에서만 유효하다는 의미다. 추가로 값의 소유권을 가진 변수는 범위를 벗어나면 `drop`이라는 특별한 함수가 자동으로 호출된다.

```rust
{
    let s = String::from("hello"); // s is valid from this point forward

    // do stuff with s
}                                  // this scope is now over, and s is no
                                   // longer valid
```

예를 들어 위 코드에서는 `s` 변수가 선언될 때 메모리가 할당된다. 변수가 `}` 범위를 벗어나면 `drop` 함수가 자동으로 호출된다. `drop` 함수는 메모리를 해제한다. 아주 깔끔하다!

### Practical language

어떤 특징들을 살펴봐야 실용적인 언어라는 것을 알 수 있을까? 고민해봤는데 그냥 내가 간단하게 사용할 수 있는지를 보자.

[여러 IDE들을 지원](https://forge.rust-lang.org/ides.html)한다. 현재 Eclipse, Visual Studio, IntelliJ IDEA, GNOME Builder, Emacs, Vim, Sublime Text, Atom, Visual Studio Code를 지원한다.

라이브러리를 쉽게 사용할 수 있다. Rust는 [Cargo](https://github.com/rust-lang/cargo)라는 패키지 매니저를 사용해서 빌드할 수 있다. 라이브러리는 crates라는 package로 표현하는데, Rust의 [crates registry](https://crates.io/)는 매우 크다. Cargo는 dependancy 관리까지 간단하게 해주니 아주 편하다.

많은 플랫폼을 지원한다. 하지만 아직 컴파일러와 패키지 매니저를 모든 플랫폼에 지원하지는 못해서 [지원 레벨에 따라 나누어놓았다](https://forge.rust-lang.org/platform-support.html).

## Conclusion

Rust가 아직 완벽하지는 않다. 하지만 [커뮤니티가 활동적](https://github.com/rust-lang/rust/pulse)이고, [6주 간격의 빠른 릴리즈 주기](https://github.com/rust-lang/rfcs/blob/master/text/0507-release-channels.md)로 업데이트하고 있으니 더 좋아질거란 확신이 든다. 시스템 프로그래밍 분야에서 미래가 기대되는 언어다.

## References

- [Rust official site](https://www.rust-lang.org)
- [Rust GitHub repository](https://github.com/rust-lang/rust)
- [Rust official document](https://doc.rust-lang.org/stable/book/)
- [Rust Wikipedia](https://en.wikipedia.org/wiki/Rust_(programming_language))
- [Rust - 나무위키](https://namu.wiki/w/Rust)
- [Friends of Rust](https://www.rust-lang.org/friends.html)
- [Stack Overflow Annual Developer Survey](https://insights.stackoverflow.com/survey)
- [GitHub Rust Topic](https://github.com/topics/rust)
- [Awesome Rust](https://github.com/rust-unofficial/awesome-rust)
- [C++ RAII patterns](http://en.cppreference.com/w/cpp/language/raii)
