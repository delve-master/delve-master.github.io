---
layout: post
title: 공개 포스팅 / 비공개 포스팅 설정하기
categories: ["tutorial","IT"]
tags: ["jekyll"]
---

만약 아직 공개하고 싶지 않은 포스팅이 있다면 Jekyll 프론트매터 (front matter)에 `published` 태그를 추가할 수 있다.

```yaml
layout: post
title: 포스팅 제목
...
...
published: false  # 공개 상태로 전환 시 true로
```

`published` 태그가 `false`로 설정된 포스팅은 블로그에 나타나지 않는다! 물론 `true`로 바꾸면 다시 나타난다. 

