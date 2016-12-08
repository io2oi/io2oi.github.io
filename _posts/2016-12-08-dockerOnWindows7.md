---
layout: post
title: "Windows7 에서 docker 이용해서 jekyll 실행하기"
---

# Windows7 에서 docker 이용해서 jekyll 실행하기

순수한 나의 경험이다.

Window7의 경우 [docker web site](https://docs.docker.com/docker-for-windows/) 에 있는 기본 설치 파일로는 설치가 불가능 하다. 이 경우에는 docker toolbox 를 사용한다. [연결](https://www.docker.com/products/docker-toolbox)

나의 경우 `github page` 의 소스를 편집하고자 하였으므로 `github page` 용 `Jekyll` docker image 뿐만이 아니라 `github page` 소스를 연결해야 했다.

이를 위해서 `docker` 에서는 volume 연결 옵션인 `-v`를 제공한다.

하지만 내가 잘못 한 것인지는 모르지만 `docker toolbox` 에서는 `C:\User\<내계정>\` 아래의 경로만 volume 연결이 가능했다.

즉,

```bash
]$ docker run -p 4000:4000 -v /d/<githubpath>:/usr/app/src <dockerimage>
```

은 안 되고

```bash
]$ docker run -p 4000:4000 -v /c/Users/<내계정>/<githubpath>:/usr/app/src <dockerimage>
```

하니 된다.

내가 사용한 `docker image`는 `starefossen/github-pages`이다.

`docker toolbox` 설치시 같이 설치된 `Kinematic` 에서 GUI를 통해서도 경로 설정 변경이 가능하다.
