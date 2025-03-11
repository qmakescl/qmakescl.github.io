---
title: Apple Silicon 에서 Jekyll 사용하기 - github pages 를 목적으로
description: ""
date: 2025-03-11T13:37:38.334Z
preview: ""
tags: [setup, jekyll, MacOS, Apple Silicon]
categories: [How]
---

## 들어가기전에

그동안 notion에 글을 써 왔는데, notion은 개인의 로그로 두고 외부로 발신할 메시지를 무엇으로 할까 고민하다 github pages를 사용하기로 결정했다. 예전에 R 관련 문서로 작성한 경험이 있어서 RStudio에서 작업하려고 하니 예전 기억이 나지 않아 요즘 Python을 사용하기에 조금은 대중적인 방식으로 사용하기 위해 Visual Studio Code를 도구로 정하고 인터넷의 많은 문서의 도움을 받아 환경을 만들었으며 아직은 어설프다. 하지만, 나의 기록으로 남긴다. 참고삼아 나의 환경은 다음과 같다.

- 하드웨어 : Mac Studio(M2 Max, 32Gb), MacBookPro(Intel i5, 16Gb)
- 편집도구 : Visual Studio Code
- GitHub Pages : [qmakescl.github.io](https://qmakescl.github.io)

## 환경구축

### Homebrew 설치

MacOS 사용자 중 프로그래밍을 하는 사용자는 대부분 [Homebrew](https://brew.sh/)를 설치해서 사용하고 있겠지만, 혹시나 하는 마음에 Homebrew 설치를 위한 명령어를 옮겨 적는다. Terminal을 열거나 Visual Studio Code의 Terminal에서 다음을 입력하고 엔터를 쳐서 실행하면 Homebrew가 설치된다.

```teminal
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Ruby 설정

MacOS는 ruby를 기본으로 설치해서 공급한다. 하지만 그 버전이 낮아 현재 사용하지 않지만 시스템에 영향을 미칠 수 있어 그대로 두고 Ruby 관리자를 이용해서 설치하는 것을 Jekyll 에서 제시하고 있다.

먼저 Jekyll에서 제안하는 설치 방법에 대해 [홈페이지 설치문서](https://jekyllrb.com/docs/installation/macos/) 를 참조할 수 있으나 영문으로 되어 있다. 이에 대해 우리나라 사용자분들이 자발적으로 참여해 번역한 [한글번역판의 설치문서](https://jekyllrb-ko.github.io/docs/installation/macos/)가 존재하는데 번역판은 2020년 기준으로 예전 공식 홈페이지의 문서를 번역해 약간의 차이가 있다. 하지만, 작동하는데는 큰 문제가 없으며 주요 차이는 다음과 같이 (버전)관리자와 이에 따른 인스톨러의 차이이며, 두가지 모두 ruby에서 지원하는 방식이다.

| 구분 | 영문판 | 한글번역판 |
|:---:|:----:|:-------:|
| 관리자 | chruby | rbenv |
| 인스톨러 | ruby-install | ruby-build |

이 문서에서는 한글번역판의 내용을 옮겨 적는다.
