# TIL docker

## docker build

```shell
docker build [OPTIONS] /path/to/a/Dockerfile
```

빌드시 옵션의 종류로는 매우 많은 지정이 가능하다. (ex. cpu사용률, quota등 세부 지정 가능)
이중 `--tag`옵션을 지정하면 빌드 후 만들고자 하는 이미지의 이름과 태그를 지정할 수 있다. `imagename:tagname`형태로 입력

PATH는 반드시 빌드하고자 하는 Dockerfile이 있는 경로로 가져와야 한다.
Dockerfile이 있는 URL로 지정도 가능.(git repo 또는 gist 링크 등)

여러개의 Dockerfile을 한곳에 저장하려면 `파일명.Dockerfile` 형태로 저장하면 된다.

> **reference**
[dockerfile](https://docs.docker.com/engine/reference/builder/), [docker build](https://docs.docker.com/engine/reference/commandline/build/)

## docker locale problem (한글 설정)

이미지를 띄우게 되면 기본적으로는 아무런 `locale` 설정이 들어있지 않다. 따라서 일반적인 `ubuntu`나 이미지들을 띄우게 되면 `한글깨짐`현상이 발생하게 된다.

이 현상을 해결하는 방법은 2가지가 있다.

1. 처음 컨테이너 생성부터 *UTF-8* 설정을 하는 방법
2. 실행 중인 컨테이너 내부로 들어가서 *UTF-8* 설정을 하는 방법

우선 사용하는 컨테이너의 설정을 확인하는 방법은 컨테이너 내부에서
`locale`을 입력하면 로케일에 대한 다양한 환경변수를 확인할 수 있다.

```shell
root@0a04e82c0ea4:/# locale
LANG=
LANGUAGE=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=
```

위 같은 환경이 나온다면 한글(*UTF-8*)설정이 되어 있지 않아 문자가 깨진다.
시스템 내에 있는 로케일에 대해 알고 싶을 경우

```shell
root@0a04e82c0ea4:/# locale -a
C
C.UTF-8
POSIX
```

### 처음 컨테이너 생성부터 *UTF-8* 설정을 하는 방법

도커를 실행할때 간단히 환경변수를 넘겨주는 방식으로 컨테이너 내부에서 로케일 설정을 할 수 있다.

```shell
docker run --runtime=nvidia -ti \
-e LC_ALL=C.UTF-8 \
--ipc=host \
-v /host/path/:/container/data \
-p 8888:8888 \
--name="locale-setting" \
ubuntu
```

이렇게 설정하고 컨테이너 내부에서 로케일을 확인해보면
아래와 같이 나오는 것을 확인할 수 있다.

```shell
root@0a04e82c0ea4:/# locale
LANG=
LANGUAGE=
LC_CTYPE="C.UTF-8"
LC_NUMERIC="C.UTF-8"
LC_TIME="C.UTF-8"
LC_COLLATE="C.UTF-8"
LC_MONETARY="C.UTF-8"
LC_MESSAGES="C.UTF-8"
LC_PAPER="C.UTF-8"
LC_NAME="C.UTF-8"
LC_ADDRESS="C.UTF-8"
LC_TELEPHONE="C.UTF-8"
LC_MEASUREMENT="C.UTF-8"
LC_IDENTIFICATION="C.UTF-8"
LC_ALL=C.UTF-8
```
