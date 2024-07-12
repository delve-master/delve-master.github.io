---
title: "Miniconda 환경 설정하기"
date: 2023-05-01 22:38:00 +0900
categories: ["IT"]
tags: ["Miniconda"]
---

Anaconda나 Miniconda는 주로 파이썬 환경 (*environment*) 을 관리할 때 사용하는 도구이다.개발을 하다보면 내 프로그램이 다른 버전의 파이썬에서도 작동하는지 테스트를 해봐야하는 상황이 존재한다. 이 때 각각 다른 파이썬 버전과 패키지가 깔려있는 환경을 구축해놓으면 이 과정이 굉장히 수월해진다.

이번 포스팅에서는 Miniconda를 이용해 이런 파이썬 env를 구축해보자.

- [Miniconda 설치](#miniconda-설치)
  - [TESTTT](#testtt)
- [TEST](#test)


## Miniconda 설치
우선 Miniconda의 공식 홈페이지 (https://docs.conda.io/projects/miniconda/en/latest/miniconda-install.html)에서 installer를 다운받자. 다운이 끝나면 .exe 파일을 실행해 installer의 안내에 따라 Miniconda를 설치하면 된다. 설정 관련해서 모르는 부분이 있으면 일단 default를 따라가면 된다. 필요하면 나중에 변경할 수 있다. 

### TESTTT

## TEST

(*end of post*)

---

[^1]: 포크한 리포지토리는 포크했던 리포지토리의 모든 데이터를 담고 있다. 이 때문에 포크 리포지토리가 비공개로 설정될 경우, 원 리포지토리(origin)에 존재하는 중요한 정보나 개인정보 등이 원 소유자가 모르게 유출될 수 있는 문제가 있다. 

[^2]: git clone을 하지 않으면 노트북 같은 로컬 머신에서 리포지토리를 수정할 수 없다. git clone이 되지 않은 리포지토리는 Github 같은 remote repository 저장소에서만 존재하기 때문. 

[^3]: `git checkout`은 브랜치를 이동할 때 쓰는 명령어인데, `-b` 옵션을 추가하면 브랜치를 생성하여 그 브랜치로 바로 이동하게 된다. 이를 이용해 `git branch` 와 `git checkout` 으로 수행할 작업을 한번에 해결할 수 있다. 