# TIL docker

## docker build

```
docker build [OPTIONS] /path/to/a/Dockerfile
```
빌드시 옵션의 종류로는 매우 많은 지정이 가능하다. (ex. cpu사용률, quota등 세부 지정 가능)
이중 `--tag`옵션을 지정하면 빌드 후 만들고자 하는 이미지의 이름과 태그를 지정할 수 있다. `imagename:tagname`형태로 입력

PATH는 반드시 빌드하고자 하는 Dockerfile이 있는 경로로 가져와야 한다.
Dockerfile이 있는 URL로 지정도 가능.(git repo 또는 gist 링크 등)

여러개의 Dockerfile을 한곳에 저장하려면 `파일명.Dockerfile` 형태로 저장하면 된다.

**reference**
`dockerfile` [link](https://docs.docker.com/engine/reference/builder/)
`docker build` [link](https://docs.docker.com/engine/reference/commandline/build/)