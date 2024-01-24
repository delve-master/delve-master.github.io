---
title: Jekyll로 블로그 만들기
categories: ["IT"]
tags: ["jekyll"]
---

블로그는 유용한 도구이다. 내가 아는 정보나 나의 생각을 정리하는데 이만한 도구가 없는 것 같다. 덕분에 나만의 블로그를 만드는 방법도 요즘에는 다양하다. 사람들이 가장 많이 아는 블로그는 아마 네이버나 다음일 것이다. 다음은 몰라도 네이버는 많은 사람들이 계정을 가지고 있으니 접근성이 아주 좋으니 당연할 것이다.

반면 개발자들 사이에서는 티스토리를 많이 활용한다. 과거 설치형 블로그 제공 서비스였던 Tattertools를 계승했기에 그 때부터 유명했던 컴덕들을 대거 흡수했기 때문이다.

문제는 이들 서비스를 이용하여 블로그를 관리하고 있다면 그 블로그가 완전히 "내 것"이 아니라는 점이다. 만약 내 블로그가 이들 운영정책을 위반하거나 악성 신고 폭탄을 맞게되면 언제든 사라질 위기에 처하게 된다. 티스토리가 그나마 이 문제에서 자유로웠지만 카카오가 티스토리를 인수하면서 별반 다를게 없게 되었다.

만약 내가 이런 제한해서 자유롭게 블로그를 운영하고 싶다면 **완전히 독립된 설치형 블로그**를 운영해야한다.

이번 포스팅에서는 설치형 블로그 툴인 Jekyll를 이용해 블로그를 만드는 과정을 정리한다.

> 아래의 과정은 모두 Windows 11을 기준으로한다.
{prompt: info}


Ruby 설치하기:

Jekyll은 Ruby 환경에서 동작하기 때문에 먼저 Ruby를 설치해야 합니다.
RubyInstaller에서 Ruby+Devkit 버전을 다운로드하고 설치하세요. 설치 중에 "Add Ruby executables to your PATH" 옵션을 선택해야 합니다.
Jekyll 및 Bundler 설치하기:

명령 프롬프트(Windows PowerShell 또는 Command Prompt)를 열고 다음 명령어를 실행하여 Jekyll 및 Bundler를 설치하세요.

bash
Copy code
gem install jekyll bundler
시스템 요구사항 확인:

Jekyll은 Ruby와 함께 동작하는데, 필요한 패키지들이 설치되어 있는지 확인하세요. 자세한 내용은 Jekyll 설치 가이드에서 확인할 수 있습니다.
Jekyll 프로젝트 생성:

원하는 디렉터리로 이동하여 Jekyll 프로젝트를 생성합니다. 아래 명령어를 실행하세요.

bash
Copy code
jekyll new myblog
myblog는 프로젝트 디렉터리의 이름으로 변경 가능합니다.

프로젝트 디렉터리로 이동:

생성된 Jekyll 프로젝트 디렉터리로 이동합니다.

bash
Copy code
cd myblog
로컬 서버 실행:

다음 명령어를 실행하여 Jekyll 로컬 서버를 시작합니다.

bash
Copy code
bundle exec jekyll serve
이제 웹 브라우저에서 http://localhost:4000으로 접속하여 Jekyll로 생성한 사이트를 확인할 수 있습니다.

이제 Jekyll이 Windows 11에서 성공적으로 설치되었고 로컬에서 실행 중입니다. 프로젝트의 _config.yml 파일을 편집하여 원하는 설정을 추가하고, Markdown 파일을 편집하여 컨텐츠를 작성할 수 있습니다.
## Jekyll 설치
먼저 공식 Jekyll 사이트 (https://jekyllrb.com/docs/installation/) 에서 설치 과정을 알아볼 수 있다. 나는 Windows 유저라 Windows 가이드를 따르고 있으니 만약 다른 OS를 사용하는 사람들은 그에 맞는 가이드를 찾으면 된다.

Jekyll


```markdown
---
layout: post
title: 포스팅 제목
...
...
published: false  # 공개 상태로 전환 시 true로
---

# 포스팅 시작
```

`published` 태그가 `false`로 설정된 포스팅은 블로그에 나타나지 않는다! 물론 `true`로 바꾸면 다시 나타난다. 

(*end of post*)